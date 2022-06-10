---
layout: post
current: post
cover:  assets/images/markdown-syntax.jpg
navigation: True
title: Jekyll Markdown Cheat Sheet
date: 2022-03-30 06:00:00
tags: [Getting started, Electronics]
class: post-template
subclass: 'post'
author: tschminkel
---

This cheat sheet provides a quick overview of all the Markdown syntax elements that are supported by Jekyll.

## What is Markdown?

Markdown is a lightweight and easy-to-use markup language for web writers. Markdown allows you to add formatting elements to plaintext documents and then convert them to structurally valid HTML.

Markdown syntax can be divided into two broad categories. These categories are (1) basic syntax outlined in the original design document and (2) extension of basic syntax for added capability and features.

Refer to [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/) for more examples.

## Basic syntax

These elements are defined in the original Markdown design document and can be used in all Markdown applications.

Detailed information and examples can be fount at [basic syntax guide](https://www.markdownguide.org/basic-syntax/).

---
### Headings

# H1 Headings
## H2 Headings
### H3 Headings
#### H4 Headings
##### H5 Headings
###### H6 Headings

```markdown
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

---
### Paragraph

Here's a paragraph.

```markdown
Here's a paragraph.
```

---
### Line break

Here's another one  
with a line break.

```markdown
Here's another one  
with a line break.
```

---
### Bold

Lorem **ipsum dolor** sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et __dolore magna__ aliqua.

```markdown
Lorem **ipsum dolor** sit amet, consectetur adipiscing elit, 
sed do eiusmod tempor incididunt ut labore et __dolore magna__ aliqua.
```

---
### Italic

Lorem *ipsum dolor* sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et _dolore magna_ aliqua.

```markdown
Lorem *ipsum dolor* sit amet, consectetur adipiscing elit, 
sed do eiusmod tempor incididunt ut labore et _dolore magna_ aliqua.
```

---
### Highlight

abcd <mark>Highlight</mark> efgh

```markdown
abcd <mark>Highlight</mark> efgh
```

---
### Blockquote

> blockquote text

```markdown
> blockquote text
```

> Blockquote
>> Nested Blockquote

```markdown
> Blockquote
>> Nested Blockquote
```

---
> Blockquote with horizontal lines

---

```markdown
---
> Blockquote with horizontal lines

---
```

---
### Ordered list

1. Item 1
1. Item 2
    1. Item 2a
    1. Item 2b
1. Item 3

```markdown
1. Item 1
1. Item 2
    1. Item 2a
    1. Item 2b
1. Item 3
```

---
### Unordered list

- Item
- Item
    - Indented item
    - Indented item
- Item

```markdown
- Item
- Item
    - Indented item
    - Indented item
- Item
```

---
### Inline code

This is an inline `code`.

```markdown
This is an inline `code`.
```

---
### Horizontal line

Here's some text.

---

Here's more text.

```markdown
Here's some text.

---

Here's more text.
```

---
### Link

[title](https://www.example.com)

```markdown
[title](https://www.example.com)
```

---
### Image

![alt text](/assets/images/ghost.png)
<figcaption>Caption goes here</figcaption>

```markdown
![alt text](/assets/images/ghost.png)
<figcaption>Caption goes here</figcaption>
```

## Extended syntax

These elements provide additional features by extending the basic syntax. Not all Markdown applications support these elements and each `Markdown Flavor` differs slightly.

Note that GitHub.com uses its own version of the Markdown syntax called [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/#GitHub-flavored-markdown) and some features are only available in the issues and pull requests.

Refer to [Jekyll Markdown coverage](https://www.markdownguide.org/tools/jekyll/) for a list of supported elements.

Detailed information and examples can be fount at [extended syntax guide](https://www.markdownguide.org/extended-syntax/).

---
### Table

| Syntax    | Description | Link                               | Image                                              |
| --------- | ----------- | ---------------------------------- | -------------------------------------------------- |
| Header    | Title       | [amazon.de](https://www.amazon.de) | ![alt text](/assets/images/amazon-icon.png)|
| Paragraph | Text        | [amazon.de](https://www.amazon.de) | ![alt text](/assets/images/amazon-icon.png)|

```markdown
| Syntax    | Description | Link                               | Image                                              |
| --------- | ----------- | ---------------------------------- | -------------------------------------------------- |
| Header    | Title       | [amazon.de](https://www.amazon.de) | ![alt text](/assets/images/amazon-icon.png)|
| Paragraph | Text        | [amazon.de](https://www.amazon.de) | ![alt text](/assets/images/amazon-icon.png)|
```

---
### Code block (no highlighting)

```
{
    "firstName": "John",
    "lastName": "Doe",
    "age": 25
}
```

---
### Syntax highlighting (e.g. Json)

```json
{
    "firstName": "John",
    "lastName": "Doe",
    "age": 25
}
```

---
### Syntax highlighting (e.g. Java)

```java
public class HelloWorld 
{
    public static void main (String[] args)
    {
        // Output "Hello World!"
        System.out.println("Hello World!");
    }
}
```

---
### Footnote

Here's a sentence with a footnote reference. [^1]

[^1]: This is the footnote.

```
Here's a sentence with a footnote reference. [^1]

[^1]: This is the footnote.
```

---
### Abbreviation

*[SMTP]: Simple Mail Transfer Protocol
The SMTP is a communication protocol for email transmission.

```markdown
*[SMTP]: Simple Mail Transfer Protocol
The SMTP is a communication protocol for email transmission.
```

---
### Heading ID

### Awesome Heading {#custom-id}
[link-to-awesome-heading](#custom-id)

```markdown
### Awesome Heading {#custom-id}
[link-to-awesome-heading](#custom-id)
```

---
### Definition list

Not supported by Jekyll.

term
: definition

```markdown
term
: definition
```

---
### Strikethrough

abcd ~~text~~ efgh

```markdown
abcd ~~text~~ efgh
```

---
### Task list

- [x] Read the Markdown guide
- [ ] Review the style guide
- [ ] Stay awesome!

```markdown
- [x] Read the Markdown guide
- [ ] Review the style guide
- [ ] Stay awesome!
```

---
### Emoji characters

👍 🤓

```markdown
👍 🤓
```

---
### Emoji shortcodes

Not supported by Jekyll.

:rocket:

```markdown
:rocket:
```

---
### Automatic URL linking

Not supported by Jekyll.

https://www.example.com

```markdown
https://www.example.com
```

---
### Disabling automatic URL linking

Not supported by Jekyll.

`https://www.example.com`

```markdown
`https://www.example.com`
```

---
### HTML

<div>
    <p>HTML test paragraph.</p>
</div>

```html
<div>
    <p>HTML test paragraph.</p>
</div>
```

---
### Spacing

Some Text here.
<p>&nbsp;</p>
Some Text here.

```html
Some Text here.
<p>&nbsp;</p>
Some Text here.
```

---
## Further reading

[The Markdown Guide](https://www.markdownguide.org/getting-started/) provides a detailed overview of Markdown, how it works, and what can be done with it.

Hands on Markdown experience can be achieved by completing [The Markdown Tutorial](https://www.markdowntutorial.com) or simply experimenting with online editors such as [StackEdit](https://stackedit.io).

A collection of awesome markdown goodies (libraries, services, editors, tools, cheatsheets, etc.) can be found at [Awesome Markdown Repo](https://github.com/mundimark/awesome-markdown) on GitHub.

---