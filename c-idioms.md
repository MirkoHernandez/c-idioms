# Command-Line Arguments


## Check for first argument.

```C
if (*++argv && !strcmp(*argv, "-n")) {
	++argv;
	// Do something,  usually set a flag.
}
```


## Processing  arguments using *while*.

```C
while(*argv) {
       if (*++argv)
	// Do something. 
}
```
