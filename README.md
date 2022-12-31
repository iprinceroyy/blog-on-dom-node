Before we go forward, I want you to have a brief idea of DOM & top-level view of the DOM tree as the further discussed topic is correlated. You can take the reference here [DOM](https://www.w3schools.com/js/js_htmldom.asp).

## Introducing DOM Node

Every tiny piece of code which is present in the document (HTML, XML) is represented as a Node object in the DOM Tree. It might be texts, comments, spaces, HTML tags, or elements.

## Node object

The Node [interface](https://medium.com/@ubale.vikas9/interface-in-oops-6eae3731c242) is an abstract base class meaning it can't be instantiated directly. Node inherits properties of EventTarget interface. All objects like Text, Comment, and Element use Node functionality by inheriting it.

```xml
<!-- Paragraph demo -->
<p>This is a paragraph tag</p>
```

Here, &lt;p&gt; tag is an object of HTMLParagraphTag which extends the HTMLElement interface which further extends the Element interface extending Node. `'This is a paragraph tag'`is an object of the Text interface that extends Node. `<!-- Paragraph demo -->` is an object of the Comment interface inheriting the Node class. The below diagram illustrates how different kinds of DOM objects are inheriting from their parent.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672141710792/2ebf9a90-a041-4a5c-adb0-fff8bf64e195.png align="center")

As you see, element, text, and comment objects are subclasses of the Node parent class as the direct object of the Node class can't be made. So, ultimately they all are Node objects.

**Note:** These objects aren't created by the users manually, these are created & implemented by the browser internally.

### Instance properties/variables

DOM Node abstract class has a bunch of properties defined

| Properties | Description | Mode |
| --- | --- | --- |
| Node.baseURI | Returns the base URL of the document containing the node as a string. | Read-only |
| Node.firstChild | Returns a node representing the first direct child node of the current node, otherwise null. | Read-only |
| Node.lastChild | Returns a node representing the current node's last direct child node otherwise null. | Read-only |
| Node.nextSibling | Returns a node representing the next sibling node of the node in the tree, null if there doesn't exist. | Read-only |
| Node.nodeType | Returns an unsigned short value representing the type of the node. | Read-only |
| Node.textContent | Returns / sets the textual content of the element and all its descendants. | Read/write |

Example demonstrating Node.textContent

```xml
<p>This text will be changed.</p>
```

Here &lt;p&gt; tag is a Node object as we've already discussed above. So, we can write

```javascript
document.getElementByTagName('p').textContent = "Text is changed";
```

**Note:** we cannot write `p.textContent = 'Text is changed';`

As &lt;p&gt; is an element node & there are certain ways to access every node.

The result after the text content of the node is modified.

```xml
<p>Text is changed</p>
```

### Instance methods

| Methods | Description |
| --- | --- |
| Node.appendChild() | Adds specified child node argument as the last child to the current node. |
| Node.contains() | Returns boolean values(true/false) indicating whether or not a node is a descendant of the calling node. |

There are many more methods & properties available. You can see them here [mdn](https://developer.mozilla.org/en-US/docs/Web/API/Node).

## Types of Node

There are different kinds of Node objects in the DOM tree. But we will be discussing 4 mainly used types of Node.

* Element Node
    
* Text Node
    
* Comment Node
    
* Document Node
    

### Element Node

HTML Tags in the DOM tree are represented as an element node.

E.g: &lt;p&gt;&lt;/p&gt;, &lt;div&gt;&lt;/div&gt;, &lt;span&gt;&lt;/span&gt;, etc.

### Text Node

Text inside the element is represented as a text node, labeled as *#text*. Elements nested inside the text are not treated as text nodes instead they form element nodes with text nodes in them. Don't worry if you didn't understand, it will be cleared after the pictorial demonstration. For the timing, just focus on the given below example.

E.g:

```xml
<p>This is text inside paragraph tag</p>
```

`'This is text inside paragraph tag'` is a text node.

### Comment Node

Comments in the document form comment nodes.

E.g: `<!-- Main -->, <!-- Testimonial section -->, <!-- about section -->`

### Document Node

The document object that represents the whole document is the document node.

Below is the code snippet with its corresponding node representation.

```xml
<!DOCTYPE html>
<html>
<head>
    <title>Live DOM Viewer</title>
</head>
<body>
    <!-- demo -->
    <div>This is div with <p>paragraph tag</p></div>
    <span>This is span tag</span>
</body>
</html>
```

![](./livedom.svg)

**Note:**

* !DOCTYPE HTML is also one type of node.
    
* A newline \\n and space represent text nodes.
    
* Spaces & new lines before &lt;head&gt; tag are ignored.
    
* The contents after the body closing tag &lt;/body&gt; are moved inside the body at the end.
    

You might be wondering why are these many text nodes in the above DOM tree. Let me clear you up. Text nodes numbered 1, 3, 4, 5, 6, 9, and 11 represent newlines & the rest are straightforward text.

Remember I told you elements nested inside the text don't form text nodes. See the dom view of the line shown below in the above diagram.

```xml
<div>This is div with <p>paragraph tag</p></div>
```

Also, the text node representing a newline after the HTML tag before the &lt;head&gt; tag is ignored. As you can see the first descendant of the HTML tag is the element node head, not a newline text node. You can play around with the code and analyze the DOM tree here [DOM Viewer](https://software.hixie.ch/utilities/js/live-dom-viewer/).

## Conclusion

That's all wrapped up. I know it's a bit difficult to grab these concepts at the first sight but once you are confident enough about these topics, it will be easier for you to do advanced DOM manipulation.

Thank you for reading my blog. Let's connect on [GitHub](https://github.com/iprinceroyy) and [Twitter](https://www.twitter.com/prince_popups).
