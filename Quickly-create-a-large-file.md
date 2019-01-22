##### Quickly create a large file (e.g. for testing, or to reserve disk space for later use)
|[[Artifacts]]|

```
(file-position (open-output-file (make-temporary-file)) (* 1024 1024)) ;; 1MB zero-filled file
```
