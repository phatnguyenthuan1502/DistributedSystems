# Chapter 7
## What Is JSON?
- JSON (JavaScript Object Notation) is a language-independent data format that expresses JSON objects as human-readable lists of properties (name-value pairs).
## JSON Syntax
- The JSON data format presents a JSON object as a brace-delimited and comma-separated list of properties: 
{ 
 property1 , 
 property2 , 
 ... 
 propertyN
} 
- A comma is not placed after the final property.
- For each property, the name is expressed as a string that’s typically quoted. The name string is followed by a colon character, which is followed by a value of a specific type ( "name": "JSON").
- JSON supports the following six types: number, string, boolean, array, object, null.
- Whitespace (space, horizontal tab, line feed, and carriage return) is allowed and is ignored around or between syntactic elements (values and punctuation).
- JSON doesn’t support comments.
- Objects and arrays can be nested.
## Validating JSON Objects
- It’s often necessary for applications to validate JSON objects, to ensure that required properties are present and that additional constraints are met. Validation is typically performed in the context of JSON Schema.
- JSON Schema is a grammar language for defining the structure, content, and semantics of JSON objects. It lets you specify metadata about what an object’s properties mean and what values are valid for those properties. The result of applying the grammar language is a schema describing the set of JSON objects that are valid.
- JSON Schema is maintained at the JSON Schema web site. This web site reveals several advantages to JSON Schema:
  - It describes your existing data format. 
  - If offers clear, human-readable, and machine-readable documentation. 
  - It provides complete structural validation.
- The JSON Schema web siteprovides links to various validator implementations for different programming languages.
