# Rendering UI with React

## Creating Elements and JSX

**Watch First**

We'll be looking at using React's ``.createElement()`` method in the next couple of videos. For starters, here is its signature:

````javascript
React.createElement( /* type */, /* props */, /* content */ );
````

**JSX Returns One Root Element, Too**

When writing JSX, keep in mind that it must only return a single element. This element may have any number of descendants, but there must be a single root element wrapping your overall JSX (typically a `<div>` or a `<span>`). Check out the following example:

````javascript
const message = (
  <div>
    <h1>All About JSX:</h1>
    <ul>
      <li>JSX</li>
      <li>is</li>
      <li>awesome!</li>
    </ul>
  </div>
);
````

**💡 Declaring Components in React 💡**

In the previous video, we defined the `ContactList` component like so:

````js
class ContactList extends Component {
// ...
}
````


**Favor Composition Over Inheritance**

You might have heard before that it’s better to “favor composition over inheritance.” This is a principle that I believe is difficult to learn today. Many of the most popular programming languages make extensive use of inheritance, and it has carried over into popular UI frameworks like the Android and iOS SDKs.

In contrast, React uses composition to build user interfaces. Yes, we extend React.Component, but we never extend it more than once. Instead of extending base components to add more UI or behavior, we compose elements in different ways using nesting and props. You ultimately want your UI components to be independent, focused, and reusable.

So if you’ve never understood what it means to “favor composition over inheritance” you’ll definitely learn using React!
