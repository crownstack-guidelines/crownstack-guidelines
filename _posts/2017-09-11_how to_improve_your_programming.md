---
title:  "How to become a better programmer"
date:   2017-09-11
author: Ashutosh Singh
categories:
- blog
tags:
- android
---

`Eric S. Raymond` says that `Computer science education cannot make anybody an expert programmer any more than studying brushes and pigment can make somebody an expert painter`. It is an art that comes from hard work. A programmer gives his time and best effort to programming. He cares about his algorithms as well as code structure. The well-structured code is the first step for it.

### Code Structure

We can't say that good formated code is not important because it increase readability and understandability of it. Most people, both programmers and management teams, do not make any structure when it comes to coding. Without any protocol, they start coding, which leads to complexity. Good presentation techniques are important, not for code beauty, but to avoid mistakes in your code. A better structure would save time and increase efficiency. Don't write code just to work or finishing the task. Write the code in well structured, always think before writing the code that we are writing code for others not for yourself.

Some common code structure rules include

* One statement per line.
* Indentation should be consistent.
* Divide programs into methods.
* Don't use white space unless there is a natural paragraph.
* Methods should perform only one task.
* Variable names should be meaningful, clear and explain itself.
* For keywords and variables, use lower case.
* Upper case should be used for defined static constants.
* Use of global variables should be avoided.
* All variables should be explicitly declared and give an initial value.
* Hierarchial data structures should be used to keep the data and program structure.
* Compound conditional statements should be limited to avoid confusion.
* When used in functions, the use of { and } should be on their own lines to demark blocks of code.
* Use simple incrementer variables for loops such as the Fortran integer variable names which are i, j, k, l,m, and n.
* We should put our most imp function at the top and the most important line at the top of the function.
* Put function/method from most important to least important priority. So that code reviewer can see the most important code of class first.
* Always pass data in the object, try to avoid work on raw data.
* Use DRY(Don't Repeat Yourself) principle.
* Don't add unnesseccary comments(Remove unused code don't comment it out it confuse others).
* If your language support ternary, use it avoid if else.

  ```
  public String getPath(URL url) {
  if (url == null) {
  return null;
  }
  else {
  return url.getPath();
  }
  }
  with:
  public String getPath(URL url) {
  return url == null ? null : url.getPath();
  }
  ```
  * Do not ignore possible errors in your code. Don’t put off handling errors until “later” (you won’t get around to it)
  * Handle all possible code paths, do not plan to handle some(unusual) cases later. Code can be buggy.
  * Don’t expect quickly hacked-out code to be of high quality.
  * Use `Binary Chop` process to figure out bugs quickly.

### How to improve yourself

`Only a fool learns from his own mistakes, a wise man learns from other mistakes.` The best way to learn code is to modify it. We should improve our code daily.

* Inspect the code by code inspector tool like lint. Remove the warning, it will help you to structure your code properly.
* Study a small piece of code, critique it. Determine if there are weak spots, refactor it. Turn sprawling code sections into smaller well-named functions.
* `"The code works” isn’t where you stop; it’s where you start.`
* Use `Boy Scout Rule` whenever you touch some code leave it better than you found it.
* Try to write better code improve your code with best algorithms. Stop and think. Don’t write stupid code.
* Read blogs, since the blog is often written by the programmer and share their personal views, experience. It helps us to increase our programming skill.
* Read other people code and try to learn from them.
* Contribute to open-source projects as a bridge from beginner to intermediate.

### How to improve you code base one step at a time

* Daily review your code and try to improve the code.
* Indentation should be consistent.
* Check your app dependecies, remove the unsed one.
* Remove unsed method, and line of code. It creates confusion for other developer.
