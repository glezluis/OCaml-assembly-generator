# OCaml-assembly-generator
OCaml program that generates pseudo assembly language from C. It takes a abstract syntanx tree from a explicity defined tree literal and prints out pseudo assembly language to stdout. This program generates assembly from the following C code,
```
int gcd() {
  int i = getint()
  int j = getint();

  while(i != j) {
    if (i > j) 
      i = i -j;
    else 
      j = j -i;
    }
  putint(i);
  return 0;
}
```

## Dependecies 
The program requires to install OCaml to run. You can find instructions to install OCaml [here](http://www.ocaml.org/docs/install.html). 

## Usage 
The program will run with the following command
```
ocaml assembly-generator.ml
```
Once it runs will print the following:
```
main:
  a1 := &input
  call readint
  i := rv
  a1 := &input
  call readint
  j := rv
  goto L1
L2:
  r1 := i
  r2 := j
  r1 = r1 > r2
  if r1 goto L3
  r1 := j
  r2 := i
  r1 = r1 - r2
  j := r1
  goto L4
L3:
  r1 := i
  r2 := j
  r1 = r1 - r2
  i := r1
L4:
L1:
  r1 := i
  r2 := j
  r1 := r1 != r2
  if r1 goto L2
  a1 := &output
  r1 := i
  a2 = r1
  call writeint
  a1 := &output
  call writeln
  goto exit
```
