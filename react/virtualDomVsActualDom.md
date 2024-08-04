## DOM(Document Object Modal): Structure of a web page
The DOM is a tree-like structure where each node represents a part of the document. Nodes can be elements, attributes, text, etc.
The DOM provides a way for JavaScript to interact with HTML and XML documents. It allows JavaScript to dynamically change the content, structure, and style of a webpage.

## Real Dom
The real DOM is a tree-like structure that represents the content of a web page. Each element, like a paragraph or a button, is a node in this tree.When you make changes to a webpage, like updating text or adding elements, the browser updates the real DOM. This process can be slow because it involves re-rendering part or all of the webpage.

## Virtual Dom
The virtual DOM is a lightweight copy of the real DOM that exists in memory. It allows frameworks like React to manage changes more efficiently.When you make changes to the UI, the virtual DOM is updated first. The virtual DOM then compares the new version with the previous one to figure out the minimum changes needed. It then updates only the parts of the real DOM that have changed.

## Shadow Dom
The Shadow DOM is a way to keep parts of your webpage isolated from the rest of the document. It's like a mini-DOM within your main DOM, with its own separate scope. It keeps the styles and scripts inside the Shadow DOM from affecting the rest of the page and vice versa. This is useful for creating reusable components without worrying about conflicts. It allows developers to create custom HTML elements (web components) that have their own isolated DOM and styles.