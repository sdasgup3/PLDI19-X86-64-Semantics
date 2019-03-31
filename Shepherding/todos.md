1. The set of things, if any, the PC determined **must** be changed for the
paper to be accepted.

- add a comparison to Sail;
- better explain the novelty.

2. The smallish set of things the PC strongly recommends changing to
improve the presentation and results.

- add the various clarifications, suggestions and explanations
  discussed in the reviews and rebuttal

Reviewer A
==========
l121: ~~"that is, 3155 instructions..." -> Unclear here whether these are the number of formalised ones or excluded ones; by cross-checking we understand that this is the number of formalised one. Maybe clarify this by giving the number of deprecated, crypto and concurrency ones respectively.~~

l143: ~~"It consists of 996 mnemonics" -> again, you just talked about all the deprecated instructions, but you refer here to the total; maybe you can make this clearer by giving the number of deprecated ones.~~

l273: ~~"We support all but a few non-deprecated user-level instructions, amounting to 3155" -> again, the "amounting" is confusing here as it comes just after the "few non-deprecated..."~~

l308: ~~"Instructions which are not included" -> you cite 4 categories here, where the intro only lists the 3 last ones; the first category (system-level instructions) is excluded by the fact that you say "user-level instructions" in the intro, but the connection could be made more explicit and more importantly it would be good to justify this choice and explain whether it can be covered later or is an intrinsic restriction of the approach. Exclusion of other categories is somehow justified (exclusion of deprecated code makes some sense; the concurrency part is somehow justified by having relaxed memory as orthogonal and future work; the crypto seems very specific). But I am missing a justification for excluding system-level instructions and the impact on the applicability of the approach.~~

l324: ~~"we took the semantic rules for about 60% of the instructions in scope from the formal semantics in Strata"-> does this mean that all of the Strata instructions represent 60% of the ones you target? Or is there more in Strata which you don't reuse?~~

l416: thanks for the example, this is helpful.

~~section 3.4: the syntax of rules is not explained well; for instance, why do we have 3 parts, one for k, one for memstate and one for nextloc; where do they come from? The configuration had memstate last and had regstate as second, not nextloc...~~

~~l462: I don't quite understand how the fetch instruction gets into the computation. The initialisation seems to "delete" all the instructions in <k> and store them in memory. But the fetch-and-execute rule seems to assume that then <k> is a sequence of fetch instructions. I suggest to clarify this.~~

~~l629: In "(= 118 × 256)^7" the "7" is a footnote but could be interpreted as a power ;)~~

l728: ~~"Our current implementation [...] incorrectly rounds..." -> it is not clear at this stage whether this is a limitation or something you have then fixed. We learn later that it is indeed a limitation. I would like to see this being stated upfront in the intro (without details, referring to section 6 for details)~~

l790: this is the first time we have a reference for the GCC torture tests but it has been mentioned multiple times before. I would have like to see the reference earlier.

l817: ~~"a large fraction (81%) of which 817 is also supported by Strata." -> the distinction and relationship between Strata and Stroke is not explained well.~~

~~l1037: "The K verifier takes a minute to verify the sum-to-n" -> a minute sounds a lot for such a simple program!~~

Questions for Authors
~~have you tried bigger examples than the ones presented here? how well does/would the work scale to bigger examples?~~

~~can you handle system-level (and crypto) instructions with your approach or is it an intrinsic limitation? If it's a limitation, what's the impact of not supporting it for the applicability of the work?~~


Reviewer B
=========
1. ~~ACL proof assistant" --> "ACL2 proof assistant" (the "2" is part of the name; it's not a version number)~~
2. ~~"may sound a daunting" --> "may sound like a daunting"~~
3. ~~is the value of undef non-deterministically chosen each time, or is it the case that every undef of a specific type is always the same value of that type? (my guess is the former, but it would be nice if the text said so)~~
4. it bugs me that the definition of the Value type is not shown in the paper, or at least thoroughly described
5. ~~for most part, I think I understand the K syntax. However, on page 5, a rule takes as input Offset of type int and on the right-hand-side it uses 64'Offset -- I guess the notation "64'" makes a 64-bit word of it. I'm also confused by the ":Mem" type annotation. What exactly is of type "Mem" here?~~
6. when you first mention the fault in the semantics of FMA, you do not explain why there is such a problem -- my guess is that it is inherited from some defect in a floating-point library of K -- please explain where the error comes from.
~~7. I note that there is a paper titled "Formally Verified Big Step Semantics out of x86-64 Binaries" accepted for CPP'19, which might be relevant related work.~~

Questions for Authors
Is instruction decoding formalized? It seems that it is not. If it is not, then I think it is misleading to talk about "machine programs" and the x86-64 ISA, since then you are really talking about "assembly programs" and assembly instructions of x86-64.

~~By testing on only one hardware platform, how do you know that you have arrived at an architecture-level model as opposed to an implementation-level model? Could your test easily be run on another x86-64 implementation? (If yes, why hasn't it been done?)~~


Reviewer C
==========
Subsection 5.1 seems fairly speculative and unlike other subsections in 5. Maybe move it into its own "future work" section?

~~It was not initially clear that each instruction was validated against 7,000+ test vectors: at first I thought only 7,000 tests total were run.

Questions for Authors
How difficult would it be to translate your semantics to inductive definitions in HOL, Coq, Agda, or similar?

Could Stoke be extended to use your x86 semantics by translating them through SMT or some similar approach?


Reviewer D
==========
1. the absence of exception modeling, how does your model apply to invalid programs, such as those with addressing or alignment issues?

2. Is alignment considered in memory instructions?

3. What is the "coverage" of the specification itself? I.e. how much fraction of the specification is tested to have parity with hardware? The 7000 inputs for each instruction may overlook some specific input configurations for instructions, especially when the instruction has undefined output for a subset of bits.

4. The authors mention that the model can be used for validating translation optimizations. However, they only use the model to check one specific input program. It will be good to instead have a methodology to validate that a given optimization always preserves program equivalence (for any program input). Checking a single program equivalence does not imply that a given optimization is valid for all programs.

5. The addressing mode seems to be always 64-bit. Having this configurable may be helpful to validate, e.g., applications that run in real-mode (e.g. bootloaders).
