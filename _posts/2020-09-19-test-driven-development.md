---
layout: post
title:  "Test Driven Development"
date:   2020-09-19
author: Ankur Abhinav
categories: tech
tags:	tests
cover:  "/assets/instacode.png"
---

Have you ever felt frustrated and exhausted while writing your code? Does it happen to you that you spend a lot of time debugging your code and suddenly start questioning your job? Debugging your code can be very stressful especially when your codebase is big. Also, it can affect your timeline as you may spend a lot of time finding that small and hidden error.   

Test Driven Development can help you from these difficult times. In this blog, I have given an overview about Test Driven Development and how you can use it. If you are a pro coder and always manage to write the correct and working piece of code in one shot, you don't need to read this blog.

## What is TDD

Test Driven Development, often called as TDD, is a cycle based technique of software engineering. In each cycle, the developer adds some new tests to the code and focuses on improving the codebase so that the new test cases pass. The aim of development is to get all the tests green rather than getting a desired output from the code.  
Each cycle can be said to have 5 different steps:
<ol>
  <li>The developer adds new tests </li>
  <li>The new tests fail while running</li>
  <li>Change your codebase with an aim to pass the new tests</li>
  <li>Run all the tests to see them pass</li>
  <li>Refactor your code to remove any duplication</li>
</ol> 

These steps are not all compulsory. Overall, the idea of TDD is to boost the confidence of the developer and to remove the stress.   
When the developer sees all the tests passing, he/she has an instant feeling of relaxation. The developer can then move on to the next cycle safely. There is no hard rule on how much change you should make in each cycle. Ideally you should add one extra test but it depends on your comfort. If you are feeling very confident about taking big steps and not breaking your code, go for it. If you are doubtful anytime or things are going out of your mind, immediately stop and run the tests. If any test is failing, fix it otherwise move forward.   
Some developers also feel comfortable on first making some obvious change in the code and then writing the test to check whether their thought is in line with the machine.


## Benefits of TDD

On first glance, TDD looks boring and time-consuming as you need to write the tests too (seems like you need to write double the amount of code). But TDD has a lot of benefits.   

TDD saves time in long run. Many times you would spend a lot of time debugging your code (more time than you spent on writing the code itself). TDD can save you from these long and stressful time.   

Personally, I have felt that TDD is very useful when you are working on a software having a large codebase which has not been written by you. Suppose your codebase doesn't have any tests. Now, if you make some small change in the code, you need to run the whole code to check whether everything is fine. The running of code may also take a lot time, and if you need to run it again and again it can be frustrating. Unfortunately, if something breaks, maybe you changed a function and some other part of the code dependent on this function goes wrong, you will have to spend some considerable time to locate the error and fix it. 

On the other hand, if your codebase has proper tests written, you just have to run all the tests and check whether they are passing. You don't need to run your entire codebase. It it's green, be happy and move forward and if you get something red, you immediately know where the error is and fix it. Running tests require less time than running your entire code because the computationally expensive parts are often mocked while writting the tests. Ideally, the runtime of all the tests should be within seconds so that you don't have to wait for too long to get the results of your tests. Also, to get these benefits, all your team members should follow TDD and write proper tests. 

When I make any small change in the codebase, I run the tests. When I get them green, I am assured that everything is fine. I don't have to worry about any of the parts getting broken. I don't have to run the code again to check whether it's working or not. And I can push my change with relief.

Overall, TDD will provide you confidence while working and help your mind to be stress-free. 


## Example

I will illustrate the TDD procedure using a very simple and small example.   
Suppose we have to write a function to calculate the BMI of a person when the input is height and weight. We know that BMI = (weight)/ (height)^2. We won't care about the units of height and weight here. 

<b>Step 1:</b> We start by writing simple test.  
{% highlight python %}

def test_calc_bmi() -> None:
	pass

{% endhighlight %}

We run the tests and everything is green. That's a good thing!

<b>Step 2:</b> We improve our tests.  
{% highlight python %}

test_cases = [
    {"weight": 20.0, "height": 1.0, "bmi": 20.0},
]


def test_calc_bmi() -> None:
    for test_case in test_cases:
        w = test_case["weight"]
        h = test_case["height"]

        actual_bmi = calc_bmi(weight=w, height=h)
        expected_bmi = test_case["bmi"]

        assert actual_bmi == expected_bmi


{% endhighlight %}

When we run the test, it fails because there is no `calc_bmi` function. Hence, we realize that we need to implement the function to make our tests pass.

<b>Step 3:</b> We add code to make the failing tests pass.

{% highlight python %}

from bmi import calc_bmi

test_cases = [
    {"weight": 20.0, "height": 1.0, "bmi": 20.0},
]


def test_calc_bmi() -> None:
    for test_case in test_cases:
        w = test_case["weight"]
        h = test_case["height"]

        actual_bmi = calc_bmi(weight=w, height=h)
        expected_bmi = test_case["bmi"]

        assert actual_bmi == expected_bmi


{% endhighlight %}

{% highlight python %}

def calc_bmi(weight: float, height: float) -> float:
    return 20.0


{% endhighlight %}

Now the tests are passing again and we are happy.  
You may be wondering that this is a very silly implementation and we definitely need to change it. You are right that we will change it in the next step. But at this time, all our tests are green and we are good to go. Remember, in TDD our aim is to keep all the tests green. Also, this technique is called `Fake it till you make it`.

<b>Step 4:</b> We add more test cases for cross-checking.
{% highlight python %}

from bmi import calc_bmi

test_cases = [
    {"weight": 20.0, "height": 1.0, "bmi": 20.0},
    {"weight": 50.0, "height": 1.5, "bmi": 22.22},
    {"weight": 80.0, "height": 1.6, "bmi": 31.25},
]


def test_calc_bmi() -> None:
    for test_case in test_cases:
        w = test_case["weight"]
        h = test_case["height"]

        actual_bmi = calc_bmi(weight=w, height=h)
        expected_bmi = test_case["bmi"]

        assert actual_bmi == expected_bmi


{% endhighlight %}

{% highlight python %}

def calc_bmi(weight: float, height: float) -> float:
    return 20.0


{% endhighlight %}

Now, the tests fail again.

<b>Step 5:</b> We refactor our code to make the tests pass.
{% highlight python %}

from bmi import calc_bmi

test_cases = [
    {"weight": 20.0, "height": 1.0, "bmi": 20.0},
    {"weight": 50.0, "height": 1.5, "bmi": 22.22},
    {"weight": 80.0, "height": 1.6, "bmi": 31.25},
]


def test_calc_bmi() -> None:
    for test_case in test_cases:
        w = test_case["weight"]
        h = test_case["height"]

        actual_bmi = calc_bmi(weight=w, height=h)
        expected_bmi = test_case["bmi"]

        assert actual_bmi == expected_bmi


{% endhighlight %}

{% highlight python %}

def calc_bmi(weight: float, height: float) -> float:
    bmi = weight / (height * height)

    return round(bmi, 2)


{% endhighlight %}
Now the tests are passing again. And everything seems fine. However, there is one issue that we need to handle. The function `calc_bmi` cannot take negative values as input. In that case, we should raise an error.   

<b>Step 6:</b> I have added the tests and refactored the code in a single step to avoid too many steps and to keep this blog shorter.
{% highlight python %}

from bmi import calc_bmi

test_cases = [
    {"weight": 20.0, "height": 1.0, "bmi": 20.0},
    {"weight": 50.0, "height": 1.5, "bmi": 22.22},
    {"weight": 80.0, "height": 1.6, "bmi": 31.25},
    {"weight": -10.0, "height": 1.0, "bmi": "error"},
    {"weight": 50.0, "height": -1.5, "bmi": "error"},
]


def test_calc_bmi() -> None:
    for test_case in test_cases:
        w = test_case["weight"]
        h = test_case["height"]

        expected_bmi = test_case["bmi"]

        try:
            actual_bmi = calc_bmi(weight=w, height=h)
        except ValueError:
            assert expected_bmi == "error"
            return

        assert actual_bmi == expected_bmi
        return


{% endhighlight %}

{% highlight python %}

def calc_bmi(weight: float, height: float) -> float:
    if (weight < 0) or (height < 0):
        raise ValueError("Invalid Input Type: negative inputs not allowed")

    bmi = weight / (height * height)

    return round(bmi, 2)


{% endhighlight %}

Finally, the code is complete and we are confident about its working, at least at this point of time.   
In future, if someone else works on this code and needs to improve it, he will start by running the tests and seeing all the tests green will give him some confidence. He can then add more tests and refactor the code to make them pass.   

I hope that this article was helpful for you and you will use TDD while development. If you have any kind of doubt regarding TDD, feel free to ask me about it in the comments.   
Thank you! 

