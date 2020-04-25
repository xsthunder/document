## parameter && redirect
> https://stackoverflow.com/questions/4758175/how-to-use-gdb-with-input-redirection
not available in mingw64, but it works in ubuntu16.04
```bash
alias debug="gdb -q -ex 'set args arg0 arg1 < small_example_input.txt' a.exe"
```

## stack

```bash
info stack # check stacks
frame 22 # select stack frame according to info stack

# stack up & down
up
down
```

## step 

```bash
s(tep) # step in
fin(ish) # step out
```
