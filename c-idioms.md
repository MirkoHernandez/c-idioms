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


## Processing  arguments using *while*.

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
