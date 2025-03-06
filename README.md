# SMTExamples

This is a somewhat simplified, pretty printed version of
NoriSharma-2013FSE-Fig8_true-termination.c_Iteration1_Lasso_4-pieceTemplate.smt2

I noticed there were a bunch of multiply by 0, 1 that I could simplify.

I did the following:
1. In emacs, replaced all "(assert " except the first with "(simplify "
2. ran z3 on it, saved results.  To my surprise, it pretty printed the output,
   greatly increasing readability.
3. Removed crap at the beginning, leaving only lines with "(let ....)"
4. Used keyboard macro in emacs to wrap "(assert ...)" around all the lets.
5. Copied the beginning of the original file before the second assert to the new file.

Running z3 on this file on my mac returns "unsat", but takes longer than the orignal.
z3 NoriSimp.smt2  266.97s user 3.56s system 99% cpu 4:32.97 total

I'm not sure if this helps.  Maybe the partitioning slowdown won't happen on this
because it's already slower?

Anyway, the increased readability might help.  There is definitely a structure
and of or of lots of LRA formulas.

I may stare at it for a while, later.




