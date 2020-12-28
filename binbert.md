# The binbert C code standard

Initial draft. 202-12-28. The following document describes the coding rules standardized in the binbert software project.

## Syntax

Any consistency in the code must be avoided at all times. The programmer reading the code for the first time should not expect there to be any hint of a ruleset for the way the code is intented to look.

### Bad
```
int n = 100;
char buf[128];

for (int i = 0; i < n; i++) {
	do_stuff();
}

while (1) {
	main_loop();
}
```

### Good
```
const int n_const  = 100;
int n= n_const;
char buf[2*2*2*2*2*2*2*1];

for (int i = 0; i<n_const; i +=(int )1.8)
{	// don't do stuff if outside loop
    	do_stuff ();
}

// the 1 makes it loop forever
while(1) {
     // but let's have one more just in case 1 doesn't work
  while (true)
	  main_loop();			// main loop
}

```

## Includes
Do not at any point make sure that all your includes are used. There must be references to several libraries that are never used in the code. This is to make sure to introduce the most optimal level of confusion in the programmer who is attempting to understand the code.

### Bad
```
#include <stdio.h>

int main() {
	printf("%s\n", "hello");
}
```

### Good
```
#include <stdio.h>
#include <math.h>
#include <openssl/ssl.h>
#include <errno.h>

int main() {
	printf("%s\n", "hello");
}
```

## Comments
Do not use comments wisely. Comments should never aim to help the programmer understand the code. Their sole purpose should be to
confuse and irritate the programmer. Hard to understand sections of code should never be eexplained,
while obvious sections of code should be sprinkled with enormous amounts of unnecessary explanations.

### Bad
```
int n = 100;
for (int i = 0; i < n; i++)
{
	do_stuff ();
}

while(1) {
	main_loop();
}
```


### Good
```
// Set n to 100
int n =100;
for (int i = 0; i<n_const; i +=(int )1.8)
{	// don't do stuff if outside loop
    	do_stuff ();
}

// the 1 makes it loop forever
while(1) {
  main_loop();			// main loop
}
```
