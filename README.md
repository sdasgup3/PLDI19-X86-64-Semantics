## Shepherd instruction I: The set of things, if any, the PC determined must be changed for the paper to be accepted.

### Shepherd Comments

1. Add a comparison to Sail.
2. better explain the novelty.

### Authors' Comments
Please find the location of the revised paper with the "highlighted" edits as pointed below:
- Add a comparison to Sail.
  - Page 14 ( Under Section 8:Related Work ) &#10148; First column &#10148; Paragraph starting with "Sail"
- Better explain the novelty.
  - Added a new section "Section 8: Lessons Learned" where we present the lessons we learned during our semantics development, identifying important aspects to be considered, and clarifying a good practice for developing a large ISA semantics. We also elaborate the novel aspects of our semantics development approach that allow us to obtain the complete and faithful semantics with an affordable amount of effort.


## Shepherd instruction II: The smallish set of things the PC strongly recommends changing to improve the presentation and results.

### Shepherd Comments
Add the various clarifications, suggestions and explanations discussed in the reviews and rebuttal

### Authors' Comments
The following is the description of our changes in terms of the reviewers' actual comments and our modification locations in the revised paper. Also, for each modification location, we highlighted the relevant text (with blue) so as to expose the modified text even better.

|Suggestion ( Line numbers are from submitted paper ) | Comments | Corrected line  |
|-|-|-|
| **Reviewer A: Overall Comments** |      | |
|l121: "that is, 3155 instructions..." -> Unclear here whether these are the number of formalised ones or excluded ones; by cross-checking we understand that this is the number of formalised one. Maybe clarify this by giving the number of deprecated, crypto and concurrency ones respectively. |  Added the individual numbers |Section 1 &#10148; Contributions &#10148; Completeness|
|l143: "It consists of 996 mnemonics" -> again, you just talked about all the deprecated instructions, but you refer here to the total; maybe you can make this clearer by giving the number of deprecated ones.| Provided an approximation of legacy and deprecated instructions |  Section 1.1 &#10148; Size and Complexity  |
|l273: "We support all but a few non-deprecated user-level instructions, amounting to 3155" -> again, the "amounting" is confusing here as it comes just after the "few non-deprecated..."|Rephrased the sentence | Section 3.1 &#10148; First paragraph |
|l308: "Instructions which are not included" -> you cite 4 categories here, where the intro only lists the 3 last ones; the first category (system-level instructions) is excluded by the fact that you say "user-level instructions" in the intro, but the connection could be made more explicit and more importantly it would be good to justify this choice and explain whether it can be covered later or is an intrinsic restriction of the approach. Exclusion of other categories is somehow justified (exclusion of deprecated code makes some sense; the concurrency part is somehow justified by having relaxed memory as orthogonal and future work; the crypto seems very specific). But I am missing a justification for excluding system-level instructions and the impact on the applicability of the approach.| Clarified that there is no inherent limitation in supporting such categories | Section 3.1 &#10148; Last paragraph |
| l324: "we took the semantic rules for about 60% of the instructions in scope from the formal semantics in Strata"-> does this mean that all of the Strata instructions represent 60% of the ones you target? Or is there more in Strata which you don't reuse? | Rephrased the sentence  | Section 3.2 &#10148; First paragraph |
| section 3.4: the syntax of rules is not explained well; for instance, why do we have 3 parts, one for k, one for memstate and one for nextloc; where do they come from? The configuration had memstate last and had regstate as second, not nextloc...| The reason of the omitted cell in configuration is clarified |<ul><li> Section 3.3 &#10148; Second paragraph &#10148; footnote 3</li><li>Section 3.4 &#10148;  footnote 7</li></ul>   |
| l462: I don't quite understand how the fetch instruction gets into the computation. The initialization seems to "delete" all the instructions in <k> and store them in memory. But the fetch-and-execute rule seems to assume that then <k> is a sequence of fetch instructions. I suggest to clarify this.| Thanks for pointing out as this is omitted by mistake. Clarified it. | Section 3.4 &#10148; Second  paragraph  |
| l629: In "(= 118 × 256)^7" the "7" is a footnote but could be interpreted as a power ;)| Addressed the ambiguity | Section 3.6 &#10148; Immediate Instruction Variants|
| l728: "Our current implementation [...] incorrectly rounds..." -> it is not clear at this stage whether this is a limitation or something you have then fixed. We learn later that it is indeed a limitation. I would like to see this being stated upfront in the intro (without details, referring to section 6 for details)|This is a defect in our library implementation and we clarified right in the introduction section | <ul><li> Section 4.1 &#10148; Instruction Level Validation  &#10148; Results &#10148; Second paragraph </li><li>  Section 6: Limitations &#10148; Floating Point Operations</li></ul>|
| l790: this is the first time we have a reference for the GCC torture tests but it has been mentioned multiple times before. I would have like to see the reference earlier.| Added the missing citation reference | Section 3.2 &#10148; Second Column &#10148; First paragraph |
| l817: "a large fraction (81%) of which 817 is also supported by Strata." -> the distinction and relationship between Strata and Stroke is not explained well.| Clarified the distinction |Section 4.2 &#10148; footnote 14 at first line |
| l1037: "The K verifier takes a minute to verify the sum-to-n" -> a minute sounds a lot for such a simple program!| We clarified our take on this scalability issue. | Section 5.2 &#10148;  footnote 16 at last line of he section |
| **Reviewer A: Qs to Authors** |      | |
| have you tried bigger examples than the ones presented here? how well does/would the work scale to bigger examples?| We clarified  take on scalability issue. | Section 5.2 &#10148;  footnote 16 at last line of he section |
| can you handle system-level (and crypto) instructions with your approach or is it an intrinsic limitation? If it's a limitation, what's the impact of not supporting it for the applicability of the work? | Already covered above |Section 3.1 &#10148; Last paragraph|
| **Reviewer B: Overall Comments**| ||
| ACL proof assistant" --> "ACL2 proof assistant" (the "2" is part of the name; it's not a version number)|Corrected| Section 1 &#10148; Existing Semantics of X86-64 &#10148; First paragraph |
| "may sound a daunting" --> "may sound like a daunting"|Corrected| Section 1 &#10148; Our Approach &#10148; First paragraph|
| is the value of undef non-deterministically chosen each time, or is it the case that every undef of a specific type is always the same value of that type? (my guess is the former, but it would be nice if the text said so)|Rephrased |Section 1.1 &#10148; Undefined Behaviors &#10148; Last paragraph |
| it bugs me that the definition of the Value type is not shown in the paper, or at least thoroughly described| Clarified the text on value type | <ul><li> Section 3.3 &#10148; Register State </li><li> Section 3.3 &#10148; Memory State &#10148; Last line </li><li> Section 4.1 &#10148; Instruction Level Validation &#10148; Second paragraph </li></ul>|
| for most part, I think I understand the K syntax. However, on page 5, a rule takes as input Offset of type int and on the right-hand-side it uses 64'Offset -- I guess the notation "64'" makes a 64-bit word of it. I'm also confused by the ":Mem" type annotation. What exactly is of type "Mem" here?|Clarified that it is the memory addressing expression which is of type `Mem`. Also, as we elaborated on the value type (as mentioned above), we hope that `64'Offset` notation will make sense now | Section 3.5 &#10148; Read From Source Operand(s) &#10148; The only highlighted text in the paragraph along with the boxed code immediately above |
| when you first mention the fault in the semantics of FMA, you do not explain why there is such a problem -- my guess is that it is inherited from some defect in a floating-point library of K -- please explain where the error comes from.|This is a defect in our library implementation and we clarified right in the introduction section | <ul><li> Section 4.1 &#10148; Instruction Level Validation  &#10148; Results &#10148; Second paragraph </li><li>  Section 6: Limitations &#10148; Floating Point Operations</li></ul>|
| I note that there is a paper titled "Formally Verified Big Step Semantics out of x86-64 Binaries" accepted for CPP'19, which might be relevant related work.|We added the work in our related work section with relevant comparison| Section 7: Related Work|
| **Reviewer B: Qs for Authors** || |
| Is instruction decoding formalized? It seems that it is not. If it is not, then I think it is misleading to talk about "machine programs" and the x86-64 ISA, since then you are really talking about "assembly programs" and assembly instructions of x86-64.|We clarified this right in the introduction section|Section 1 &#10148; Our Approach &#10148; footnote 1 at first line|
| By testing on only one hardware platform, how do you know that you have arrived at an architecture-level model as opposed to an implementation-level model? Could your test easily be run on another x86-64 implementation? (If yes, why hasn't it been done?) | We have detailed our test platforms and as mentioned in the rebuttal, we have acknowledged this task as one of our future work. | Section 4.1 &#10148; First paragraph |
| **Reviewer C: Overall Comments**| ||
| It was not initially clear that each instruction was validated against 7,000+ test vectors: at first I thought only 7,000 tests total were run.|We clarified this right in the introduction section |Section 1 &#10148; Contributions &#10148; Faithfulness|
| **Reviewer C: Qs for Authors** || |
| Could Stoke be extended to use your x86 semantics by translating them through SMT or some similar approach? |Stoke uses an internal representation of SMT formulas (which they call bit-vector formulas created using APIs like SymBitVector & SymBool) which is later converted to SMT formulas. It would be straightforward to port the SMT formulas emitted by K to the bit-vector formula using the above APIs. Also, this porting can easily be validated. We mentioned the feasibility of this translation. | Section 8 &#10148; Employing Multiple Semantic Engineering Frameworks |
| **Reviewer D: Overall Comments** || |
| the absence of exception modeling, how does your Usability & portabilitymodel apply to invalid programs, such as those with addressing or alignment issues?| Clarified |Section 6 &#10148; Exceptions|
| Is alignment considered in memory instructions?| Clarified |Section 3.3 &#10148; Memory State &#10148; footnote 4 in first paragraph|
| What is the "coverage" of the specification itself? I.e. how much fraction of the specification is tested to have parity with hardware? The 7000 inputs for each instruction may overlook some specific input configurations for instructions, especially when the instruction has undefined output for a subset of bits.| Clarified the coverage of semantic rules |Section 4.1 &#10148; Test Inputs &#10148; Last paragraph|

<!--

| The authors mention that the model can be used for validating translation optimizations. However, they only use the model to check one specific input program. It will be good to instead have a methodology to validate that a given optimization always preserves program equivalence (for any program input). Checking a single program equivalence does not imply that a given optimization is valid for all programs.| We agree with the reviewer's comments. However our goal is to demonstrate that our semantics can be used for formal reasoning of x86-64 programs for a wide variety of purposes. Therefore, the applications are illustrative only. We believe that each application can be leveraged into a standalone tool, with its own user interface, something which is demonstrated by other similar tools developed using K framework. ||
| The addressing mode seems to be always 64-bit. Having this configurable may be helpful to validate, e.g., applications that run in real-mode (e.g. bootloaders)| The reviewer is correct in pointing that the addressing mode is 64 bit. In the current work, we do not aim to extend the model to 32-bit mode mainly because such an extension requires major changes in the memory model, for example, 32-bit mode uses segmentation, which is almost completely disabled in 64-bit mode. ||
-->
