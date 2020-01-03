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

