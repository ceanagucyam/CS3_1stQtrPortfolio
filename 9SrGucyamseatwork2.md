# Seatwork #2 - Getting to know CSS Position and z-index.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="author" content="Ceana E. Gucyam & Patricia A. Santos" />
  <meta name="revised" content="March 27, 2026" />
  <style>
    body { font-family: Arial, sans-serif; }
    .header, .footer {
      background: lightblue;
      padding: 10px;
    }
    .footer {
       position: fixed;
       bottom: 0;
       width: 100%;
       opacity: 0.5;
    }
    .sidebar {
      position: relative;
      top: 20px;
      left: 20px;
      background: lightgreen;
      width: 150px;
      height: 200px;
    }
    .content {
      position: absolute;
      top: 66px;
      left: 200px;
      background: lightyellow;
      width: 300px;
      height: 200px;
      z-index: 1;
    }    

    .notice {
    position: absolute;
    top: 60px;
    left: 400px;
    background: orange;
    padding: 10px;
    z-index: 2;
    }

  </style>
</head>
<body>
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">Main Content</div>
  <div class="footer">Footer</div>
  <div class="notice">Notice!</div>

</body>
</html>
```
### Step 1 (Static vs Relative):

- Add in css ```position: relative; top: 20px; left: 20px;``` to .sidebar.

 **Guided Question: What changed compared to the default static positioning? Try to give different values to top and left or you can change it to bottom, right.**
- Answer: The sidebar changes its position using offset properties (top, bottom, right, or left) without affecting the layout of the other elements. The element is relative to its normal position.

### Step 2 (Fixed):

- Add in css ```position: fixed; bottom: 0; width: 100%;``` to .footer.

 **Guided Question: What happens when you scroll the page? Why does the footer behave differently from position relative?**
- Answer: Relative elements move with the page as you scroll; meanwhile, for fixed elements, like the footer, it stays fixed in the viewport. 

### Step 3 (Absolute):

- Add in css ```position: absolute; top: 66px; left: 200px;``` to .content.

**Guided Question: What is the effect of position: absolute on an element? How is it different from fixed?**
- Answer: Absolute positioning on an element is relative to the nearest positioned ancestor, and moves when the ancestor or the page scrolls/moves. On the other hand, fixed positioning on an element stays fixed in the viewport, making it stay in the same place even when scrolling.

### Step 4 : (Absolute)

- Add in html ```<div class="notice">Notice!</div>``` and include the css below:

```css
.notice {
    position: absolute;
    top: 60px;
    left: 400px;
    background: orange;
    padding: 10px;
    z-index: 2;
}
```

- Give .content a z-index: 1.

- Guided Question: 
**Why does the notice appear on top of the content?** 
- The notice appears on top because it has a higher z-index value (z-index: 2) than the content box (z-index: 1). In CSS, elements with a higher z-index are stacked "closer" to the viewer along the z-axis.

**What happens if you swap the z‑index values?**
- If the values are swapped (Content: 2, Notice: 1), the  content box will cover the notice box. Since the notice is positioned  inside or over the content, it becomes hidden behind the yellow background.
  
- Challenge: 
    * What changes that you have to do on the code that will position .notice box on the top right corner of the .content box? Please write the code on paper as well (both html and css on the part of .notice and .content).
 ### 1.  


**HTML:**
```html
<div class="content">
    Main Content
    <div class="notice">Notice!</div>
</div> 
```
**CSS:**
``` css
.content {
    position: absolute; 
    top: 66px;
    left: 200px;
    width: 300px;
    height: 200px;
    z-index: 1;
}

.notice {
    position: absolute;
    top: 0;
    right: 0;
    z-index: 2;
}
```

    * Try to change the position of .content to relative then to fixed. What do you observed each time?
### 2. 
* **Relative:** The content box stays below the sidebar, and the notice stays stuck to the content box's top-right corner.
* **Fixed:** The yellow box "pops out"  and stays stuck to that specific part of the screen even when scrolling. The notice stays stuck to the corner of the yellow box.

    * What do you observe on about the effect of z-index on .notice and .content boxes?
### 3.
* **Requirement:** The z-index only works on elements that have a position property, either relative, absolute, fixed, or sticky. 
* **Stacking:** It creates a "layering" effect, and without it, elements usually stack based on their order in the HTML code (later elements appear on top). z-index allows us to override that order.

3. Please answer the following reflection questions (15 minutes)

    a. Could you summarize the differences between the CSS position values (static, relative, absolute, fixed)? 
   - **Static Positioning:** The default positioning where elements appear normal with the default position value `static`.
   - **Relative Positioning:** The element positioned is relative to its normal position, but can be changed using offset properties. 
   - **Absolute Positioning:** The element positioned is relative to its nearest positioned ancestor.
   - **Fixed Positioning:** The element positioned stays fixed in the viewport, making it stay in the same place even when scrolling.

    b. How does absolute positioning depend on its parent element?
    - The element with absolute positioning is removed from normal document flow and looks for its nearest parent (nearest positioned ancestor). If it finds a parent set to relative, absolute, or fixed, it uses the parent's edges as the starting point for its coordinates.

    c. How do you differentiate sticky from fixed (you can research on sticky)?
   * **Fixed:** It is always stuck to the screen from the start.
   *  **Sticky:** It acts like relative until you scroll to a specific 

    d. If you were designing a webpage for a school event, how might you use positioning to highlight important information? Please give concrete examples.
  * I would use fixed positioning for a "Register Now" button or a "When is this event" reminder so it stays visible as users scrolls through the page, basically the buttons and information that are important for the user to see. I would use absolute positioning for updates or announcements like "New" and place it on the top corner to grab attention immediately.
