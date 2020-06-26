# General

Information about embedding Racket (CS) can be found at [[https://docs.racket-lang.org/inside/cs-embedding.html]]. Information about embedding Racket (Normal) can be found at [[https://docs.racket-lang.org/inside/embedding.html]]

## Mac OS X Specific Notes

### Embedding and signing Racket.framework in Xcode

The Racket.framework distributed with the Racket distribution currently requires some modification to embed and sign. Here is a list of steps to modify the currently distributed Racket.framework for the Racket 7.7 (CS) distribution.

Note there are two uses of the term embedding in the following: One refers to embedding racket in your executable, and the other refers to embedding Racket.framework in your Mac OS X app's bundle.

The documentation (6-26-2020) says (https://docs.racket-lang.org/inside/cs-embedding.html)

"On Mac OS, besides "libracketcs.a" for static linking, a dynamic library is provided by the "Racket" framework, which is typically installed in "lib" sub-directory of the installation. Supply -framework Racket to gcc when linking, along with -F and a path to the "lib" directory. At run time, either "Racket.framework" must be moved to a location in the standard framework search path, or your embedding executable must provide a specific path to the framework (possibly an executable-relative path using the Mach-O @executable_path prefix)."

That sets the search paths _used_ by rpath, but the library binary still needs to reference @rpath to make use of these rpath search paths. Below we use install_name_tool to fix up the binary to reference the @rpath directly.

Note also that Xcode is hard coded to codesign in the Versions/A subdirectory and hasn't added any support for signing other major versions, so i link version A in the below steps. Since all apple products now use embedded frameworks, it seems apple has no plan to support non-automatic codesigning for framework major versions other than 'A' (see https://developer.apple.com/forums/thread/65963). Some system frameworks that are apple-distributed still use non-'A' major versions, but to accomplish this in Xcode you would need to add a `codesign` step manually. Also note that creating the A symlink is only necessary if you wish to sign the framework on copy.

Note also for a proper framework structure (see https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPFrameworks/Concepts/FrameworkAnatomy.html), the framework should have an Info.plist in Resources and both of `Versions/Current/Racket` and `Versions/Current/Resources`, symlinks in the top level.

Note you would have to modify the steps if you were using normal (non-CS) Racket.

All that said, here are the steps:

1. Drag the framework into xcode
1. select copy if needed, ok
1. Click on project, General tab, "Frameworks, Libraries, and Embeddeed Content"
1. Change do not embed to either embed or embed and sign
1. cd to your copied framework in your project
1. `cd Versions`
1. `ln -s 7.7_CS Current`
1. if "embed and sign" was chosen:
  `ln -s 7.7_CS A` (xcode is hard coded to sign the major version A, see above)
1. `cp /path/to/Info.plist 7.7_CS/Resources`
1. `cd ..`
1. `rm -f Racket`
1. `ln -s Versions/Current/Racket`
1. `ln -s Versions/Current/Resources`
1. `install_name_tool -id @rpath/Racket.framework/Versions/7.7_CS/Racket ./Racket`
1. `otool -L Racket` (to verify)
1. Switch to Xcode, build and run

