### What does "Makefile should not re-link" mean?
it means only rebuild (or relink) when a file is changed or updated. 
But if nothing has changed: Don't rebuild the executable, just keep using the existing one.

### Why's this important?
Efficiency: Saves time by not rebuilding everything unnecessarily.
Correctness: Ensures your executable is only rebuilt when needed — keeping your build process fast and reliable.

### Example to illustrate
Suppose your project has:

file1.c
file2.c
Makefile
Your Makefile has rules like:

make
Copy
file: file1.o file2.o
	$(CC) $(CFLAGS) -o $@ $^
Here's what happens:

#### First time: 
When you run make, it compiles file1.c and file2.c into .o files, then links them once into file.
Next time, without changing anything:
Make checks timestamps.
If file1.o and file2.o are already up-to-date (they haven't changed since last build), Make skips re-compiling and relinking.
It reuses the existing executable file.
What if you change file1.c?
Make notices that file1.o is outdated.
It recompiles file1.c into file1.o.
It then relinks only if needed, updating file.
