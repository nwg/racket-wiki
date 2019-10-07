Set your PATH environment variable so you can use `raco` and other Racket command line functions.

On macOS: `sudo sh -c 'echo "/Applications/Racket v7.3/bin" >> /etc/paths.d/racket'`
On Windows one of the following 
 * add the racket bin path to `Path` in 'Envi­ron­ment Vari­ables' (under System Properties, Advanced tab)
 * right click on Start menu and select Command Prompt(Admin), then `setx /m PATH "C:\my\installed\racket\bin\;%PATH%"` (restart command prompt required)
 * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment (restart windows required)
