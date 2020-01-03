# Why is React ?
You'll discover what makes React great. You will compose simple functions together to create complex ones, write declarative code, discover unidirectional data flow, and that React is just JavaScript.
- Concept 01: Introduction
- Concept 02: What is Composition?
- Concept 03: What is Declarative Code?
- Concept 04: Unidirectional Data Flow
- Concept 05: React Is "Just JavaScript"
- Concept 06: Lesson Summary

## What is Composition?

From [Wikipedia](https://en.wikipedia.org/wiki/Function_composition_(computer_science)), Composition is:

to combine simple functions to build more complicated ones

Let's take a look at how we can build up complex functions just by combining simple ones together.

**Benefits of Composition**

Because the concept of composition is such a large part of what makes React awesome and incredible to work with, let's dig into it a little bit. Remember that composition is just combining simple functions together to create complex functions. This is the key recipe: composition is built from simple functions!

Consider the following `getProfileLink()` function:

````javascript
function getProfileLink (username) {
  return 'https://github.com/' + username
}
````

This function is ridiculously simple, isn't it? It's just one line! Similarly, the `getProfilePic` function is also just a single line:

````javascript
function getProfilePic (username) {
  return 'https://github.com/' + username + '.png?size=200'
}
````

These are definitely simple functions, so to compose them, we'd just combine them together inside another function:

````javascript
function getProfileData (username) {
  return {
    pic: getProfilePic(username),
    link: getProfileLink(username)
  }
}
````

Now we could have written `getProfileData` without composition by providing the data directly:

````javascript
function getProfileData (username) {
  return {
    pic: 'https://github.com/' + username + '.png?size=200',
    link: 'https://github.com/' + username
  }
}
````

There's nothing technically wrong with this at all; this is entirely accurate JavaScript code. But this isn't composition. There are also a couple of potential issues with this version that isn't using composition. If the user's link to GitHub is needed somewhere else, then duplicate code would be needed. A good function should follow the "DOT" rule:

Do One Thing

This function is doing a couple of different (however minor) things; it's creating two different URLs, storing them as properties on an object, and then returning that object. In the composed version, each function just does one thing:

- `getProfileLink` – just builds up a string of the user's GitHub profile link
- `getProfilePic` – just builds up a string the user's GitHub profile picture
- `getProfileData` – returns a new object

**React & Composition **

React makes use of the power of composition, heavily! React builds up pieces of a UI using **components**. Let's take a look at some pseudo code for an example. Here are three different components:

````html
<Page />
<Article />
<Sidebar />
````

Now let's take these simple components, combine them together, and create a more complex component (aka, composition in action!):

````html
<Page>
  <Article />
  <Sidebar />
</Page>
````

Now the `Page` component has the `Article` and `Sidebar` components inside. This is just like the earlier example where `getProfileData` had `getProfileLink` and `getProfilePic` inside it.

We'll dig into components soon, but just know that composition plays a huge part in building React components.

**Composition Recap**

Composition occurs when simple functions are combined together to create more complex functions. Think of each function as a single building block that does one thing (DOT). When you combine these simple functions together to form a more complex function, this is **composition.**

**Further Research**
- [Compose me That: Function Composition in JavaScript](https://www.linkedin.com/pulse/compose-me-function-composition-javascript-kevin-greene)
- [Functional JavaScript: Function Composition For Every Day Use](https://hackernoon.com/javascript-functional-composition-for-every-day-use-22421ef65a10)


## Declarative Code

In contrast to imperative code, we've got **declarative code**. With declarative code, we don't code up all of the steps to get us to the end result. Instead, we declare what we want done, and JavaScript will take care of doing it. This explanation is a bit abstract, so let's look at an example. Let's take the imperative `for` loop code we were just looking at and refactor it to be more declarative.

With the imperative code we were performing all of the steps to get to the end result. What is the end result that we actually want, though? Well, our starting point was just an array of names:

````javascript
const people = ['Amanda', 'Geoff', 'Michael', 'Richard', 'Ryan', 'Tyler']
````

The end goal that we want is an array of the same names but where each name ends with an exclamation mark:

````javascript
["Amanda!", "Geoff!", "Michael!", "Richard!", "Ryan!", "Tyler!"]
````

To get us from the starting point to the end, we'll just use JavaScript's `.map()` function to declare what we want done.

````javascript
const excitedPeople = people.map(name => name + '!')
````

That's it! Notice that with this code we haven't:

- created an iterator object
- told the code when it should stop running
- used the iterator to access a specific item in the `people` array
- stored each new string in the `excitedPeople` array

…all of those steps are taken care of by JavaScript's `.map()` Array method.


