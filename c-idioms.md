# Command-Line Arguments


## Check for first argument using *strcmp*.

```C
if (*++argv && !strcmp(*argv, "-n")) {
	++argv;
	// Do something,  usually set a flag.
}
```


## Check for first argument pattern.

```C
if (argc > 1 && argv[1][0] == '-' && argv[1][1] ==  'n') {        
}

```


## Process optional arguments first

As seen in the original K&R, by convention optional arguments start with a minus sign.

```C
while(--argc > 0 && (*++argv)[0] == '-') {
	// Process optional arguments
}
```


## Processing arguments using *while*.

```C
while(*argv) {
       // Do something
       if (*++argv)
	// Do something, considering there are more arguments to be processed.
}
```


## Processing arguments using *for*.

```C

for(int i = 1; i < argc; i++) {
	// Do something using argv[i]
}

```


## Processing option arguments using getopt

Arguments are processed using while and switch. Most of the time argc and argv are the same arguments received by main. optarg is the variable set to to the *value* of the option argument. optind is the variable set to the *index* of next non-option argument.

```C
while ((c = getopt (argc, argv, "f: :c")) != -1) { // Process option arguments
	switch (c) {
	case 't':
		foo(optarg)  // Do something, optarg is the value of the option t.
		break;
	default:
	}
}
argc -= optind;   // update list of arguments so that regular arguments (non-option) can be processed as usual.
argv += optind;
```


# Control Flow


## Nested ternary operator in order to chose an alternative.

In this idiom the consequent and alternative expressions of the ternary operator can be ternary expressions themselves. The conditions must be mutually exclusive and the final expression must different in each case.

```C
!x ? (!y ? upleft : (y == bottom ? lowleft : left)) :
    (x == last ? (!y ? upright : (y == bottom ? lowright : right)) :
		 (!y ? upper : (y == bottom ? lower : normal)));
```


## goto expression as function termination.

A goto expression is used to execute code required in multiple parts of the function. This idiom presumes multiple exit conditions and that the label should always be before the end of the function. Convenient for code reuse if preventing a function call is required for performance.

```C
int some_function(int n) 
{
	if ()
		return 1;
	if ()
		goto message;
	for() {
		for () { // Nested for to indicate the usefulness of the idiom (a break statement won't do here).
			goto message;
		}
	}
	// Handle common exit condition. Ideally the label should be the name of the operation.
	:message
		 // print something
		 return -1;
}
```


# Bit manipulation


## Arithmetic

left shift by n is equivalent to a division by 2<sup>n</sup>. right shift by n is equivalent to a multiplication by 2<sup>n</sup>. bitwise and by n is equivalent to a modulus operation by 2<sup>n</sup> + 1, so the right operand should be *odd*.

\#+NAME

```C

// Multiplication
3 << 2; // divide by 4
3 << 4  // divide by 16

// Division
3 >> 2; // multiply by 16
3 >> 4;  // multiply by 16

// Modulus
19 & 3;    // equal to  19 % 4 

```


## Check endianness

```C

 unsigned int x;
 char *c;

x = 0x12345678; // set 4 byte integer
c = (char *)&x; // grab first byte

if (*c == 0x12) // check first byte
	// big endian

// A simpler version
int n = 1;
if(*(char *)&n == 1)


```
