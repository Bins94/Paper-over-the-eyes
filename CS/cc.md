# llvm IR bitcode
http://pllab.cs.nthu.edu.tw/cs340402/lectures/lectures_2013/LLVM%20Bitcode%20Introduction.pdf

# GCC AST RTL ...
http://icps.u-strasbg.fr/~pop/gcc-ast.html

# llvm checker
http://clang-analyzer.llvm.org/checker_dev_manual.html#analyzer
ProgramPoint: Location in the program. Record additional state information.
 * pre-statement
 * post-statement
 * entering a call
 ...
 * stack frame
ProgramState: Abstract state of the program.
 * Environment: source code expressions to symbolic values.
 * Store: a mapping from memory locations to symbolic values.
 * GenericDataMap: Constraints on symbolic.
 A new statement listen by each checker. Checker called one after another. All checkers adds a chain to the ExplodedGraph.
 SVal: semantic evaluation of expressions. Can be concrete integers, symbolic values, memory location... Include symbolic value and otherwise. Symbolic value should be tracked while otherwise did need to be tracker. Unreasonable value( float point) evaluate to UnknownVal.
 SymExpr: A actual( immutable) value with constraints for a specify path.
 MemRegion: 
CheckerDocumentation.cpp: Desribe the class of kinds of checker.

# clang static analysis
http://lcs.ios.ac.cn/~xuzb/canalyze/memmodel.pdf
syntax-only analysis:
AST: sourcelocation
     sourceline(before proprocess take place)
path-sensitive analysis
CFG: basic block
Exploded graph: all paths through CFG + state on each path in every statement( program point)
clang path-sensitive analysis: abstract interpretaion of program
    assumes assigning symbolic value
    splite all possible states

# http://clang-developers.42468.n3.nabble.com/How-to-generate-constraints-on-input-to-reach-a-specific-program-statement-location-in-execution-td4053911.html
