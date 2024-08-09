### **DOM Selectors**

1. **`getElementById`**:
   - **Usage**: `document.getElementById('element-id')`
   - Selects a single element by its unique `id` attribute. It returns the first element with the specified ID.

2. **`getElementsByClassName`**:
   - **Usage**: `document.getElementsByClassName('class-name')`
   - Returns a live HTMLCollection of all elements with the specified class name(s). The collection is dynamic.

3. **`getElementsByTagName`**:
   - **Usage**: `document.getElementsByTagName('tag-name')`
   - Returns a live HTMLCollection of all elements with the specified tag name. This collection is dynamic.

4. **`querySelector`**:
   - **Usage**: `document.querySelector('selector')`
   - Returns the first element within the document that matches the specified CSS selector(s). If no matches are found, it returns `null`.

5. **`querySelectorAll`**:
   - **Usage**: `document.querySelectorAll('selector')`
   - Returns a static (non-live) NodeList of all elements that match the specified CSS selectors. **This collection does not update automatically when the document changes.**

6. **`document.head`**:
   - **Usage**: `document.head`
   - Returns the `<head>` element of the current document, which typically contains metadata, links to stylesheets, and scripts.

7. **`document.forms`**:
   - **Usage**: `document.forms`
   - Returns a live HTMLCollection of all the `<form>` elements within the document.

8. **`document.body`**:
   - **Usage**: `document.body`
   - Returns the `<body>` element of the current document, which contains the content of the webpage.

9. **`document.links`**:
   - **Usage**: `document.links`
   - Returns a live HTMLCollection of all the `<a>` elements with an `href` attribute in the document.

10. **`document.images`**:
    - **Usage**: `document.images`
    - Returns a live HTMLCollection of all the `<img>` elements in the document.

### **Navigating DOM Nodes**

1. **`parentNode`**:
   - **Usage**: `element.parentNode`
   - Returns the parent node of the specified element. 

2. **`childNodes`**:
   - **Usage**: `element.childNodes`
   - Returns a live NodeList of all child nodes (including text nodes) of the specified element.

3. **`children`**:
   - **Usage**: `element.children`
   - Returns a live HTMLCollection of all child elements (excluding text nodes) of the specified element.

4. **`firstChild`**:
   - **Usage**: `element.firstChild`
   - Returns the first child node (including text nodes) of the specified element.

5. **`firstElementChild`**:
   - **Usage**: `element.firstElementChild`
   - Returns the first child element (excluding text nodes) of the specified element.

6. **`lastChild`**:
   - **Usage**: `element.lastChild`
   - Returns the last child node (including text nodes) of the specified element.

7. **`lastElementChild`**:
   - **Usage**: `element.lastElementChild`
   - Returns the last child element (excluding text nodes) of the specified element.

8. **`nextSibling`**:
   - **Usage**: `element.nextSibling`
   - Returns the next sibling node (including text nodes) of the specified element.

9. **`nextElementSibling`**:
   - **Usage**: `element.nextElementSibling`
   - Returns the next sibling element (excluding text nodes) of the specified element.

10. **`previousSibling`**:
    - **Usage**: `element.previousSibling`
    - Returns the previous sibling node (including text nodes) of the specified element.

11. **`previousElementSibling`**:
    - **Usage**: `element.previousElementSibling`
    - Returns the previous sibling element (excluding text nodes) of the specified element.

12. **`createElement`**:
    - **Usage**: `document.createElement('tag-name')`
    - Creates a new element of the specified tag name. The element is not added to the document until you append it to an existing node.

13. **`.className`**:
    - **Usage**: `document.createElement('tag-name').className = 'class-name'`
    - Sets the class names for the newly created element.

14. **`.id`**:
    - **Usage**: `document.createElement('tag-name').id = 'id-name'`
    - Sets the `id` for the newly created element.

15. **`setAttribute`**:
    - **Usage**: `document.createElement('tag-name').setAttribute('attribute', 'value')`
    - Adds or changes an attribute for the newly created element.

16. **`createTextNode`**:
    - **Usage**: `document.createTextNode('text')`
    - Creates a new text node with the specified text content.

17. **`appendChild`**:
    - **Usage**: `parentElement.appendChild(newElement)`
    - Adds a new child node to the specified parent element. If the child is already in the document, it will be moved to the new position.

18. **`insertBefore`**:
    - **Usage**: `parentElement.insertBefore(newElement, referenceElement)`
    - Inserts a new node before the reference node as a child of a specified parent node.


### **Events**

Events in JavaScript are actions or occurrences that happen in the browser, such as a click, a keypress, or loading a page.

1. **`e.target.id`**:
   - **Usage**: `e.target.id`
   - Refers to the `id` of the element that triggered the event.

2. **`e.target.className`**:
   - **Usage**: `e.target.className`
   - Refers to the class name(s) of the element that triggered the event.

3. **`e.target.classList`**:
   - **Usage**: `e.target.classList`
   - Provides a DOMTokenList representing the class attribute of the element that triggered the event. Methods such as `.add()`, `.remove()`, `.toggle()`, and `.contains()` can be used to manipulate classes.

4. **`e.type`**:
   - **Usage**: `e.type`
   - Returns the type of event that was triggered, such as `click`, `keypress`, etc.

5. **`e.clientX`**:
   - **Usage**: `e.clientX`
   - Returns the horizontal coordinate of the mouse pointer relative to the browser window when the event was triggered.

6. **`e.clientY`**:
   - **Usage**: `e.clientY`
   - Returns the vertical coordinate of the mouse pointer relative to the browser window when the event was triggered.

7. **`e.offsetX`**:
   - **Usage**: `e.offsetX`
   - Returns the horizontal coordinate of the mouse pointer relative to the target element when the event was triggered.

8. **`e.offsetY`**:
   - **Usage**: `e.offsetY`
   - Returns the vertical coordinate of the mouse pointer relative to the target element when the event was triggered.

9. **`e.altKey`**:
   - **Usage**: `e.altKey`
   - Returns `true` if the `Alt` key was pressed when the event was triggered.

10. **`e.ctrlKey`**:
    - **Usage**: `e.ctrlKey`
    - Returns `true` if the `Ctrl` key was pressed when the event was triggered.

11. **`e.shiftKey`**:
    - **Usage**: `e.shiftKey`
    - Returns `true` if the `Shift` key was pressed when the event was triggered.

### **Mouse Actions**

1. **`dblclick`**:
   - **Usage**: `element.addEventListener('dblclick', callback)`
   - Fires when the user double-clicks on an element.

2. **`mousedown`**:
   - **Usage**: `element.addEventListener('mousedown', callback)`
   - Fires when the user presses a mouse button down on an element.

3. **`mouseup`**:
   - **Usage**: `element.addEventListener('mouseup', callback)`
   - Fires when the user releases a mouse button over an element.

4. **`mouseenter`**:
   - **Usage**: `element.addEventListener('mouseenter', callback)`
   - Fires when the mouse pointer enters an element.

5. **`mouseleave`**:
   - **Usage**: `element.addEventListener('mouseleave', callback)`
   - Fires when the mouse pointer leaves an element.

6. **`mouseover`**:
   - **Usage**: `element.addEventListener('mouseover', callback)`
   - Fires when the mouse pointer moves over an element or one of its children.

7. **`mouseout`**:
   - **Usage**: `element.addEventListener('mouseout', callback)`
   - Fires when the mouse pointer moves out of an element or one of its children.

8. **`mousemove`**:
   - **Usage**: `element.addEventListener('mousemove', callback)`
   - Fires when the mouse pointer moves within an element.

### **Keyboard Events**

1. **`keydown`**:
   - **Usage**: `element.addEventListener('keydown', callback)`
   - Fires when the user presses a key down.

2. **`keyup`**:
   - **Usage**: `element.addEventListener('keyup', callback)`
   - Fires when the user releases a key.

3. **`keypress`**:
   - **Usage**: `element.addEventListener('keypress', callback)`
   - Fires when the user presses a key down and holds it. It only fires for keys that produce a character value.

4. **`focus`**:
   - **Usage**: `element.addEventListener('focus', callback)`
   - Fires when an element gains focus, such as when clicking into an input field.

5. **`cut`**:
   - **Usage**: `element.addEventListener('cut', callback)`
   - Fires when the user cuts text from an input or textarea.

6. **`paste`**:
   - **Usage**: `element.addEventListener('paste', callback)`
   - Fires when the user pastes text into an input or textarea.

7. **`input`**:
   - **Usage**: `element.addEventListener('input', callback)`
   - Fires when the user changes the value of an input or textarea. It triggers on each keystroke.

8. **`change`**:
   - **Usage**: `element.addEventListener('change', callback)`
   - Fires when the value of an input, select, or textarea element changes. It triggers after the input loses focus.

9. **`submit`**:
   - **Usage**: `formElement.addEventListener('submit', callback)`
   - Fires when the form is submitted.

10. **`e.preventDefault()`**:
    - **Usage**: `event.preventDefault()`
    - Prevents the default action associated with the event, such as submitting a form or following a link.

11. **`classList.contains`**:
    - **Usage**: `element.classList.contains('class-name')`
    - Returns `true` if the element contains the specified class, otherwise `false`.

12. **`confirm`**:
    - **Usage**: `confirm('Are you sure?')`
    - Displays a dialog box with a message and OK/Cancel buttons. Returns `true` if the user clicks OK, and `false` if they click Cancel.

13. **`removeChild`**:
    - **Usage**: `parentElement.removeChild(childElement)`
    - Removes a child node from the DOM tree.

