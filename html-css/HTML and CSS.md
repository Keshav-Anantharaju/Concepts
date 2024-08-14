#  HTML and CSS for beginners

## HTML

### Introduction to HTML

- HTML (HyperText Markup Language) is the standard markup language used to create web pages. It structures the content on the web by using a series of elements, which are defined by tags. These elements can contain text, images, links, and other types of data, which are then rendered by web browsers.

### HTML Structure

- A basic HTML document is structured as follows:

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document Title</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <!-- Content goes here -->
    </body>
    </html>
    ```
___
### The `html` Root Element

- The `<html>` tag is the root element of an HTML document. All other HTML elements must be descendants of this tag. It usually includes the `lang` attribute to specify the language of the content.

    Example:

    ```html
    <html lang="en">
        <!-- head and body elements go here -->
    </html>
    ```
___
### The `head` Element

- The `<head>` element is a container for metadata (data about data) and links to external resources. It is not displayed directly on the web page but is critical for defining how the page should be interpreted and rendered by the browser.

#### Common Elements Inside the `head`

- **`<meta>` Tags**: These provide metadata such as character set, author, viewport settings, and keywords.
- **`<title>` Tag**: Defines the title of the document, which appears in the browser's title bar or tab.
- **`<link>` Tag**: Used to link external resources like CSS stylesheets or favicon icons.
- **`<script>` Tag**: Used to include or reference JavaScript files.

### 1. `meta` Tags

- `<meta>` tags are used to specify metadata about the HTML document, and they often appear within the `<head>` section.

    **Common `meta` Tags**

    
    - **The `viewport` Meta Tag**

        - The `<meta name="viewport">` tag is crucial for responsive web design. It allows the page to adjust to the screen size of the device it is being viewed on.

            Example:

            ```html
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            ```

        - **`width=device-width`**: Sets the width of the page to follow the screen-width of the device (from desktops to mobile devices).
        - **`initial-scale=1.0`**: Sets the initial zoom level when the page is first loaded.

    - **`charset` Attribute**

        - The `charset` attribute within a `<meta>` tag specifies the character encoding for the HTML document. UTF-8 is the most widely used encoding, allowing for the representation of a vast range of characters from various languages.

            Example:

            ```html
            <meta charset="UTF-8">
            ```

            Some charatcers encoders:
            - **UTF-8** is recommended for most modern web pages due to its efficiency, compatibility, and support for all languages and symbols.
            - **ASCII** is a subset of most modern encodings (like UTF-8), ensuring broad compatibility. ASCII is widely used in older systems and protocols where simplicity and compatibility are paramount.

            - **ISO-8859-1** or **Windows-1252** may still be used in legacy systems or for specific Western European language content.
            - **UTF-16** can be considered in specialized cases, especially for content heavy in non-Latin characters.
            

### 2. The `link` Tag

- The `<link>` tag is used to define relationships between the current document and external resources. It is most commonly used to link CSS stylesheets.

    Example:

    ```html
    <link rel="stylesheet" href="styles.css">
    ```

    **Attributes:**
    - **`rel`**: Specifies the relationship between the current document and the linked resource. Common values include `"stylesheet"` for CSS files.
    - **`href`**: Specifies the URL of the linked resource.

### 3. The `script` Tag
- Used to embed or link to JavaScript in an HTML document, with options for inline scripts and external files.

    ```html
    <script src="main.js"></script>
    ```

### 4. The `title` Tag
- Defines the page's title, crucial for both user experience and SEO, and should be placed within the `<head>` section. 

    ```html
    <title> Understanding Title Tags </title>
    ```
___
### The `body` Element

- The `<body>` element contains the content of the HTML document. This includes text, images, videos, and interactive elements like forms and buttons.

    Example:

    ```html
    <body>
        <h1>Welcome to My Website</h1>
        <p>This is a sample paragraph.</p>
    </body>
    ```
___
### Semantic vs. Non-Semantic Tags

- **Semantic Tags**: 
    - These tags clearly define their content. Examples include `<header>`, `<footer>`, `<article>`, `<section>`, and `<nav>`. They improve accessibility and SEO ( search engine optimization ) by providing context to the structure of the webpage.
  
        Example:
        ```html
        <article>
            <h2>Article Title</h2>
            <p>This is the content of the article.</p>
        </article>
        ```

- **Non-Semantic Tags**: 
    - These tags do not convey any information about the content. Examples include `<div>` and `<span>`. They are often used for styling or scripting purposes.

        Example:
        ```html
        <div class="container">
            <span>This is some text inside a span.</span>
        </div>
        ```

### Inline vs. Block Elements

- **Inline Elements**:
    - Inline elements do not start on a new line. They only take up as much width as necessary and allow other inline elements to sit next to them on the same line.
    - **Examples**: `<a>`, `<span>`, `<img>`, `<strong>`, `<em>`.
    - Useful for formatting small parts of text or embedding elements within a block of content.

        ```html
        <p>This is an <span style="color: red;">inline</span> element.</p>
        ```

- **Block Elements**:
    - Block elements start on a new line and take up the full width available, pushing other elements to the next line.
    - **Examples**: `<div>`, `<h1>`, `<p>`, `<ul>`, `<section>`.
    - Useful for creating structural divisions on a page.

        ```html
        <div>
            <h1>This is a block element</h1>
            <p>This paragraph is inside a block element.</p>
        </div>
        ```
- **Inline-Block Elements**

    - Inline-block elements combine characteristics of both inline and block elements. 
    - Like inline elements, inline-block allows other elements to sit next to them on the same line. 
    - However, they also behave like block elements iwhere we can set width, height, and margins, which is not possible with purely inline elements.

        ```html
        <div>
            <div style="display: inline-block">Box 1</div>
            <div style="display: inline-block">Box 1</div>
            <div style="display: inline-block">Box 1</div>
        </div>
___
### Attributes

- HTML elements can have attributes, which provide additional information about the element. Attributes are always included in the opening tag and usually consist of a name and a value.

    Example:

    ```html
    <img src="image.jpg" alt="Description of image">
    ```

    - **`src`**: Specifies the source of the image.
    - **`alt`**: Provides alternative text for the image, improving accessibility.

#### `class` and `id` Attributes

- **`class`**: Used to define a group of elements that can be styled or manipulated with CSS or JavaScript. Multiple elements can share the same class.
  
    Example:
    ```html
    <div class="highlight">This text is highlighted.</div>
    ```

- **`id`**: A unique identifier for a specific element. An `id` should be unique within the document, making it suitable for targeting elements with CSS or JavaScript.

    Example:
    ```html
    <div id="main-header">This is the main header.</div>
    ```
___
## CSS

### Inline and External CSS
- **Inline CSS:**
    - CSS rules are applied directly within HTML elements using the style attribute.
    - Useful for quick styling but not recommended for large projects due to lack of separation of concerns.

        ```html
        <p style="color: blue; font-size: 16px;">This is an inline-styled paragraph.</p>
        ```
- **External CSS:**

    - CSS rules are defined in separate `.css` files and linked to the HTML document using the `<link>` tag.

    - Recommended for maintaining clean, manageable code and reusing styles across multiple pages.

        ```html
        <!-- index.html -->
        <link rel="stylesheet" href="styles.css">
        ```
        ```css
        /* styles.css */
        p {
            color: blue;
            font-size: 16px;
        }
        ```

### CSS reset
- A CSS reset is a set of rules that removes default browser styles to ensure consistency across different browsers. 
    
    Common reset styles include setting margins, paddings, and border styles to zero.
    Example
    ```css
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    ```

### CSS Box model
- The CSS box model describes the rectangular boxes generated for elements in the document tree. Each box consists of four areas:

    - **Content:** The actual content of the box, such as text or an image.

    - **Padding:** Space between the content and the border, inside the element.
    - **Border:** A line surrounding the padding (if any) and content.
    - **Margin:** Space outside the border, separating the element from other elements.

    ```css
    .box {
        width: 300px;
        padding: 20px;
        border: 5px solid black;
        margin: 15px;
    }
    ```

### CSS Size and units
- CSS supports various units for specifying sizes:

    - **Pixels (px):** Fixed-size units.

    - **Em:** Relative to the font size of the element.
    - **Rem:** Relative to the font size of the root element (<html>).
    - **Percentages (%):** Relative to the parent element’s size.
    - **Viewport Units (vw, vh):** Relative to the viewport's width (vw) and height (vh).
    - **Absolute Units:** Such as cm, mm, in, pt, and pc.
    
        Example
        ```css
        .element {
            width: 50%;          /* 50% of the parent element's width */
            font-size: 1.5em;    /* 1.5 times the font size of the parent element */
            height: 100vh;       /* 100% of the viewport height */
        }
        ```

### CSS colors
- CSS supports several methods for specifying colors:

    - **Named Colors:** Predefined color names (e.g., red, blue, green).

    - **Hexadecimal (Hex):** #RRGGBB or #RGB (e.g., #ff0000).
    - **RGB:** rgb(R, G, B) where R, G, and B are integers from 0 to 255 (e.g., rgb(255, 0, 0)).
    - **RGBA:** rgba(R, G, B, A) where A is the alpha channel for opacity (e.g., rgba(255, 0, 0, 0.5)).
    - **HSL:** hsl(H, S%, L%) where H is the hue, S is the saturation, and L is the lightness (e.g., hsl(0, 100%, 50%)).
    - **HSLA:** hsla(H, S%, L%, A) where A is the alpha channel for opacity (e.g., hsla(0, 100%, 50%, 0.5)).


### CSS positioning
**Relative Positioning**:
- The element is positioned relative to its normal position in the document flow. The `top`, `right`, `bottom`, and `left` properties are used to offset it.
- Allows for minor adjustments to an element’s position while keeping its space in the layout.

    ```css
    .relativeElement {
        position: relative;
        top: 10px;
        left: 15px;
    }
    ```

**Absolute Positioning**:
- The element is positioned relative to the nearest positioned ancestor (i.e., an ancestor with any position value other than `static`). If no such ancestor exists, it is positioned relative to the initial containing block (usually the viewport).
-  Useful for precise positioning of elements on the page.

    ```css
    .absoluteElement {
        position: absolute;
        top: 20px;
        right: 10px;
    }
    ```

### Common CSS Styling Classes

**Styling Classes**:

- **Examples**:

    - `.text-center`: Centers text alignment.
    - `.btn`: Styles for buttons.
    - `.hidden`: Hides elements.

    ```css
    .text-center {
        text-align: center;
    }

    .btn {
        padding: 10px 20px;
        background-color: #007bff;
        color: white;
        border: none;
        border-radius: 5px;
    }

    .hidden {
        display: none;
    }
    ```

### CSS Specificity
- Determines which CSS rules apply to an element when multiple rules match. It is calculated based on the types of selectors used in the rule.
- **Specificity Hierarchy**:

    1. Inline styles (e.g., `style="color: red;"`) - Highest specificity.
    2. ID selectors (e.g., `#header`) - Higher specificity.
    3. Class selectors, attribute selectors, pseudo-classes (e.g., `.nav`, `[type="text"]`, `:hover`) - Medium specificity.
    4. Element selectors, pseudo-elements (e.g., `div`, `::before`) - Lowest specificity.

        ```css
        #header { color: blue; } /* Highest specificity */
        .nav { color: green; }
        div { color: red; } /* Lowest specificity */
        ```

### CSS Responsive Queries
- Used to apply different styles for different screen sizes or device characteristics.
- Essential for creating responsive web designs that adapt to various devices.

    ```css
    @media (max-width: 768px) {
        .container {
            width: 100%;
        }
    }

    @media (min-width: 769px) {
        .container {
            width: 80%;
        }
    }
    ```

### Flexbox and Grid

**Flexbox**:
- A one-dimensional layout model for distributing space along a single axis (row or column).
- Ideal for layout components in a row or column, aligning items, and handling spacing.

    ```css
    .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    ```

**CSS Grid**:
- A two-dimensional layout model for creating complex grid-based designs with rows and columns.
- Useful for creating complex layouts with both rows and columns, such as grid systems and magazine layouts.

    ```css
    .grid-container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 10px;
    }

    .grid-item {
        background: lightgray;
    }
    ```

### Transition Property
- The transition property allows for smooth changes between CSS property values. 
- It specifies the duration, timing function, and properties to transition.

    Example
    ```css
    .transition-box {
        width: 100px;
        height: 100px;
        background-color: blue;
        transition: background-color 0.5s ease, width 0.5s ease;
    }

    .transition-box:hover {
        background-color: red;
        width: 200px;
    }
    ```
    In this example, the background color and width transition smoothly when the element is hovered over.

### Media Queries
- Media queries are used to apply styles based on the characteristics of the device, such as its width, height, or resolution.

    Example
    ```css
    /* Mobile devices */
    @media (max-width: 600px) {
        .responsive {
            font-size: 14px;
        }
    }

    /* Tablets and larger devices */
    @media (min-width: 601px) and (max-width: 1024px) {
        .responsive {
            font-size: 18px;
        }
    }

    /* Desktops */
    @media (min-width: 1025px) {
        .responsive {
            font-size: 24px;
        }
    }
    ```

## Conclusion
- HTML and CSS are the core of web design, facilitating the creation of engaging, accessible, and responsive websites. Proficiency in both is crucial for any web developer, as they serve as the foundation for all modern web technologies.