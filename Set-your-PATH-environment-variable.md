Hot Tip: [[Set your PATH environment variable]] so you can use `raco` and other Racket command line functions.

On macOS:

* `sudo sh -c 'echo "/Applications/Racket v7.7/bin" >> /etc/paths.d/racket'`
  (If you have installed a previous version you may want to edit `/etc/paths.d/racket` to remove the old paths. I used `vi` but you may prefer to delete the file with `sudo rm /etc/paths.d/racket` , and recreate it with the above command)

* To use command line tools (`raco`) you will also need to run the command `sudo xattr -r -d com.apple.quarantine /Applications/Racket\ v7.7/`  

On Windows one of the following 
 * add the racket bin path to `Path` in 'Envi­ron­ment Vari­ables' (under System Properties, Advanced tab)
 * right click on Start menu and select Command Prompt(Admin), then `setx /m PATH "C:\my\installed\racket\bin\;%PATH%"` (restart command prompt required)
 * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment (restart windows required)

