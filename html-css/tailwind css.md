### **Padding Utilities**

-   **`p-{size}`**: Applies padding to all sides of an element.

-   **`px-{size}`**: Applies horizontal padding (left and right) only.

-   **`py-{size}`**: Applies vertical padding (top and bottom) only.

-   **`pt-{size}`**: Applies padding to the top.

-   **`pr-{size}`**: Applies padding to the right.

-   **`pb-{size}`**: Applies padding to the bottom.

-   **`pl-{size}`**: Applies padding to the left.

In Tailwind CSS, margin utilities help you add space outside of an element. Here’s a guide to using margin utilities:

### **Margin Utilities**

-   **`m-{size}`**: Applies margin to all sides of an element.

-   **`mx-{size}`**: Applies horizontal margin (left and right) only.

-   **`my-{size}`**: Applies vertical margin (top and bottom) only.

-   **`mt-{size}`**: Applies margin to the top.

-   **`mr-{size}`**: Applies margin to the right.

-   **`mb-{size}`**: Applies margin to the bottom.

-   **`ml-{size}`**: Applies margin to the left.

### **Font Size Utilities**

-   **`text-xs`**: Extra small text (0.75rem / 12px)
-   **`text-sm`**: Small text (0.875rem / 14px)
-   **`text-base`**: Base text (1rem / 16px, default size)
-   **`text-lg`**: Large text (1.125rem / 18px)
-   **`text-xl`**: Extra large text (1.25rem / 20px)
-   **`text-2xl`**: 2x extra large text (1.5rem / 24px)
-   **`text-3xl`**: 3x extra large text (1.875rem / 30px)
-   **`text-4xl`**: 4x extra large text (2.25rem / 36px)
-   **`text-5xl`**: 5x extra large text (3rem / 48px)
-   **`text-6xl`**: 6x extra large text (3.75rem / 60px)
-   **`text-7xl`**: 7x extra large text (4.5rem / 72px)
-   **`text-8xl`**: 8x extra large text (6rem / 96px)
-   **`text-9xl`**: 9x extra large text (8rem / 128px)

### **Font Weight Utilities**

-   **`font-thin`**: Thin (100)
-   **`font-extralight`**: Extra light (200)
-   **`font-light`**: Light (300)
-   **`font-normal`**: Normal (400)
-   **`font-medium`**: Medium (500)
-   **`font-semibold`**: Semi-bold (600)
-   **`font-bold`**: Bold (700)
-   **`font-extrabold`**: Extra bold (800)
-   **`font-black`**: Black (900)

In Tailwind CSS, line height is controlled using utility classes that set the `line-height` property. These classes help you adjust the vertical spacing between lines of text in your elements.

### **Line Height Utilities**

Tailwind provides a set of predefined line height values:

-   **`leading-none`**: `line-height: 1;`
-   **`leading-tight`**: `line-height: 1.25;`
-   **`leading-snug`**: `line-height: 1.375;`
-   **`leading-normal`**: `line-height: 1.5;` (default value)
-   **`leading-relaxed`**: `line-height: 1.625;`
-   **`leading-loose`**: `line-height: 2;`

### **Border Utilities**

-   **Border Width**: Set the width of the border.

    -   `border-{width}`: `border-0`, `border-2`, `border-4`, `border-8`

-   **Border Color**: Set the color of the border.

    -   `border-{color}`: `border-gray-500`, `border-red-600`, `border-blue-300`

-   **Border Style**: Set the style of the border.

    -   `border-{style}`: `border-solid`, `border-dashed`, `border-dotted`, `border-double`, `border-none`

-   **Border Radius**: Set the radius for rounded corners.
    -   `rounded-{size}`: `rounded-sm`, `rounded-md`, `rounded-lg`, `rounded-xl`, `rounded-full`

### **Grid Container**

-   **`grid`**: Applies `display: grid` to the container.
-   **`grid-cols-{n}`**: Defines the number of columns in the grid, e.g., `grid-cols-3`.
-   **`grid-rows-{n}`**: Defines the number of rows in the grid, e.g., `grid-rows-3`.
-   **`grid-flow-{direction}`**: Controls the direction items are placed in the grid, e.g., `grid-flow-row`, `grid-flow-col`.

### **Grid Item Properties**

-   **`col-span-{n}`**: Defines how many columns an item should span, e.g., `col-span-2`.
-   **`row-span-{n}`**: Defines how many rows an item should span, e.g., `row-span-2`.
-   **`col-start-{n}`**: Defines the starting column line for an item, e.g., `col-start-2`.
-   **`col-end-{n}`**: Defines the ending column line for an item, e.g., `col-end-4`.
-   **`row-start-{n}`**: Defines the starting row line for an item, e.g., `row-start-2`.
-   **`row-end-{n}`**: Defines the ending row line for an item, e.g., `row-end-4`.

### **Gap**

-   **`gap-{size}`**: Defines the gap between grid items, e.g., `gap-4`.
-   **`gap-x-{size}`**: Defines the horizontal gap, e.g., `gap-x-4`.
-   **`gap-y-{size}`**: Defines the vertical gap, e.g., `gap-y-4`.

### **Justify Content Utility**

-   `justify-start`
-   `justify-center`
-   `justify-end`
-   `justify-between`
-   `justify-around`
-   `justify-evenly`

### **Justify Self Utility**

-   `justify-self-auto`
-   `justify-self-start`
-   `justify-self-center`
-   `justify-self-end`
-   `justify-self-stretch`

### **Align Items Utility**

-   `items-start`
-   `items-center`
-   `items-end`
-   `items-baseline`
-   `items-stretch`

### **Align Self Utility**

-   `self-auto`
-   `self-start`
-   `self-center`
-   `self-end`
-   `self-baseline`
-   `self-stretch`

### **Background Image Utilities**

1. **Basic Background Image**:

    - **`bg-{image}`**: Apply a background image using predefined images. Tailwind doesn’t include default image utilities, so you typically use `bg-[url('/path/to/image')]`.

2. **Custom Background Image**:

    - **`bg-[url('/path/to/image')]`**: Apply a custom background image by specifying the URL in square brackets.

3. **Background Image Position**:

    - **`bg-{position}`**: Set the position of the background image.
        - Examples: `bg-center`, `bg-top`, `bg-bottom`, `bg-left`, `bg-right`

4. **Background Image Size**:

    - **`bg-{size}`**: Set the size of the background image.
        - Examples: `bg-cover`, `bg-contain`

5. **Background Image Repeat**:

    - **`bg-repeat`**: Repeat the background image.
        - Examples: `bg-repeat`, `bg-no-repeat`

6. **Background Image Attachment**:
    - **`bg-fixed`**: Keep the background image fixed during scrolling.
    - **`bg-local`**: Scroll with the element.
    - **`bg-scroll`**: Default, scroll with the background.

### **Example**

```html
<div class="bg-[url('/path/to/image.jpg')] bg-cover bg-center h-64">
    This div has a background image that covers the entire area and is centered.
</div>

<div
    class="bg-[url('/path/to/image.jpg')] bg-no-repeat bg-bottom bg-fixed h-64"
>
    This div has a background image that does not repeat, is fixed, and aligned
    to the bottom.
</div>
```

In these examples:

-   The first div uses `bg-[url('/path/to/image.jpg')]` to set a background image, `bg-cover` to make it cover the entire element, and `bg-center` to center it.
-   The second div uses `bg-no-repeat` to prevent repetition, `bg-bottom` to position the image at the bottom, and `bg-fixed` to keep the image fixed during scrolling.
