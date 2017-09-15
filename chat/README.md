
# React Real Time Text Messaging Application

## Author : Alexander Adu-Sarkodie
* React is all about modular, composable components. For our comment box example, we'll have the following component structure:

- CommentBox
  - CommentList
    - Comment
  - CommentForm

* We pass some methods in a JavaScript object to React.createClass() to create a new React component. The most important of these methods is called render which returns a tree of React components that will eventually render to HTML.

* ReactDOM.render() instantiates the root component, starts the framework, and injects the markup into a raw DOM element, provided as the second argument.

* The JSX compiler will automatically rewrite HTML tags to React.createElement(tagName) expressions and leave everything else alone. This is to prevent the pollution of the global namespace.

* Let's create the Comment component, which will depend on data passed in from its parent. Data passed in from a parent component is available as a 'property' on the child component. These 'properties' are accessed through this.props. Using props, we will be able to read the data passed to the Comment from the CommentList, and render some markup:

* By surrounding a JavaScript expression in braces inside JSX (as either an attribute or child), you can drop text or React components into the tree. We access named attributes passed to the component as keys on this.props and any nested elements as this.props.children.

see below:


 <div className="comment">
        <h2 className="commentAuthor">
          {this.props.author}
        </h2>
        {this.props.children}
 </div>


* So far, based on its props, each component has rendered itself once. props are immutable: they are passed from the parent and are "owned" by the parent. To implement interactions, we introduce mutable state to the component. this.state is private to the component and can be changed by calling this.setState(). When the state updates, the component re-renders itself.

* render() methods are written declaratively as functions of this.props and this.state. The framework guarantees the UI is always consistent with the inputs.

* When the server fetches data, we will be changing the comment data we have. Let's add an array of comment data to the CommentBox component as its state:

* Here, componentDidMount is a method called automatically by React when a component is rendered. The key to dynamic updates is the call to this.setState(). We replace the old array of comments with the new one from the server and the UI automatically updates itself. Because of this reactivity, it is only a minor change to add live updates. We will use simple polling here but you could easily use WebSockets or other technologies.

* All we have done here is move the AJAX call to a separate method and call it when the component is first loaded and every 2 seconds after that. Try running this in your browser and changing the comments.json file (in the same directory as your server); within 2 seconds, the changes will show!


## To use

There are several simple server implementations included. They all serve static files from `public/` and handle requests to `/api/comments` to fetch or add data. Start a server with one of the following:


```sh
npm install
node server.js
```


And visit <http://localhost:3000/>. Try opening multiple tabs!

## Changing the port

You can change the port number by setting the `$PORT` environment variable before invoking any of the scripts above, e.g.,

```sh
PORT=3001 node server.js
```
