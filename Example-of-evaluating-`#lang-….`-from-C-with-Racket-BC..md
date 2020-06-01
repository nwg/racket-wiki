Example of evaluating `#lang ….` from C with Racket BC.

```c
#include "scheme.h"
#include "base.c"

/* 
  To gather all the modules needed by `racket/base` in "base.c":

   raco ctool --c-mods base.c ++lib racket/base ++lib racket/base/lang/reader ++lib racket/runtime-config

 Compilation and linking of this file is something like

  gcc -DMZ_PRECISE_GC -I path/to/racket/include main.c path/to/libracket3m.a

 but the details depend on the platform.
*/


static int run(Scheme_Env *e, int argc, char *argv[])  {
  MZ_GC_DECL_REG(1);
  MZ_GC_VAR_IN_REG(0, e);
  
  MZ_GC_REG();
  
  declare_modules(e);

  scheme_namespace_require(scheme_intern_symbol("racket/base"));

  scheme_eval_string("(read-accept-reader #t)", e);
  scheme_eval_string("(current-module-declare-name"
		     " (make-resolved-module-path 'something))", e);
  scheme_eval_string("#lang racket/base 'ok", e);
  scheme_eval_string("(dynamic-require ''something #f)", e);							     

  MZ_GC_UNREG();
  
  return 0;
}
  
int main(int argc, char *argv[]) {
  return scheme_main_setup(1, run, argc, argv);
}
```
- [M Flatt via Slack](https://racket.slack.com/archives/C06V96CKX/p1590796695123000?thread_ts=1590774810.118200&cid=C06V96CKX)