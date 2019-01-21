This code directory contains the following progression:

1. Hash dictionaries updated with void* for entry and key
   a. Word count example
	# cc0 -x -d lib/*.c0 hdict-void.c1 words-void.c1 words-main-void.c1
   b. Produce example
        # cc0 -x -d hdict-void.c1 produce-void.c1 produce-main-void.c1

   c. Doesn't work in combination
   	# cc0 -x -d lib/*.c0 hdict-void.c1 words-void.c1 produce-void.c1 words-main-void.c1


2. Generic hash dictionaries (with void* and function pointers)
	# cc0 -x -d lib/*.c0 hdict.c1 words.c1 produce.c1 main.c1
