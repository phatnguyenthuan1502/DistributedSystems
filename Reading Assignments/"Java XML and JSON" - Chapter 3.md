# Chapter 3
## What Is DOM?
- Document Object Model (DOM) is a Java API for parsing an XML document into an in-memory tree of nodes, and for creating an XML document from a node tree. After a DOM parser creates a tree, an application uses the DOM API to navigate over and extract infoset items from the tree’s nodes. 
DOM has two big advantagesover SAX:
 DOM permits random access to a document’s infoset 
items, whereas SAX only permits serial access. 
 DOM also lets you create XML documents, whereas you 
can only parse documents with SAX . 
However, SAX is advantageous over DOM in that it can parse documents 
of arbitrary sizes, whereas the size of documents parsed or created by DOM 
is limited by the amount of available memory for storing the document’s 
node-based tree structure. 
## A Tree of Nodes
## Exploring the DOM API
### Obtaining a DOM Parser/Document Builder
### Parsing and Creating XML Documents
## Demonstrating the DOM API
