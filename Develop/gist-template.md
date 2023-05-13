# Introduction to Regex

Hello user, this reposiroty was created so anyone who has problems or wish to learn what is Regex can jump on this and feel with a better understanding of what Regex is and how to use iit in our jobs.

for this examples I choose to explain Regex with the example of

```
Matching an HTML Tag – /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/
```

`
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

- (+)

```
const regex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;
```

the plus sign means one or more occurrences of the previous character or group, in this casa ([a-z]+) matches one or more lowercase letters. For example, "div","span","p" all of this ones match the part of the regex pattern.

- (\*)

the asterisk means zero or more occurrences of the previous character or group. in this case,

```
([^<]+)
```

matches zero or more characters that are not the following "<"

```
const html2 = "<span class='highlight'>Some text</span>";
```

in the example of the above the class container, would match the html tag providing with a true when we test this.

- (?)

the Question mark means that zero or one occurence of the prevoius character or group. but this one is not used in the example of the HTML tag.

- {}

The curly brackets are also not used for this example of the html Tag matching cases but it can be used ot specify a range of the ocurrence of the previous characters or group between three to five times.

### OR Operator

the or operator in regex is represented by the pipe symbol which is this one "|"and it usuallu allows us to specifyh the multiple alternatives tfor the patters that we have. for this example we are going to use this

```
/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/
```

The OR operator is used inside of a non-capturong group "(?:)" to specify two alternatives to match usully the closing tags of the html

```
(?:>(.*)<\/\1>|\s+\/>)
```

- "(?:)" produces a non-capturing group, which doesn't capture the text as a separate group but instead matches it.
- "<" matches the greater-than symbol that comes after the HTML element's beginning tag.

-"(.\'\*)" matches any characters inside the HTML element (apart from line terminators, which will be collected as a group).
-"<\/\1>"matches the tag name in the opening tag, where 1 is a backreference to the first capturing group, which matches the closing tag of the HTML element.
-"|" is the OR operator.
-"\s+\/>" it usaually matches a self-closing tag that ends with a forward slash.

This indicates that the regex will match either a self-closing tag that ends with a forward slash or the whole opening and closing tags of an HTML element (with any text in between).

Here are a few instances of how this regex's OR operator is used in JavaScript:

```
const regex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;

console.log(regex.test('<div>Hello world</div>'));  // true
console.log(regex.test('<img src="image.jpg" />')); // true
console.log(regex.test('<span>'));                  // false
console.log(regex.test('</div>'));                  // false
```

### Character Classes

A character class is a mechanism to match a group of characters in a regular expression. Any character that comes inside the square brackets, [], which define a character class, is regarded as a potential match. For instance, any instance of "a", "b", or "c" will match the character class [abc]. mechanics

lets go with examples:

- [a-z]

the pattern [a-z] matches any lowercase letter this will be included from a to z, in regex the first capturing group matches one or more lowercase letters immedeatly the following starting from the opening of "<"

### Flags

most of the time flags are used after the closing statement all the way at the end.

- g

a global flag that enables the regular expression to find more than one instance of an input string.

- i

the regular expression matches case-insensitively thanks to the case-insensitive parameter.

- m

The multiline flag causes the ^ and $ anchors to match the start and end of each line rather than the start and end of the whole input string.

- s

The. character is made to match any character, including line terminators, thanks to the dot-all flag.

- u

Unicode support is enabled with the unicode flag, which also changes how some metacharacters function.

- y

sticky flag, which makes the regular expression match only at the current position in the input string.

```
const regex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/gi;

console.log(regex.test("<p>Some text here</p>")); // true
console.log(regex.test("<div><p>Some text here</p></div>")); // true
console.log(regex.test("<P>Some text here</P>")); // true (because of the 'i' flag)
console.log(regex.test("<p>Some\ntext\nhere</p>")); // true (because of the 'm' flag)
console.log(regex.test("<p>Some text here</p>\n<p>More text here</p>")); // true (because of the 'm' flag)
console.log(regex.test("<p>Some text here</p>")); // true (because of the 's' flag)
console.log(regex.test("<😀>Some text here</😀>")); // true (because of the 'u' flag)
console.log(regex.test("<p>Some text here</p>")); // true (because the 'g' flag allows multiple matches)
```

The regular expression in the preceding example is made case-insensitive and global using the gi flags. Additionally, we use the s option to make the. character match any character (including line terminators) and the m flag to make the and $ anchors match the beginning and end of each line. Additionally, we employ the u flag to activate complete Unicode support, enabling the regular expression to recognize emoji characters. Finally, we match multiple instances of the regular expression in the input string by using the g flag.

### Grouping and Capturing

Grouping and capturing is the process of creating a subexpression within the pattern that can be referred to as a group. These groups allow you to match and capture a specific part of the matched text, which can be useful in various scenarions which will be the following.

- ([a-z]+)

Between angle brackets, this group matches and catches one or more lowercase letters. The tag name is recorded by this group.

- ([^<]+)\*

There are 0 or more characters in this group that match and are captured. This group tracks the characteristics of the tag.

- (.\*)(<\/\1>)?

The closing tag (if present) and the content of the tag are matched and captured by this group. Any character that matches and is captured by the (.\*) at least a dozen times.

```
const regex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;
const htmlTag = '<a href="https://www.example.com">Example</a>';

const match = htmlTag.match(regex);
const tagName = match[1]; // 'a'
const attributes = match[2]; // ' href="https://www.example.com"'
```

### Bracket Expressions

Character sets, commonly referred to as bracket expressions, are used to match a certain character from a group of characters. A group of characters must be enclosed in square brackets [in the syntax for bracket expressions].

For instance, we can use the bracket expression [abc] to match a single lowercase a, b, or c. Similarly, we can use the bracket expression [0-9] to match a single digit. The character can be used to negate a character set; for instance, [abc] will match any character that is not an a, b, or c.

To match particular characters in the HTML tag example, we can utilize bracket expressions. For instance, we may use the formula [a-z-] to match any lowercase letter or hyphen within the tag name. We can use the expression [s] to match any whitespace character within the tag attributes.

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
