# What does "Makefile should not re-link" mean?
it means only rebuild (or relink) when a file is changed or updated. 
But if nothing has changed: Don't rebuild the executable, just keep using the existing one.

# Why's this important?
Efficiency: Saves time by not rebuilding everything unnecessarily.
Correctness: Ensures your executable is only rebuilt when needed — keeping your build process fast and reliable.
