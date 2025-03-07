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

----

I have added two assertions of negations of atomic formulas that appear
at the beginning of the first two asserts, and see a significant slowdown.

I added the negation of the first atomic formula in the third assert, and it
speeded up a bit (!).  Maybe this is random (like scrambling), I don't know.

-- original problem

cvc5 NoriSimp.smt2  158.53s user 2.42s system 98% cpu 2:43.58 total
(base) dill@Davids-MacBook-Pro-3 SMTExamples % time cvc5 NoriSimp.smt2

time cvc5 NoriSimp.smt2

unsat

-- with negated first atomic formula

cvc5 NoriSimp.smt2  204.26s user 2.27s system 99% cpu 3:27.94 total

(base) dill@Davids-MacBook-Pro-3 SMTExamples % time cvc5 NoriSimp.smt2

time cvc5 NoriSimp.smt2

unsat

-- with negated first atomic formula from second assertion

cvc5 NoriSimp.smt2  284.26s user 3.59s system 98% cpu 4:51.36 total

(base) dill@Davids-MacBook-Pro-3 SMTExamples % time cvc5 NoriSimp.smt2

time cvc5 NoriSimp.smt2

unsat

-- with negated first atomic formula from third assertion

-- I then removed it.

cvc5 NoriSimp.smt2  263.61s user 3.07s system 98% cpu 4:30.25 total

(base) dill@Davids-MacBook-Pro-3 SMTExamples % time cvc5 NoriSimp.smt2

time cvc5 NoriSimp.smt2

unsat




