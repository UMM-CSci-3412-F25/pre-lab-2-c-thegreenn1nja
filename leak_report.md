# Leak report

_Use this document to describe whatever memory leaks
you find in `clean_whitespace.c` and how you might fix
them. You should also probably remove this explanatory
text._


The memory leak happened because the strip function used memory for the stripped string using calloc, 
but the returned pointer was not freed after use. Every call to strip created a new block of memory that 
needed to be released. Updating all code that calls strip in both the testing file and the actual file to 
call free on the returned pointer after it is no longer needed. This makes it so that even the empty string 
case in strip returns a heap allocated string, which is also freed by the caller. This makes it so that every 
use from strip is matched with a matching free, which stops memory leaks.