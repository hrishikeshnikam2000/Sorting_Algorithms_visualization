# Manual Responsiveness Testing Guide

This guide provides instructions on how to manually test the responsiveness of the Sorting Visualizer application.

## 1. Running the Application

1.  Open your terminal or command prompt.
2.  Navigate to the root directory of the project.
3.  Ensure all dependencies are installed by running:
    ```bash
    npm install
    ```
4.  Start the development server:
    ```bash
    npm start
    ```
5.  This will typically open the application automatically in your default web browser (e.g., at `http://localhost:3000`). If it doesn't, open your browser and navigate to this URL.

## 2. Using Browser Developer Tools for Responsive Testing

Most modern web browsers (Chrome, Firefox, Edge, Safari) have built-in developer tools that allow you to simulate different screen sizes.

1.  **Open Developer Tools**:
    *   Right-click on the page and select "Inspect" or "Inspect Element".
    *   Alternatively, press `F12` (Windows/Linux) or `Cmd+Opt+I` (Mac).

2.  **Toggle Device Mode / Responsive Design Mode**:
    *   Look for an icon that often resembles a tablet and phone (e.g., in Chrome, it's labeled "Toggle device toolbar"; in Firefox, "Responsive Design Mode"). Click this icon.
    *   The page view will change to a responsive mode, often with a toolbar at the top or side to control the viewport dimensions.

3.  **Simulate Different Screen Sizes**:
    *   **Predefined Devices**: The toolbar usually has a dropdown menu with a list of common devices (e.g., "iPhone SE", "iPad Air", "Galaxy S8+"). Select these to test standard device viewports.
    *   **Custom Dimensions**: You can manually enter width and height values into input fields in the device mode toolbar.
    *   **Drag to Resize**: Often, you can drag the edges of the simulated viewport to resize it dynamically.

4.  **Suggested Breakpoints and Sizes to Test**:
    *   **Desktop**:
        *   1920x1080 (Full HD)
        *   1366x768 (Common laptop)
    *   **Tablet (Portrait & Landscape)**:
        *   768x1024 (e.g., iPad portrait - **Test media query at 768px width**)
        *   1024x768 (e.g., iPad landscape)
    *   **Mobile (Portrait & Landscape)**:
        *   480x854 (Generic mobile - **Test media query at 480px width**)
        *   375x667 (e.g., iPhone SE, 6, 7, 8)
        *   414x896 (e.g., iPhone XR)
        *   360x640 (e.g., Common Android)
    *   Test resizing the window manually to observe how the layout flows between and beyond these specific breakpoints.

## 3. What to Look For During Testing

As you view the application at different screen sizes, pay attention to the following:

*   **`SortingVisualizer` Component Fit**:
    *   Does the entire `.array-container` (the area holding the bars) fit within the screen width without causing horizontal scrolling?
    *   Are the individual `.array-bar` elements visible and distinguishable? They should not be so thin or crowded that they become a solid block, nor should they overflow their container.

*   **No Horizontal Scrolling**:
    *   Ideally, there should be no horizontal scrollbar for the page at any of the tested screen sizes. If there is, it indicates that some content is wider than the viewport.

*   **Media Query Activation**:
    *   **At or below 768px width (Tablet)**:
        *   Does the `.array-container` width adjust to `95%`?
        *   Does the `.array-bar` width change to `1%` and its margin to `0 0.2vw`? (Inspect the CSS properties using the developer tools' "Elements" or "Inspector" panel).
    *   **At or below 480px width (Mobile)**:
        *   Does the `.array-container` width adjust to `98%`?
        *   Does the `.array-bar` width change to `1.5%` and its margin to `0 0.3vw`? (Inspect CSS properties).

*   **Layout Integrity**:
    *   Are there any overlapping elements (e.g., text over buttons, parts of the visualizer overlapping other UI elements)?
    *   Is the layout broken in any way (e.g., elements pushed to unexpected locations)?

*   **`App-header` Behavior**:
    *   With `min-height: auto`, does the `App-header` (the dark bar at the top, if present and containing content) shrink or grow appropriately based on its content? It should not force an unnecessarily large height on the page. If the header is empty or has minimal content, it should be relatively small.

*   **General Usability**:
    *   Are all interactive elements (buttons, sliders, etc., if any are present) easily clickable/tappable on smaller screens?
    *   Is text readable?

By systematically checking these aspects across a range of device sizes, you can verify that the responsiveness improvements are working as intended.
