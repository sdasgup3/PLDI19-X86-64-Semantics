######################
Getting Started Guide
######################
1. How to do the instalation
2. Run bubble-sort program to check that the installation is correct.


#########################
Step-by-Step Instructions
#########################

===============================================================
Artifacts for "Semantics of Instructon & Execution environment"
Refer Section 3
===============================================================

============================
Artifacts for "Testsuite"
Refer
1. Section 4.1 --> Instruction Level Validation->Test Inputs
2. Section 4.1 --> Program Level Validation
============================

============================
Artifacts for "Reported Bugs"
Refer
1. Section 4.1 --> Instruction Level Validation --> Inconsistencies Found in the Intel Manual
2. Section 4.2
3. Line 776-781
============================

============================
Artifacts for "Applications"
Refer Section 5
============================

In this section we presented some applications to demonstrate that
our semantics can be used for formal reasoning of x86-64
programs for a wide variety of purposes. Here, we present the artifacts for
the applications presented in Sections 5.2, 5.3 and 5.4


5.2. Program Verification: In this sub-section, we prove the
functional correctness of the sum-to-n program.

Working Directory: x86-semantics/program-veriifcation/sum_to_n_32_bit

The directory structure:

test-spec.k: The actual specification file that is fed to the verifier. The specification has two parts:
             the top-level specification and the loop invariant.
runlog.txt : The pre-populated output of the verifier.
run.sh     : Script to run the prover.

Reproducing the runlog.txt
--------------------------
./run.sh

Note
----
At the end of the section, we mentioned the time taken by the verifier to be
~1 min, which can be reproduced by the above command or can be cross-checked in the
runlog.txt file.


5.3. Symbolic Execution: In this section we  demonstrate how the symbolic execution
capability can be used to find a security vulnerability.


Working Directory: x86-semantics/program-veriifcation/safe_addrptr_32

The directory structure:

test-spec.k: The actual specification file that is fed to the verifier.
runlog.txt : The pre-populated output of the verifier.
run.sh     : Script to run the prover.
path_condition.z3 : The z3 query that need to be solved in order to get the input triggering the 
                    security vulnerability.

Interpretation of the log and reproducing the vulnerability
-----------------------------------------------------------
1. At line number 87 of runlog.txt, we obtain the path condition when the control reaches L2 when r >= a (refer figure 4(a)). We encode this condition as a Z3 formula in path_condition.z3 and `AND` it with the condition for a + b to overflow. The resulting formula is checked for satisfiability. We mentioned all the details in path_condition.z3 as comments and request the reviewer to have a look at it.
2. Execute `z3 path_condition.z3` to reproduce the inputs triggering the vulnerability.

Reproducing the runlog.txt
--------------------------
./run.sh


============================================
Artifacts for "Reported Numbers/Percentages"
============================================

1. In Line 12-13, we mentioned "... This totals 3155 instruction variants, corresponding to 774
mnemonics ..."

2. In Line 51, we mentioed "Heule et al. ...,  but it covers only a fragment (∼47%) of all instructions ..."

3. In Line 66-70, we mentioed "Goel et al. ...  only a small fragment (∼33%) of all user-level instructions..."

4. In Line 136, we mentioned "Our formal semantics is publicly available ..."

5. In Line 143, we mentioned "It consists of 996 mnemonics, and each mnemonic admits several variants,"

6. In Line 185, we mentioned "Remill  updates the flag with 0 .. Radare  keeps it unmodified."

7. In Line  139, we mentioned "Strata .. 1905 instruction variants (representing 466 unique mnemon- ics) of the x86-64 Haswell ISA"

8. In Line 323-326, we mentioned "To leverage previous work as much as possible, we took the semantic rules for about 60% of the instructions
in scope from the formal semantics in Strata"

9. In Line 351-352, we mentioned "We then manually added K rules for the remaining 40%
of the target instructions..."


10. In Line 363-366, we mentioned "... compared against the semantics defined in the Stoke project for about 330 instructions that were omitted in Strata..."


11. In Line 574-576, we mentoned "For each instruction, we converted the SMT formulas that Strata provides to a K specification using a simple script (∼500 LOC)."

12. In Line 641-644, we mentioned "the original Strata-provided formula for shrxl %edx, %ecx, %ebx consists of 8971 terms (including the operator symbols), but we could simplify it to a formula
consisting of only 7 terms"

13. In Line 814-817, we mentioned "Stoke  contains manually written semantics for ∼1764
x86-64 instruction variants, a large fraction (81%) of which
is also supported by Strata"

14. In Line 819-821 we mentioned "Moreover, these manually written
formulas are based on a similar model of the CPU state to
ours, which makes it easier to compare them against ours by"

