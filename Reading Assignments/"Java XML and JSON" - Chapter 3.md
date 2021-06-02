# Chapter 3
## What Is DOM?
- Document Object Model (DOM) is a Java API for parsing an XML document into an in-memory tree of nodes, and for creating an XML document from a node tree. After a DOM parser creates a tree, an application uses the DOM API to navigate over and extract infoset items from the tree’s nodes.
- The size of documents parsed or created by DOM is limited by the amount of available memory for storing the document’s node-based tree structure.
## A Tree of Nodes
- DOM views an XML document as a tree that is composed of several kinds of nodes.
- Each node has a node name, which is the complete name for nodes that have names, and #node-type for unnamed nodes, where node-type is one of cdata-section, comment, document, document-fragment, or text. Nodes also have local names (names without prefixes), prefixes, and namespace URIs. Finally, nodes have string values, which happen to be the content of text nodes, comment nodes, and similar text-oriented nodes; normalized values for attributes; and null for everything else.
- DOM classifiesnodes into 12 types, of which seven types can be considered part of a DOM tree:
-   sw
## Exploring the DOM API
### Obtaining a DOM Parser/Document Builder
### Parsing and Creating XML Documents
## Demonstrating the DOM API
