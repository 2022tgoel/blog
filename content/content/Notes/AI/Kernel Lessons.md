
* Triton runs tuning: discard the first run of your kernel
- Be consistent about emptying the cache!
- Be consistent about the gpu you are using! They actually have different performances and run at different clock speeds and stuff
- Don’t use tensor cores when you are checking correctness… tf32 is really bad.