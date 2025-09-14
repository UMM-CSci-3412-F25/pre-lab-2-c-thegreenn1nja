# Leak report

_Use this document to describe whatever memory leaks
you find in `clean_whitespace.c` and how you might fix
them. You should also probably remove this explanatory
text._

Clean whitespace
==57966== Memcheck, a memory error detector
==57966== Copyright (C) 2002-2024, and GNU GPL'd, by Julian Seward et al.
==57966== Using Valgrind-3.23.0 and LibVEX; rerun with -h for copyright info
==57966== Command: ./check_whitespace
==57966== 
The string 'Morris' is clean.
The string '  stuff' is NOT clean.
The string 'Minnesota' is clean.
The string 'nonsense  ' is NOT clean.
The string 'USA' is clean.
The string '   ' is NOT clean.
The string '     silliness    ' is NOT clean.
==57966== 
==57966== HEAP SUMMARY:
==57966==     in use at exit: 46 bytes in 6 blocks
==57966==   total heap usage: 7 allocs, 1 frees, 1,070 bytes allocated
==57966== 
==57966== LEAK SUMMARY:
==57966==    definitely lost: 46 bytes in 6 blocks
==57966==    indirectly lost: 0 bytes in 0 blocks
==57966==      possibly lost: 0 bytes in 0 blocks
==57966==    still reachable: 0 bytes in 0 blocks
==57966==         suppressed: 0 bytes in 0 blocks
==57966== Rerun with --leak-check=full to see details of leaked memory
==57966== 
==57966== For lists of detected and suppressed errors, rerun with: -s
==57966== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

Test:

==61374== Memcheck, a memory error detector
==61374== Copyright (C) 2002-2024, and GNU GPL'd, by Julian Seward et al.
==61374== Using Valgrind-3.23.0 and LibVEX; rerun with -h for copyright info
==61374== Command: ./check_whitespace_test
==61374== 
[==========] Running 10 tests from 2 test suites.
[----------] Global test environment set-up.
[----------] 5 tests from strip
[ RUN      ] strip.EmptyString
[       OK ] strip.EmptyString (8 ms)
[ RUN      ] strip.NoWhitespace
[       OK ] strip.NoWhitespace (2 ms)
[ RUN      ] strip.WhitespaceOnFront
[       OK ] strip.WhitespaceOnFront (1 ms)
[ RUN      ] strip.WhitespaceOnBack
[       OK ] strip.WhitespaceOnBack (1 ms)
[ RUN      ] strip.WhitespaceOnBothEnds
[       OK ] strip.WhitespaceOnBothEnds (1 ms)
[----------] 5 tests from strip (17 ms total)

[----------] 5 tests from is_clean
[ RUN      ] is_clean.EmptyString
[       OK ] is_clean.EmptyString (1 ms)
[ RUN      ] is_clean.NoWhitespace
[       OK ] is_clean.NoWhitespace (0 ms)
[ RUN      ] is_clean.WhitespaceOnFront
[       OK ] is_clean.WhitespaceOnFront (1 ms)
[ RUN      ] is_clean.WhitespaceOnBack
[       OK ] is_clean.WhitespaceOnBack (1 ms)
[ RUN      ] is_clean.WhitespaceOnBothEnds
[       OK ] is_clean.WhitespaceOnBothEnds (1 ms)
[----------] 5 tests from is_clean (7 ms total)

[----------] Global test environment tear-down
[==========] 10 tests from 2 test suites ran. (52 ms total)
[  PASSED  ] 10 tests.
==61374== 
==61374== HEAP SUMMARY:
==61374==     in use at exit: 144 bytes in 8 blocks
==61374==   total heap usage: 308 allocs, 300 frees, 122,815 bytes allocated
==61374== 
==61374== LEAK SUMMARY:
==61374==    definitely lost: 144 bytes in 8 blocks
==61374==    indirectly lost: 0 bytes in 0 blocks
==61374==      possibly lost: 0 bytes in 0 blocks
==61374==    still reachable: 0 bytes in 0 blocks
==61374==         suppressed: 0 bytes in 0 blocks
==61374== Rerun with --leak-check=full to see details of leaked memory
==61374== 
==61374== For lists of detected and suppressed errors, rerun with: -s
==61374== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)