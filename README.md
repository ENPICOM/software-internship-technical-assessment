# bachelor-software-internship-assessment

A coding assessment to be done by ENPICOM bachelor software engineering internship candidates

## Intro

Hello there! First of all, congratulations - if you're asked to complete this assessment,
it means we believe you're a promising internship candidate. However, programming skill
is hard to judge by just talking, so we would like to ask you to complete this small programming
challenge.

Please do not spend too much time on this - it should only take an hour or two.

## General instructions

We would like to ask you to complete this assignment using the [TypeScript](https://www.typescriptlang.org/) language, 
since this is our main application development language at ENPICOM. 
For running TypeScript code without having to compile it to JavaScript first, we recommend [ts-node](https://github.com/TypeStrong/ts-node).

To get started, please make a fork of this [Git](https://git-scm.com/) repository, and commit + push
your code to the fork. When you have finished the assignment and made sure it works correctly, just
send us the link to the repository you used.

For this assignment, please create a command line application implementing the algorithm described
in the next section. This application should:

- accept a single string of text on STDIN (read until the end)
- exit with status 0 _if_ the provided string is valid according to the algorithm
- exit with status **42** otherwise

To help you out, we have provided a set of test cases to validate your implementation.
To run these tests, you will need [Node.js](https://nodejs.org/en/download/) installed - if you do not
have it installed, you can download it at that link for your OS.

You can run the tests from the root of the repository as follows:

```bash
$ node tests.js '<your-application-command>'
```

For example, if you use ts-node to run your application, this would be something like:

```bash
$ node tests.js 'ts-node luhn.ts'
```


## Algorithm description

Given a number determine whether or not it is valid per the Luhn formula.

The [Luhn algorithm](https://en.wikipedia.org/wiki/Luhn_algorithm) is
a simple checksum formula used to validate a variety of identification
numbers, such as credit card numbers and Canadian Social Insurance
Numbers.

The task is to check if a given string is valid.

## Validating a Number

Strings of length 1 or less are not valid. Spaces are allowed in the input,
but they should be stripped before checking. All other non-digit characters
are disallowed.

## Example 1: valid credit card number

```text
4539 1488 0343 6467
```

The first step of the Luhn algorithm is to double every second digit,
starting from the right. We will be doubling

```text
4_3_ 1_8_ 0_4_ 6_6_
```

If doubling the number results in a number greater than 9 then subtract 9
from the product. The results of our doubling:

```text
8569 2478 0383 3437
```

Then sum all of the digits:

```text
8+5+6+9+2+4+7+8+0+3+8+3+3+4+3+7 = 80
```

If the sum is evenly divisible by 10, then the number is valid. This number is valid!

## Example 2: invalid credit card number

```text
8273 1232 7352 0569
```

Double the second digits, starting from the right

```text
7253 2262 5312 0539
```

Sum the digits

```text
7+2+5+3+2+2+6+2+5+3+1+2+0+5+3+9 = 57
```

57 is not evenly divisible by 10, so this number is not valid.
