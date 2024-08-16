# Introduction to DOM
- The Document Object Model (DOM) is a programming interface for web documents. It represents the structure of a webpage as a tree of objects, making it possible for programs (like JavaScript) to manipulate the content, structure, and style of the page dynamically.

## Document as tree
- The DOM represents the HTML document as a tree structure where each node is an object representing part of the document.
- The tree starts with the document object as the root, which contains other elements like `<html>`, `<head>`, `<body>`, and so on.

   ![DOM tree structure](https://www.w3schools.com/JS/pic_htmltree.gif)

### DOM Nodes
- In the DOM, everything is a node. The DOM represents a document as a tree of nodes, where each node is an object representing part of the document.

- **Types of nodes**
   - **Element Nodes:** Represent HTML tags like `<div>`, `<p>`, `<a>`, etc.
   - **Text Nodes:** Represent the text inside elements.
   - **Comment Nodes:** Represent comments in the HTML.
- **Node properties**
   1. **nodeName:** Returns the name of the node as a string.
      ```javascript
      const elementNode = document.querySelector("div");
      console.log(elementNode.nodeName); // Outputs: "DIV"
      const textNode = elementNode.firstChild;
      console.log(textNode.nodeName); // Outputs: "#text"
      ```

   2. **nodeType:** Returns a numeric code representing the type of the node.
      - **Element Node:** 1
      - **Text Node:** 3
      - **Comment Node:** 8
      - **Document Node:** 9
      - **DocumentFragment Node:** 11

         ```javaScript
         console.log(elementNode.nodeType); // Outputs: 1 (Element Node)
         console.log(textNode.nodeType);    // Outputs: 3 (Text Node)
         ```

   3. **nodeValue:** Returns or sets the value of the node.
      ```javascript
      console.log(textNode.nodeValue); // Outputs: "Hello, World!"
      const commentNode = document.createComment("This is a comment");
      console.log(commentNode.nodeValue); // Outputs: "This is a comment"
      ```
   4. **parentNode:** Returns the parent node of the current node. If the node has no parent, it returns null.
      ```javascript
      console.log(elementNode.parentNode); // Outputs the parent element of the <div>
      ```
   5. **childNodes:** Returns a live NodeList of all child nodes of the current node, including elements, text, and comment nodes.
      ```javascript
      console.log(elementNode.childNodes); // Outputs a NodeList of all child nodes
      ```
   6. **firstChild:** Returns the first child node of the current node, or null if there are no child nodes.
      ```javascript
      console.log(elementNode.firstChild); // Outputs the first child node (could be an element, text, or comment node)
      ```
   7. **lastChild:** Returns the last child node of the current node, or null if there are no child nodes.
      ```javascript
      console.log(elementNode.lastChild); // Outputs the last child node
      ```

   8. **nextSibling:** Returns the node immediately following the current node in the DOM tree, or null if there is no such node.
      ```javascript
      console.log(elementNode.nextSibling); // Outputs the next sibling node
      ```
   9. **previousSibling:** Returns the node immediately preceding the current node in the DOM tree, or null if there is no such node.
      ```javascript
      console.log(elementNode.previousSibling); // Outputs the previous sibling node
      ```

   10. **textContent:** Returns or sets the text content of the node and its descendants.
         ```javascript
         console.log(elementNode.textContent); // Outputs all text within the element
         elementNode.textContent = "New Text"; // Sets new text within the element
         ```

   11. **ownerDocument:** Returns the document object associated with the node, which is usually the entire document the node belongs to.
         ```javascript
         console.log(elementNode.ownerDocument); // Outputs the document object
         ```
   12. **attributes:** Returns a live NamedNodeMap of attributes of an element node. Each attribute can be accessed like an object property.
         ```javascript
         console.log(elementNode.attributes); // Outputs all attributes of the element
         ```







### DOM Manipulation
- DOM manipulation refers to the process of using JavaScript (or similar languages) to read, change, add, or delete elements and attributes within the DOM. 
#### **Selecting Elements for Manipulation**
   1. **`getElementById`**:
      - **Syntax**: `document.getElementById('element-id')`
      - Selects a single element by its unique `id` attribute. It returns the first element with the specified ID.

   2. **`getElementsByClassName`**:
      - **Syntax**: `document.getElementsByClassName('class-name')`
      - Returns a live HTMLCollection of all elements with the specified class name(s). The collection is dynamic.

   3. **`getElementsByTagName`**:
      - **Syntax**: `document.getElementsByTagName('tag-name')`
      - Returns a live HTMLCollection of all elements with the specified tag name. This collection is dynamic.

   4. **`querySelector`**:
      - **Syntax**: `document.querySelector('selector')`
      - Returns the first element within the document that matches the specified CSS selector(s). If no matches are found, it returns `null`.

   5. **`querySelectorAll`**:
      - **Syntax**: `document.querySelectorAll('selector')`
      - Returns a static (non-live) NodeList of all elements that match the specified CSS selectors. **This collection does not update automatically when the document changes.**

   6. **`document.head`**:
      - **Syntax**: `document.head`
      - Returns the `<head>` element of the current document, which typically contains metadata, links to stylesheets, and scripts.

   7. **`document.forms`**:
      - **Syntax**: `document.forms`
      - Returns a live HTMLCollection of all the `<form>` elements within the document.

   8. **`document.body`**:
      - **Syntax**: `document.body`
      - Returns the `<body>` element of the current document, which contains the content of the webpage.

   9. **`document.links`**:
      - **Syntax**: `document.links`
      - Returns a live HTMLCollection of all the `<a>` elements with an `href` attribute in the document.

   10. **`document.images`**:
      - **Syntax**: `document.images`
      - Returns a live HTMLCollection of all the `<img>` elements in the document.
#### **Modifying the DOM**
   1. **Changing content**
      - **innerHTML:** 

         - Set or get the HTML content of an element.

            ```javascript
            element.innerHTML = '<p>New Content</p>';
            ```
      - **textContent:** 
         - Set or get the text content of an element, without HTML markup.

            ```javascript
            element.textContent = 'Plain Text';
            ```
      - **innerText:**
         - Set or get the HTML content of an element.

            ```javascript
            element.innerText = 'New Content';
            ```
      - **createTextNode**:
         - Creates a new text node with the specified text content.
            ```javascript
            const text = document.createTextNode('this is text node');
            element.appendChild(text);
            ```

      - **Difference between `innerText` and `textContent`**
         - **Visibility:** innerText considers only visible text, while textContent includes all text, visible or hidden.

         - **Performance:** textContent is generally faster as it doesn’t trigger reflow or repaint, unlike innerText.
   2. **Changing Attributes**

      - **setAttribute(name, value):**
         - Set the value of an attribute on an element.

            ```javascript
            element.setAttribute('class', 'newClass');
            ```

      - **getAttribute(name):**
         - Get the value of an attribute from an element.

            ```javascript
            const value = element.getAttribute('id');
            ```

      - **removeAttribute(name):** 
         - Remove an attribute from an element.

            ```javascript
            element.removeAttribute('class');
            ```
      
      - **Accessing and modifying `classList`**
         1. **Accessing the classList**
            - The classList property returns a live `DOMTokenList` collection of the class attributes of the element.
               ```javascript
               const element = document.querySelector('#element');
               console.log(element.classList);  // Outputs the list of classes
               ```

         2. **Adding a class**
            - To add a class to an element, use the `add` method.
               ```javascript
               element.classList.add('new-class');
               ```

         3. **Removing a Class**
            - To remove a class from an element, use the `remove` method.
               ```javascript
               element.classList.remove('old-class');
               ```
         
         4. Toggling a Class
            - The toggle method adds the class if it doesn't exist and removes it if it does.
               ```javascript
               element.classList.toggle('active');
               element.classList.toggle('active', true);  // Forces the class to be added
               element.classList.toggle('active', false); // Forces the class to be removed
               ```

         5. Checking if a Class Exists
            - The contains method checks if a class is present on the element and returns a boolean value.
               ```javascript
               if (element.classList.contains('visible')) {
                  console.log('The element is visible');
               }
               ```
         6. Replacing a Class
            - The replace method replaces an existing class with a new one.
            ``` javascript
            element.classList.replace('old-class', 'new-class');
            ```

   3. **Changing styles**
      - **style.property:** 
         - Directly modify the CSS properties of an element.

            ```javascript
            element.style.color = 'blue';
            ```

   4. **Adding and removing elements**
      - **createElement(tagName):**
         - Create a new element.

            ```javascript
            const newElement = document.createElement('div');
            ```
      - **appendChild(newNode):** 
         - Add a new child node to an element.

            ```javascript
            element.appendChild(newElement);
            ```
      - **removeChild(childNode):**
         - Remove a child node from an element.

            ```javascript
            element.removeChild(childNode);
            ```
      - **insertBefore(newNode, referenceNode):**
         - Insert a new node before a reference node.

            ```javascript
            element.insertBefore(newElement, referenceNode);
            ```
#### Event handling
   1. **Adding Event Listeners**
      - **addEventListener(event, function):** 
         - Attach an event handler to an element.

            ```javascript
            element.addEventListener('click', function() {
               alert('Element clicked!');
            });
            ```
      - **onclick = function:**
         - `onclick` is a property that allows you to define a single click event handler for an element. 
         - If an element consist of multiple `onclick` events, the last assigned function will overwrite any previous ones.
            ```javascript
            const button = document.getElementById('myButton');
            button.onclick = function() {
               alert('Button clicked!');
            };
            button.onclick = function() {
            console.log('Another click event');
            };
            ```
         Advantages:
            - Simple and straightforward for handling a single click event.
            - Easier to use for basic event handling scenarios.
      
      - **Multiple event listeners**
         - Adding multiple event listeners to an element allows you to handle different types of events or multiple actions for the same event type. 
         - **Adding Different Event Listeners**
            ```javascript
            const button = document.querySelector('button');

            button.addEventListener('click', function() {
               console.log('Button was clicked');
            });

            button.addEventListener('mouseover', function() {
               console.log('Mouse is over the button');
            });
            ```
         - **Adding Multiple Listeners for the Same Event**
            - Each listener will be called in the order they were added.
            ```javascript
            const button = document.querySelector('button');

            button.addEventListener('click', function() {
               console.log('First click listener');
            });

            button.addEventListener('click', function() {
               console.log('Second click listener');
            });
            ```
         - **Using a Single Listener for Multiple Events**
            ```javaScript
            const button = document.querySelector('button');
            function handleEvent(event) {
               if (event.type === 'click') {
                  console.log('Button clicked');
               } else if (event.type === 'mouseover') {
                  console.log('Mouse over button');
               }
            }

            button.addEventListener('click', handleEvent);
            button.addEventListener('mouseover', handleEvent);
            ```





      - **Waiting for DOM to load**
         1. **Using `DOMContentLoaded` Event**
            - The DOMContentLoaded event is fired when the initial HTML document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading.

               ```javascript
               document.addEventListener("DOMContentLoaded", function() {
                  // Your code here
                  console.log("DOM fully loaded and parsed");
               });
               ```

         2. **Using `load` Event**
            - The load event is fired when the whole page, including all dependent resources such as stylesheets and images, has loaded.

               ```javascript
               window.addEventListener("load", function() {
                  // Your code here
                  console.log("Page fully loaded");
               });
               ```

         3. **Using `defer` Attribute in Script Tag**
            - If `defer` attribute is inclided in the `<script>` tag, the script will be executed after the document has been parsed but before the `DOMContentLoaded` event.

               ```html
               <script src="your-script.js" defer></script>
               ```
   2. **Removing Event Listeners**
      - **removeEventListener(event, function):** 
         - Remove an event handler from an element.

            ```javascript
            element.removeEventListener('click', handleClick);
            ```
   3. **Event Propagation**
      - **Event Bubbling:** 
         Events propagate from the target element up through the DOM tree (child to parent).

      - **Event Capturing:** 
         Events propagate from the parent down to the target element (parent to child).

      - Stopping Propagation: You can stop event propagation using `event.stopPropagation().`

         ```javascript
         element.addEventListener('click', function(event) {
            event.stopPropagation();
         });
         ```


### Web storage
- Web storage is an essential part of modern web development, providing methods for storing data on the client side.
1. **Cookies**
   - Originally designed for server-client communication, primarily for maintaining session states between browser requests.

   - Cookies are limited to about 4KB of data.
   - Cookies can be accessible from both client-side scripts (JavaScript) and server-side scripts.
      ```javascript
      // Setting a cookie
      document.cookie = "username=JohnDoe; expires=Fri, 31 Dec 2024 23:59:59 GMT; path=/";

      // Reading a cookie
      console.log(document.cookie);

      // Deleting a cookie
      document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/";
      ```
2. **Local Storage**
   - Used for storing data on the client side that persists even after the browser is closed and reopened.

   - Up to 5MB of data per domain.
   - Only accessible via JavaScript on the client side. Data is not sent to the server with every HTTP request.
      ```javaScript
      // Setting data in localStorage
      localStorage.setItem('username', 'JohnDoe');

      // Retrieving data from localStorage
      console.log(localStorage.getItem('username'));

      // Removing data from localStorage
      localStorage.removeItem('username');

      // Clearing all data from localStorage
      localStorage.clear();
      ```
3. **Session Storage**
   - Similar to `localStorage`, but the data is only stored for the duration of the page session.

   - Up to 5MB of data per domain.
   - Only accessible via JavaScript on the client side, and not sent to the server.
   - Data is cleared when the page session ends, which typically happens when the browser tab or window is closed.
      ```javaScript
      // Setting data in sessionStorage
      sessionStorage.setItem('username', 'JohnDoe');

      // Retrieving data from sessionStorage
      console.log(sessionStorage.getItem('username'));

      // Removing data from sessionStorage
      sessionStorage.removeItem('username');

      // Clearing all data from sessionStorage
      sessionStorage.clear();
      ```

**Key differences**
| **Feature**        | **Cookies**                                                   | **localStorage**                                            | **sessionStorage**                                           |
|--------------------|---------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|
| **Persistence**    | Persists beyond sessions based on their expiration.           | Persists indefinitely until explicitly deleted.             | Persists only for the duration of the page session.          |
| **Data Capacity**  | 4KB                                                           | 5MB                                                         | 5MB                                                         |
| **Security**       | Can be marked as HttpOnly and Secure, but vulnerable to CSRF. | Only accessible via JavaScript, vulnerable to XSS attacks.  | Only accessible via JavaScript, vulnerable to XSS attacks.  |
| **Use Cases**      | Session management, tracking, storing user preferences across sessions. | Storing user settings, themes, or preferences that persist across sessions. | Storing temporary data, like form inputs, during a session. |





Waiting For The Dom To Load!!!
event lifecycle
   
multiple event listeners


### Frequently Asked Questions
1. **Find an element and remove some or all of its children**
   - **Remove all children**
      ```javascript
      const parentElement = document.querySelector('#parent');
      while (parentElement.firstChild) {
         parentElement.removeChild(parentElement.firstChild);
      }
      ```
   - **Remove some children**

      ```javascript
      const parentElement = document.querySelector('#parent');
      const childElements = parentElement.querySelectorAll('.child-class');
      childElements.forEach(child => parentElement.removeChild(child));
      ```

2. **Find an element and add an element to one of its children**
   - Appending a new child element:

      ```javascript
      const parentElement = document.querySelector('#parent');
      const newChild = document.createElement('div');
      newChild.textContent = 'I am a new child!';
      parentElement.appendChild(newChild);
      ```

3. **Difference b/w NodeList & HTMLCollection**
   - **NodeList**
      - A NodeList is a collection of nodes. It can contain any type of nodes (elements, text nodes, etc.).

      - It can be iterated using forEach.
         ```javascript
         const nodeList = document.querySelectorAll('div');
         nodeList.forEach(node => console.log(node));
         ```
   - **HTMLCollection:**
      - An HTMLCollection is a collection of HTML elements.
      - It is always live, meaning it updates automatically when the DOM changes.
      - It does not support forEach directly, it needs to be  converted into an array first.

         ```javascript
         const htmlCollection = document.getElementsByClassName('some-class');
         Array.from(htmlCollection).forEach(element => console.log(element));
         ```
4. **Why using Prompt and alert is bad.**
   - **Blocking Behavior**
      - Alert and prompt are modal dialogs that pause script execution and block user interaction until dismissed, which can disrupt user experience.
   - **User Experience**
      - They look outdated and are not customizable, leading to a poor and inconsistent user experience across different browsers.

5. **Can you explain the concept of event delegation?**
   - Event Delegation is a technique in which you use a single event listener to manage events for multiple child elements by leveraging event bubbling.
   
   - Instead of adding event listeners to individual child elements, a single listener  is added to a common ancestor (parent element).
   - When an event is triggered on a child element, it bubbles up to the ancestor, where the event listener can handle it.
   - **Advantages**
      - Reduces the number of event listeners, which is more efficient, especially with a large number of elements.
      - Easily handles events for dynamically added elements without needing to reattach listeners.
      - 
      ```javascript
      const parentElement = document.querySelector('#parent');
      parentElement.addEventListener('click', (event) => {
         if (event.target && event.target.matches('button.delete-btn')) {
            console.log('Delete button clicked:', event.target);
         }
      });
      ```
      In this example, the event listener is attached to the #parent element, but it handles clicks on any button with the class delete-btn within it.
