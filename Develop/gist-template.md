# Introduction to Regex

Hello user, this reposiroty was created so anyone who has problems or wish to learn what is Regex can jump on this and feel with a better understanding of what Regex is and how to use iit in our jobs.

for this examples I choose to explain Regex with the example of

```
Matching an HTML Tag – /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/
```

Expect the explanations to be done with this example.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [What is Regex](#what-is-regex)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

### What is Regex

Regular expressions (regex) are a set of characters that allow you to search for and match patterns in text. It is a powerful tool for manipulating text and is widely used in programming and data processing applications. To use regex, you need to be familiar with the syntax and special characters that represent different types of characters and patterns in text. With regex, you can perform complex searches and replace operations in text with just a few lines of code. It is an essential tool for anyone working with text data, and mastering it can greatly improve your productivity and efficiency.

## Regex Components

### Anchors

there are two Anchors that we should pay attention to.

- ^(Caret)Anchor
- $(dollar)Anchor

the "^" Anchor is making sure that we have the same on at the beggining of the test here is an example.

```
const regex = /^hello/;
console.log(regex.test("hello world"));   // true
console.log(regex.test("goodbye world")); // false
```

as we can see on the example above the "^" is looking for hello at the beggining of the sentence so it can be true.

and on the other one as it does not start and matches with "hello" the test was false.

now lets see "$" Anchor.

now the dollar anchor is looking for the end of the string to match here is an example

```
const regex = /world$/;
console.log(regex.test("hello world"));   // true
console.log(regex.test("hello there"));   // false
```

for this two exmaples I believe it was better to use normal strings.

### Quantifiers

Quantifiers define the minimum and maximum number of times that a character or set of characters must match.

*(+)

```
const regex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;
```

the plus sign means one or more occurrences of the previous character or group, in this casa ([a-z]+) matches one or more lowercase letters. For example, "div","span","p" all of this ones match the part of the regex pattern. 

**

the asterisk means zero or more occurrences of the previous character or group. in this case,

```
([^<]+)
```
matches zero or more characters that are not the following "<"

```


```

```
const html2 = "<span class='highlight'>Some text</span>";
```

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
