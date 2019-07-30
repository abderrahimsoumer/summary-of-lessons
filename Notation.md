# Notation
Notation is a common language used to communicate mathematical ideas. **Think of notation as a universal language used by academic and industry professionals to convey mathematical ideas**. In the next videos, you might see things that seem confusing. Use the quizzes to assist with your understanding of the concepts.

You likely already know some notation. Plus, minus, multiply, division, and equal signs all have mathematical symbols that you are likely familiar with. Each of these symbols replaces an idea for how numbers interact with one another. In the coming concepts, you will be introduced to some additional ideas related to notation. Though you will not need to use notation to complete the project, it does have the following properties:

1. **Understanding how to correctly use notation makes you seem really smart**. Knowing how to read and write in notation is like learning a new language. A language that is used to convey ideas associated with mathematics. 


2. **It allows you to read documentation, and implement an idea to your own problem**. Notation is used to convey how problems are solved all the time. One really popular mathematical algorithm that is used to solve some of the world's most difficult problems is known as Gradient Boosting. The way that it solves problems is explained here: https://en.wikipedia.org/wiki/Gradient_boosting. If you really want to understand how this algorithm works, you need to be able to read and understand notation. 


3. **It makes ideas that are hard to say in words easier to convey**. Sometimes we just don't have the right words to say. For those situations, I prefer to use notation to convey the message. Similar to the way an emoji or meme might convey a feeling better than words, notation can convey an idea better than words. Usually those ideas are related to mathematics, but I am not here to stifle your creativity.


## Example to Introduce Notation

There is a lot going on in this video - here is a recap of the big ideas.

### Rows and Columns

If you aren't familiar with spreadsheets, this will be covered in detail in future lessons. Spreadsheets are a common way to hold data. They are composed of rows and columns. Rows run horizontally, while columns run vertically. Each column in a spreadsheet commonly holds a specific **variable**, while each row is commonly called an **instance** or **individual**.

The example used in the video is shown below.

|Date	|Day of Week	|Time Spent On Site (X)|	Buy (Y)|
|-----|-------------|-----------------------|--------|
|June 15	|Thursday|	5	|No|
|June 15	|Thursday|	10	|Yes|
|June 16	|Friday|	20	|Yes|


This is a **row**:

|Date	|Day of Week	|Time Spent On Site (X)|	Buy (Y)|
|-----|-------------|----------------------|---------|
|June 15	|Thursday	|5	|No|

This is a **column**:

|Time Spent On Site (X)|
|----------------------|
|5|
|10|
|20|

### Before Collecting Data

**Before collecting data, we usually start with a question, or many questions, that we would like to answer. The purpose of data is to help us in answering these questions.**

### Random Variables

A **random variable** is a placeholder for the possible values of some process (mostly... the term 'some process' is a bit ambiguous). As was stated before, notation is useful in that it helps us take complex ideas and simplify (often to a single letter or single symbol). We see random variables represented by capital letters (X, Y, or Z are common ways to represent a random variable).

We might have the random variable X, which is a holder for the possible values of the amount of time someone spends on our site. Or the random variable Y, which is a holder for the possible values of whether or not an individual purchases a product.

X is 'a holder' of the values that could possibly occur for the amount of time spent on our website. Any number from 0 to infinity really.

## Capital vs. Lower Case Letters

**Random variables** are represented by capital letters. Once we observe an outcome of these random variables, we notate it as a lower case of the same letter.

## Notation for Calculating the Mean

We know that the mean is calculated as the sum of all our values divided by the number of values in our dataset.

In our current notation, adding all of our values together can be extremely tedious. If we want to add 3 values of some random variable together, we would use the notation:

x1 + x2 + x3 

If we want to add 6 values together, we would use the notation:

x1 + x2 + x3 + x4 + x5 + x6

To extend this to add one hundred, one thousand, or one million values would be ridiculous! How can we make this easier to communicate?!

## Aggregations

An **aggregation** is a way to turn multiple numbers into fewer numbers (commonly one number).

**Summation** is a common aggregation. The notation used to sum our values is a greek symbol called sigma Σ.

## Other Aggregations
The Σ sign is used for aggregating using summation, but we might choose to aggregate in other ways. Summing is one of the most common ways to need to aggregate. However, we might need to aggregate in alternative ways. If we wanted to multiply all of our values together we would use a product sign Π , capital Greek letter pi. The way we aggregate continuous values is with something known as integration (a common technique in calculus), which uses the following symbol ∫ which is just a long s. We will not be using integrals or products for quizzes in this class, but you may see them in the future!
