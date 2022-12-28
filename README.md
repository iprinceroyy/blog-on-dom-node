## Table of contents

## Introducing DOM Node

Every tiny piece of code which is present in the document is represented as a Node object in the DOM Tree. It might be text, comments, space, HTML tags, or elements.

## Node object

The Node interface is an abstract base class meaning it can't be instantiated directly. Node inherits properties of EventTarget interface. All objects like Text, Comment, and Element use Node functionality by inheriting it.

```xml
<!-- Paragraph demo -->
<p>This is a paragraph tag</p>
```

&lt;p&gt; tag is an object of HTMLParagraphTag which extends the HTMLElement interface which further extends the Element interface extending Node. 'This is a paragraph tag' is an object of the Text interface that extends Node. &lt;!-- Paragraph demo --&gt; is an object of the Comment interface inheriting Node. The below diagram illustrates how different kinds of DOM objects are inheriting from their parent.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672141710792/2ebf9a90-a041-4a5c-adb0-fff8bf64e195.png align="center")

As you see, element, text, and comment objects are subclasses of the Node parent class. So, ultimately they all are Node objects.

### Instance properties/variable

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

Here &lt;p&gt; tag is a Node object as we have already discussed above. So, we can write

document.getElementByTagName('p').textContent = "Text is changed";

Note: we cannot write p.textContent = "Text is changed";

As &lt;p&gt; is an element node & there are certain ways to access every node.

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

Text inside the element is represented as a text node, labeled as #text. Elements nested inside the text are not treated as text nodes instead they form element nodes with text nodes in them. Don't worry if didn't understand, it will be cleared after the pictorial demonstration. For the timing, just focus on the given below example.

E.g: &lt;p&gt;This is text inside paragraph tag&lt;/p&gt;

"This is text inside paragraph tag" is a text node.

### Comment Node

Comments in the document form comment nodes.

E.g: &lt;!-- Main --&gt;, &lt;!-- Testimonial section --&gt;, &lt;!-- about section --&gt;

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

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672235317613/1224219b-53b4-4480-a75f-54bfcaac1bb0.png align="center")

Note:

* !DOCTYPE HTML is also one type of node.
    
* A newline \\n and space represent text nodes.
    
* Spaces & new lines before &lt;head&gt; tag are ignored.
    
* The contents after the body closing tag &lt;/body&gt; are moved inside the body at the end.
    

You might be wondering why are these many text nodes in the DOM tree. Let me clear you up.
