### **Text utilities**

-   **Text Alignment Utilities**

    -   **`.text-start`**: Align text to the left.
    -   **`.text-center`**: Align text to the center.
    -   **`.text-end`**: Align text to the right.
    -   **`.text-{breakpoint}-{alignment}`**: Align text at specific breakpoints, e.g., `text-md-center`.

-   **Font Size Utilities**

    -   **`fs-1`**: Font size equivalent to `36px`.
    -   **`fs-2`**: Font size equivalent to `30px`.
    -   **`fs-3`**: Font size equivalent to `24px`.
    -   **`fs-4`**: Font size equivalent to `18px`.
    -   **`fs-5`**: Font size equivalent to `16px`.
    -   **`fs-6`**: Font size equivalent to `14px`.

-   **Font Weight Utilities**

    -   **`fw-light`**: Light font weight.
    -   **`fw-normal`**: Normal font weight.
    -   **`fw-bold`**: Bold font weight.
    -   **`fw-bolder`**: Bolder font weight.
    -   **`fw-lighter`**: Lighter font weight.

-   **Line Height Utilities**

    -   **`lh-1`**: Line height of `1`.
    -   **`lh-sm`**: Line height of `1.25`.
    -   **`lh-base`**: Line height of `1.5`.
    -   **`lh-lg`**: Line height of `2`.

-   **Text Transform**:

    -   **`text-lowercase`**: Transforms text to lowercase.
    -   **`text-uppercase`**: Transforms text to uppercase.
    -   **`text-capitalize`**: Capitalizes the first letter of each word.

-   **Text Wrapping**:
    -   **`text-wrap`**: Wraps the text.
    -   **`text-nowrap`**: Prevents text from wrapping.

### **Border Utilities**

-   **Border Width**: Set the width of the border.

    -   **`border`**: Adds a 1px border.
    -   **`border-0`**: Removes the border.
    -   **`border-{size}`**: Adds a thicker border, e.g., `border-2`, `border-3`, `border-4`, `border-5`.

-   **Border Color**: Set the color of the border.

    -   **`border-{color}`**: Apply a border color, e.g., `border-primary`, `border-secondary`, `border-success`.

-   **Border Radius**: Set the radius for rounded corners.
    -   **`rounded`**: Applies a default border radius.
    -   **`rounded-{size}`**: Apply a specific radius, e.g., `rounded-sm`, `rounded-lg`, `rounded-pill`.

### **Grid System**

Bootstrap's grid system uses a series of containers, rows, and columns to layout and align content. It’s built with flexbox and is fully responsive.

-   **Container**: Centered and responsive padding.

    -   **`.container`**: Fixed-width container.
    -   **`.container-fluid`**: Full-width container.

-   **Rows**: Wrap the columns and control the horizontal space.

    -   **`.row`**: Create a row to contain columns.

-   **Columns**: Define the layout of content.
    -   **`.col`**: Automatically distribute columns.
    -   **`.col-{n}`**: Define a specific column width, e.g., `col-4` (out of 12).
    -   **`.col-{breakpoint}-{n}`**: Define column width at different breakpoints, e.g., `col-md-6`.

### **Justify Content Utility**

-   **`justify-content-start`**: Aligns items to the start.
-   **`justify-content-center`**: Aligns items to the center.
-   **`justify-content-end`**: Aligns items to the end.
-   **`justify-content-between`**: Space between items.
-   **`justify-content-around`**: Space around items.
-   **`justify-content-evenly`**: Distributes items evenly.

### **Align Items**:

-   **`.align-items-start`**: Align items at the start.
-   **`.align-items-center`**: Align items at the center.
-   **`.align-items-end`**: Align items at the end.
-   **`.align-items-baseline`**: Align items along the baseline.
-   **`.align-items-stretch`**: Stretch items to fill the container.

### **Background Image Utilities**

1. **Basic Background Image**:

    - **`.bg-image`**: Apply a background image. Bootstrap doesn’t include this utility by default, so you typically add it via custom CSS.

2. **Custom Background Image**:

    - Apply a custom background image in your CSS:
        ```css
        .bg-custom {
            background-image: url("/path/to/image.jpg");
            background-size: cover;
            background-position: center;
        }
        ```

3. **Background Image Position**:

    - **`bg-{position}`**: Set the position of the background image.
        - Examples: `bg-center`, `bg-top`, `bg-bottom`, `bg-left`, `bg-right`.

4. **Background Image Size**:

    - **`bg-{size}`**: Set the size of the background image.
        - Examples: `bg-cover`, `bg-contain`.

5. **Background Image Repeat**:

    - **`bg-repeat`**: Repeat the background image.
    - **`bg-no-repeat`**: Don’t repeat the background image.

6. **Background Image Attachment**:
    - **`bg-fixed`**: Keep the background image fixed during scrolling.
    - **`bg-scroll`**: Default, scroll with the background.

### **Display Utilities**

-   **`.d-{value}`**: Controls the display property.
-   **`d-block`**: Display as block.
-   **`d-inline`**: Display as inline.
-   **`d-inline-block`**: Display as inline-block.
-   **`d-none`**: Hide element (display: none).
-   **`d-{breakpoint}-{value}`**: Control display at different breakpoints, e.g., `d-md-block`.

### **Flexbox Utilities**

-   **Flex Direction**:

    -   **`.flex-row`**: Flex items in a row (default).
    -   **`.flex-column`**: Flex items in a column.
    -   **`.flex-row-reverse`**: Reverse the row direction.
    -   **`.flex-column-reverse`**: Reverse the column direction.

-   **Flex Wrapping**:
    -   **`.flex-wrap`**: Enable flex wrapping.
    -   **`.flex-nowrap`**: Disable flex wrapping.
    -   **`.flex-wrap-reverse`**: Reverse the wrapping direction.

### **Visibility Utilities**

-   **`.visible`**: Makes an element visible.
-   **`.invisible`**: Makes an element invisible but still takes up space.
-   **`.visually-hidden`**: Hide visually but keep accessible to screen readers.

### **Position Utilities**

-   **`.position-static`**: Default positioning.
-   **`.position-relative`**: Position relative to its normal position.
-   **`.position-absolute`**: Position absolutely relative to the nearest positioned ancestor.
-   **`.position-fixed`**: Position fixed relative to the viewport.
-   **`.position-sticky`**: Position sticky based on the user's scroll position.

### **Overflow Utilities**

-   **`.overflow-auto`**: Adds scrollbars when content overflows.
-   **`.overflow-hidden`**: Hides overflowed content.
-   **`.overflow-visible`**: Default, content is visible when it overflows.
-   **`.overflow-scroll`**: Always shows scrollbars.

### **Sizing Utilities**

-   **Width**:

    -   **`w-25`**: Width of 25%.
    -   **`w-50`**: Width of 50%.
    -   **`w-75`**: Width of 75%.
    -   **`w-100`**: Width of 100%.
    -   **`w-auto`**: Width based on the content.

-   **Height**:

    -   **`h-25`**: Height of 25%.
    -   **`h-50`**: Height of 50%.
    -   **`h-75`**: Height of 75%.
    -   **`h-100`**: Height of 100%.
    -   **`h-auto`**: Height based on the content.###

-   **Padding Utilities**

    -   **`p-{size}`**: Applies padding to all sides of an element. (`size` can be `0`, `1`, `2`, `3`, `4`, `5`)
    -   **`px-{size}`**: Applies horizontal padding (left and right).
    -   **`py-{size}`**: Applies vertical padding (top and bottom).
    -   **`pt-{size}`**: Applies padding to the top.
    -   **`pr-{size}`**: Applies padding to the right.
    -   **`pb-{size}`**: Applies padding to the bottom.
    -   **`pl-{size}`**: Applies padding to the left.

-   **Margin Utilities**
    -   **`m-{size}`**: Applies margin to all sides of an element. (`size` can be `0`, `1`, `2`, `3`, `4`, `5`, `auto`)
    -   **`mx-{size}`**: Applies horizontal margin (left and right).
    -   **`my-{size}`**: Applies vertical margin (top and bottom).
    -   **`mt-{size}`**: Applies margin to the top.
    -   **`mr-{size}`**: Applies margin to the right.
    -   **`mb-{size}`**: Applies margin to the bottom.
    -   **`ml-{size}`**: Applies margin to the left.

### **Color Utilities**

-   **Background Color**:

    -   **`bg-primary`**: Primary background color.
    -   **`bg-secondary`**: Secondary background color.
    -   **`bg-success`**: Success background color.
    -   **`bg-danger`**: Danger background color.
    -   **`bg-warning`**: Warning background color.
    -   **`bg-info`**: Info background color.
    -   **`bg-light`**: Light background color.
    -   **`bg-dark`**: Dark background color.
    -   **`bg-white`**: White background color.

-   **Text Color**:
    -   **`text-primary`**: Primary text color.
    -   **`text-secondary`**: Secondary text color.
    -   **`text-success`**: Success text color.
    -   **`text-danger`**: Danger text color.
    -   **`text-warning`**: Warning text color.
    -   **`text-info`**: Info text color.
    -   **`text-light`**: Light text color.
    -   **`text-dark`**: Dark text color.
    -   **`text-muted`**: Muted text color.

### **Shadow Utilities**

-   **`shadow-none`**: No shadow.
-   **`shadow-sm`**: Small shadow.
-   **`shadow`**: Default shadow.
-   **`shadow-lg`**: Large shadow.

### **Rounded Utilities**

-   **`rounded`**: Default border-radius.
-   **`rounded-sm`**: Small border-radius.
-   **`rounded-lg`**: Large border-radius.
-   **`rounded-circle`**: Circular border-radius.
-   **`rounded-pill`**: Pill-shaped border-radius.

### **Opacity Utilities**

-   **`opacity-25`**: 25% opacity.
-   **`opacity-50`**: 50% opacity.
-   **`opacity-75`**: 75% opacity.
-   **`opacity-100`**: 100% opacity (default).

### **Float Utilities**

-   **`float-start`**: Floats element to the left.
-   **`float-end`**: Floats element to the right.
-   **`float-none`**: No floating (default).

### **Visibility Utilities**

-   **`visible`**: Make an element visible.
-   **`invisible`**: Make an element invisible but still takes up space.
