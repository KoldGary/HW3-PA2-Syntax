# CS351 - Syntax and Semantics Basics

**Due Date:** Sep 24 by 11:59 PM

## Overview

This assignment focuses on syntactic specification in PLCC. You will define grammars, build parsers and basic interpretation using PLCC.

By completing this assignment, you'll gain hands-on experience with the second phase of language implementation: parsing and syntax analysis. This builds directly on the lexical specification skills from PA1.

Answer q1-4 directly here in the README.md and then create the necessary grammar files in the `q5/`, `q6/`, and `q7/` folders.

---

## QUESTION 1: Grammar Rule Analysis

Consider the following grammar rule in a PLCC file:

```
<blah>:Goo ::= THIS <VAR> IS <silly>
```

What (non-abstract) Java class does this grammar rule define, and what are its
instance variables (a.k.a. fields) and types? Write your answer in the form of
a Java signature for the constructor for the class:

```
XXX(AAA aaa, BBB bbb, ...)
```

Here XXX is the class name, and the instance variables are aaa of type AAA, bbb
of type BBB, and so forth.

### ANSWER

```
[write your answer here]
```

---

## QUESTION 2: Repeating Rule Analysis

Repeat the question above, except use the following grammar rule:

```
<many> **= THIS <rule> HAS MULTIPLE OCCURRENCES <OF> <stuff>
```

### ANSWER

```
[write your answer here]
```

---

## QUESTION 3: Named Non-terminal Analysis

Repeat the question above, except use the following grammar rule:

```
<classes> ::= I AM TAKING <CSIT>c1 <CSIT>c2 AND <CSIT>c3
```

### ANSWER

```
[write your answer here]
```

---

## QUESTION 4: Grammar Rule Correction

Consider what is wrong with the following grammar rule in a PLCC file. You can
assume that this is part of a larger PLCC grammar file in which other token
specifications and grammar rules may appear. Your answer should be a grammar
rule that fixes all of the obvious errors on this line and that will be
acceptable to PLCC. Your answer should keep the essential nature of the
original grammar rule.

Do _not_ add or remove any of the '<' or '>' characters. Do _not_ try to
explain your answer -- just give the corrected grammar rule.

```
<VAR> := token <foo>
```

### ANSWER

```
[write your answer here]
```

---

## QUESTION 5: Balanced Parentheses Parser

In `q5/grammar`, define a grammar that generates a parser that accepts strings that only contain a balanced set of parentheses, and end in an at-sign.

For example, the following are legal sentences in the proposed language:

```
@
()@
()(()(()))@
```

The following are illegal sentences in the proposed language:

```
())@
(@
)(@
(()@
()
```

`q5/grammar` contains a partial implementation of the language. So far, it contains a complete lexical specification. Your job is to complete the syntactic specification.

Your first rule should begin:

```
<balanced> ::=
```

The legal and illegal input files have been provided for your convenience in `q5/inputs/`.

> **Development Cycle**
>
> Same as in PA1, but this time you need to test the parser.
>
> ```bash
> # Test all the illegal strings and make sure they fail.
> parse < inputs/illegal-01
> parse < inputs/illegal-02
> ...
> # Test all the legal strings and make sure they pass.
> parse < inputs/legal-01
> ...
> ```
>
> If you get tired of repeating these tests over and over again. Consider writing a script to do it for you.

- **Constraint:** **_Do not_** use the repeating rule (`**=`).
- **Tip:** You should be able to define your grammar in just three BNF lines using two non-terminals.
- **Tip:** Do use recursion.
- **Tip:** You may need to provide PLCC with class names and/or instance variable names to avoid collisions.
- **Tip:** Consider looking at `LON` for some ideas.

---

## QUESTION 6: Meta-Grammar for PLCC

In `q6/grammar`, build a grammar for PLCC's lexical specification.
Please ensure that your grammar embodies the following structure:

- Each line is either a comment or a rule.
- Each rule is either a skip rule or a token rule.
- The keyword "token" in a token rule is optional.

You can use the input from PA1 Q2 to test your grammar. It should say OK when you
parse it.

You can try other grammars from other languages. Copy their
grammar into a file like `input2`, then delete everything after the lexical
specification, and then see if your parser can parse it.

**Note:** This question builds on your lexical specification from PA1. You'll need to extend it with syntactic rules.

---

## QUESTION 7: Pretty Printer for Lexical Specifications

This builds on question 6. Copy your `q6/grammar` to `q7/grammar`.
Add a semantic specification to `q7/grammar` that
creates a pretty-printer for a lexical specification.
Your pretty-printer
will reproduce the original input without comments, and with any `token`
keywords that were not present. For example, if the input was:

```
skip WS '\s+'
# I have too much to do, so I'm not going to use the token keyword.
HI 'hi'
# OK, I have time to type this one.
token BYE 'bye'
```

Test you pretty-printer with `rep -n < input`. When you run this through your interpreter (pretty-printer), it would
produce:

```
skip WS '\s+'
token HI 'hi'
token BYE 'bye'
```

**Reminder:** For polymorphism to work, the base-class must have at least
an abstract method as a placeholder.

**Note:** This question requires both grammar parsing (from Q6) and semantic actions to implement the pretty-printing functionality.

---

## Submission Requirements

Your repository should contain:

```
README.md        # q1-4 short answers
q5/
  grammar        # Your balanced parentheses grammar
  inputs/        # (provided - test cases)

q6/
  grammar        # Your PLCC meta-grammar
  input          # (provided - test input)

q7/
  grammar        # Your pretty-printer grammar (extends q6)
  input          # (provided - test input)
  expected       # (provided - expected output)
```

**To Submit:**

1. Complete all questions, including written answers in this README
2. Test your grammars to ensure they work correctly
3. From inside your container: `tar -czf /workspace/pa2-YOURNAME.zip /workspace`
4. Download and submit the zip file to Kodiak

**Grading Criteria:**

- **Submission (33.3%):** Files are properly named and located as specified
- **Completeness (33.3%):** All questions attempted (incomplete = incorrect)
- **Correctness (33.3%):** Solutions demonstrate understanding of syntax specifications

**Late Policy:** 10% per day, maximum 5 days late

---

## Getting Help

- **Office Hours:** Wednesday 12:30-1:30 PM (Herman 207), Tuesday 12:30-1:30 PM (Herman 207)
- **Discord:** Post questions in #help channel
- **Email:**  for private concerns

**Resources:**

- PLCC Reference Manual (Slides 1a)
- Lecture slides on Syntax Specification (Slides 1)
- Your PA1 lexical specification (needed for Q6-Q7)

---

_Course content developed by Declan Gray-Mullen for WNEU with Claude_
