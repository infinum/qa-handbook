> *"Testing is a skill. While this may come as a surprise to some people it is a simple fact."*


## What is XPath?
XPath stands for XML Path Language. It provides different types of expressions, or queries, that are used to navigate through XML and HTML documents and select a node or a set of nodes.

XPath is written in a path-like syntax that resembles the path in a traditional file system (hierarchical or tree-like structure):

`xpath_syntax = //tagname[@attribute='Value']`

When you can't make use of other locators such as ID, Class, and so on, XPath will come in handy to locate the element because it will always be available.

Sometimes it might be rather long and not very pretty. However, you should avoid using this type of XPath, called absolute XPath, since it is quite brittle.

`/html/body/div[2]/div[1]/h4[1]/html[1]/body[1]/div[2]/div[1]/div[1]/h4[1]`



## Briefly about nodes
When reading about XPath and XML you will often come across the term *node*.

An XML document is treated as a tree of nodes in which the nodes are in a hierarchical relationship to each other. Each node is an XML element enclosed within an opening `<` and a closing `>` tag, such as:

`<element></element>`
 
### Types of nodes

There are seven types of nodes:

- Root
- Element
- Text
- Attribute
- Comment
- Processing instruction
- Namespace
 
XML file example:

```
<?xml version="1.0" encoding="UTF-8"?>
 
<library>
  <book>
    <title lang="en">The Lord of the Rings</title>
    <author>J. R. R. Tolkien</author>
    <year>1954</year>
  </book>
</library>
```

In the example above:

`<?xml version="1.0" encoding="UTF-8"?>` is a processing instruction used to instruct the application how to read the document

`<library>` is the root (the topmost) element node

`<author>` is an element node

`lang="en"` is an attribute node


### Relationships between the nodes
As mentioned, the nodes are in a hierarchical relationship to each other. The terms used to describe that relationship are **parent**, **child** and **sibling**. Except for the root, every node in the hierarchy has exactly one *parent* node. A node can have any number of *child* nodes. The nodes that have the same parent are called *siblings*.

The terms that could also be used are **ancestor** and **descendant**. The parent of a node or a parent of a parent is called an *ancestor*. Similarly, a child of a node, or a child of a child node is a *descendant*.

Using the XML example above:

`<book>` is the *parent* of `<title>`, `<author>` and `<year>`

`<title>`, `<author>` and `<year>` are *siblings*

`<title>` is the *first child* of `<book>`

`<year>` is the *last child* of `<book>`


The *ancestors* of `<author>` are `<book>` and `<library>`

The *descendants* of `<library>` are `<book>`, `<title>`, `<author>` and `<year>`



## Types of XPath

There are two types of XPath:

 - Absolute XPath
 - Relative Xpath

### Absolute XPath
 - Starts with a single slash (/) which means it starts from the root element
 - It directly locates an element
 - It is fragile

Example: `/html/body/div[2]/div[1]/h4[1]/b/html[1]/body[1]/div[2]/div[1]/div[1]/h4[1]`

### Relative XPath
 - Starts with a double slash (//) which means it starts from anywhere in the document
 - Shorter and easier to read compared to the absolute path
 - It is less fragile compared to the absolute path

Example: `//img[@id="profile_image"]`


---


![dilbert_selenium_xpath.png](/img/dilbert_selenium_xpath.png)
