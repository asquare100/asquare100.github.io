---
layout: post
title:  "The Purpose of Commenting"
date:   2020-08-10
author: Ankur Abhinav
categories: tech
tags: coding
cover:  "/assets/blog-covers/comments.png"
---

One of the most crucial and also the most ignored part of every code is `Commenting`. The coder while writing a code is usually too much involed into the logic of the code and its implementation that he rarely thinks about the person who is ever going to read the code later. The prime objective of the coder is to get the desired output from the code. However, writing a clean, readable and easily understandable code is very important while working in a coding team.

## What are comments
> In computer programming, a comment is a programmer-readable explanation or annotation in the source code of a computer program. They are added with the purpose of making the source code easier for humans to understand, and are generally ignored by compilers and interpreters.   
-Wikipedia

Basically, comments are something through which the writer of the code and the reader of the code interact. Every language has its own syntax for commenting. In this blog, I am not going to discuss about any syntax. My purpose is to explain the purpose of comments in a code. What makes a comment good and what not to comment.

## What to avoid

First of all, it should be clear what should not be used as comments.
Usually, in university or high-school, the professors allot some marks in a programming assignment for comments. And the students write comments just for the sake of commenting. Also, when it comes to commenting, the students are taught nothing more than its syntax.

Some of the useless comments have been shown below:
{% highlight c++ %}

// A function to add two numbers
int add(int a, int b)
{
	int result; // A new variable has been initialized
	result = a + b; // The sum of a and b is stored in variable result
	return result;
}

{% endhighlight %}

>The most important thing to keep in mind is that Comments are not a proxy to a bad code.

Here, from bad code, I don't mean a code with poor logic. Instead, I mean a code which is not very friendly with the reader. 

{% highlight c++ %}

// This function returns the distance between two Points
float func(Point p1, Point p2);

float calcDistance(Point p1, Point p2);

{% endhighlight %}

In the code snippet above, there are two instances of the same code. One of them is bad code with explantion given in comments and the other one doesn't need any explanation.

How to write good and reader friendly code is a different topic. However, the basic essence is that the code should be as self-explanatory as possible by using the proper names of variables, functions, classes, etc. Try to avoid writing comments separately and instead make the code itself look good and readble.

## What to Comment

Is it possible to avoid comments completely just by writing a clean and readble code. The answer is "NO"! 
There are many things which need to be commented.   
Some of them have been described below.

### Improvements in code
While writing a code, the coder is aware of the improvements to be done in the code and things that need to be done ahead. He should properly comment these issues so that the reader easily understands what to improve and how to proceed with the current piece of code.

An example is as follows:
{% highlight c++ %}

// TODO: Reduce the memory complexity
// FIX: The function sometimes return NULL values which can break the code

{% endhighlight %}

### Thought process

When a person writes a code, he has many thoughts in his mind, all of which are lost once he finishes his code. The thoughts can be about the implementation process or choosing any particular algorithm. Also, the coder may have tried different methods which are not part of the final function.
All these thoughts should be commented so that the reader may become aware of these crucial things and don't repeat the same process again while modifying the code.

{% highlight c++ %}

// The approach using Binary Search Tree was harder.
// Some of edge cases might be missing.

{% endhighlight %}

### Bigger Picture

Often, when a person takes a look at the code, it is difficult to get the overall functioning of the code instantly. To make his job easier, there should be some high level comments which describe the overall data flow and functioning of the code.

For example:
{% highlight c++ %}
/*
 This file contains the helper functions for the Dataset extraction part.
 It handles the permission issues and other minor details.
*/

{% endhighlight %}



### Be into Reader's mind

For few moments after completing the code, think as if you are the reader of the code and you are looking at it for the  first time. Try to find what all things can be difficult to understand in the code. Fix that either by improving the code or by adding proper comments.

## Conclusion

The next time you write a code, remember to give a small thought to the convenience of the reader and write proper comments, Also, don't comment just for the sake of commenting. I hope you found this blog useful and will use it during your coding time.   

If you find any flaw in this article, then please point it out in the comments section of this blog. Also, if you have any more idea on what not to comment or what should be commented then please let me know in the comments.   

Thanks a lot for reading!   

The basic idea of this article is inspired from the book "The Art of Readable Code" by Dustin Boswell, Trevor Foucher.
