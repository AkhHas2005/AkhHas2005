# I've got the following code to draw a parallelogram  

## Me
I've got the following code to draw a parallelogram using openGL in C++, however I'm unsure about the order of the vertices: 

```C++
GLfloat parallelogram[] = {
      4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f,// Top Right
      3.0f,  -1.0f, 0.0f,  0.0f, 1.0f, 0.0f,// Bottom Right
      -4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f,// Bottom Left 
      3.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f,// Top Left
      4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f,// Top Right
      -4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f,// Bottom Left
};
```  

What is the correct order?  

## Co-Pilot
Thanks for sharing your code, Hasan! You're on the right track, but the order of vertices is crucial when drawing shapes in OpenGL, especially for non-rectangular polygons like a **parallelogram**.

Let’s break down what you have:  

```cpp
GLfloat parallelogram[] = {
    4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
    3.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
   -4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left 
    3.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
   -4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left
};
```  

### Issues:  
- You have **6 vertices**, which suggests you're drawing **two triangles** to form the parallelogram.
- However, the order seems off and might not form a clean parallelogram.  

### Correct Vertex Order for Two Triangles:  
To draw a parallelogram using two triangles, you need to define the vertices in a way that the triangles share a diagonal. Here's a corrected version:  

```cpp
GLfloat parallelogram[] = {
    // Triangle 1
    3.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
   -4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left

    // Triangle 2
    3.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
    4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
};
```  

### Visual Explanation:  

```
Top Left     Top Right
   *-----------*
   |\         |
   | \        |
   |  \       |
   |   \      |
   |    \     |
   *-----*----*
Bottom Left   Bottom Right
```

This way, the two triangles are:  

- Triangle 1: Top Left, Bottom Right, Bottom Left
- Triangle 2: Top Left, Top Right, Bottom Right  

Would you like me to help you visualize this with a diagram or generate the OpenGL rendering code snippet for it?  

## Me
Can you give me another basic implementation of a parallelogram?  

## Co-Pilot
Sure! Here's a **basic implementation of a parallelogram in OpenGL using C++**, assuming you're using modern OpenGL with shaders and vertex buffers.  

### ✅ Basic Parallelogram Example (Two Triangles)  

```C++
GLfloat parallelogramVertices[] = {
    // Positions         // Colors (RGB)
    -0.5f,  0.5f, 0.0f,   1.0f, 0.0f, 0.0f, // Top Left
     0.5f, -0.5f, 0.0f,   0.0f, 1.0f, 0.0f, // Bottom Right
    -1.0f, -0.5f, 0.0f,   0.0f, 0.0f, 1.0f, // Bottom Left

    -0.5f,  0.5f, 0.0f,   1.0f, 0.0f, 0.0f, // Top Left
     1.0f,  0.5f, 0.0f,   1.0f, 1.0f, 0.0f, // Top Right
     0.5f, -0.5f, 0.0f,   0.0f, 1.0f, 0.0f, // Bottom Right
};
```

### 🧠 Explanation:  
- This defines **two triangles** that together form a parallelogram.
- The parallelogram is slanted because the top and bottom edges are not aligned vertically.
- Each vertex has a position `(x, y, z)` and a color `(r, g, b)`.

### 🛠️ How to Use:
1. Load this into a **Vertex Buffer Object (VBO)**.
2. Set up a **Vertex Array Object (VAO)**.
3. Use a **vertex shader** and **fragment shader** to render it.
4. Draw using `glDrawArrays(GL_TRIANGLES, 0, 6);`.

Would you like me to give you the full working OpenGL program including shaders and setup?  

## Me
What does this error mean?  

## Co-Pilot
Could you please share the exact **error message** you're seeing? That will help me give you a precise explanation.

However, based on your previous code snippet, here are a few **common OpenGL-related errors** and what they typically mean:

### 🔴 "GL_INVALID_OPERATION"  

This usually means you're trying to draw something without properly binding a shader program or VAO (Vertex Array Object). Make sure:   

- Your shader is compiled and linked.
- You're using `glUseProgram()` before drawing.
- Your VAO is bound with `glBindVertexArray()`.  

### 🔴 "GL_INVALID_VALUE"  

This can happen if you pass an invalid number of vertices or indices to a draw call like `glDrawArrays()` or `glDrawElements()`.  

### 🔴 Segmentation Fault / Crash  

If your vertex array isn't correctly sized or you're accessing out-of-bounds memory, it could crash. Double-check:  

- The number of vertices matches your draw call.
- You're not exceeding buffer limits.  

### 🔴 Nothing is drawn

If no error appears but nothing shows up:  

- Check your vertex coordinates — are they inside the view frustum?
- Confirm your camera/view/projection matrices are set correctly.
- Ensure your shape isn't being culled (e.g., wrong winding order).  

If you paste the **full error message**, I can explain exactly what it means and how to fix it. Want to do that now?  

## Me
Variable 'glm::tvec4<float,5>::<unnamed-tag>::<unnamed-tag>::a' is uninitialized. Always initialize a member variable (type.6).  

## Co-Pilot
The warning you're seeing:  

> **Variable 'glm::tvec4<float,5>::::::a' is uninitialized. Always initialize a member variable (type.6).**  

suggests that you're using a `glm::tvec4<float, 5>` — which is unusual because `glm::tvec4` is typically a 4-component vector (like `vec4`). A 5-component vector isn't standard in GLM, so this might be a typo or a misuse.  

### Here's what might be going wrong:  

1. **Incorrect template usage**: `glm::tvec4<float, 5>` implies you're trying to create a vector with 5 components, but `tvec4` is specifically for 4 components. If you need 5 components, you should use `glm::vec<5, float, glm::defaultp>` instead.
2. **Uninitialized member**: The warning is telling you that a member variable (likely named a) inside your vector struct is not initialized. This can happen if you declare a vector but don’t assign values to it.  

### ✅ How to fix it:  

If you're trying to use a 4-component vector (e.g., for position and alpha), use:  

```cpp
glm::vec4 myVec(1.0f, 2.0f, 3.0f, 1.0f); // x, y, z, w
```  

If you really need a 5-component vector, do this instead:  

```cpp
glm::vec<5, float, glm::defaultp> myVec(1.0f, 2.0f, 3.0f, 4.0f, 5.0f);
```  

And make sure every component is initialized.  

### 🔍 Suggestions:  
- Double-check the type you're using. If you're working with OpenGL and shaders, you likely only need `vec2`, `vec3`, or `vec4`.
- If this warning comes from a struct or class, ensure all members are initialized in the constructor or with default values.  

Would you like to share the part of your code where this vector is declared or used? I can help you correct it directly.  

## Me
This image [Uploaded Image Expired] shows what I've currently got (the green one is the meant to be the paralellogram). This is my code:  

```cpp
// Code adapted from www.learnopengl.com, www.glfw.org

#include <iostream>
#define GLEW_STATIC
#include <GL/glew.h>
#include <GLFW/glfw3.h>

// GLM Mathematics
#include <glm/glm.hpp>
#include <glm/gtc/matrix_transform.hpp>
#include <glm/gtc/type_ptr.hpp>
#include <glm/gtx/matrix_interpolation.hpp>

#include "shader.h"

int main(void)
{
    //++++create a glfw window+++++++++++++++++++++++++++++++++++++++
    GLFWwindow* window;

    if (!glfwInit()) //Initialize the library
        return -1;

    window = glfwCreateWindow(1080, 1080, "OpenGL Tanagram Coursework", NULL, NULL);
    if (!window)
    {
        glfwTerminate();
        return -1;
    }


    glfwMakeContextCurrent(window);//Make the window's context current

    //++++Initialize GLEW to setup the OpenGL Function pointers+++++++
    glewExperimental = GL_TRUE;
    glewInit();

    //++++Define the viewport dimensions++++++++++++++++++++++++++++
    glViewport(0, 0, 1080, 1080);

    //++++++++++Set up vertex data (and buffer(s)) and attribute pointers+++++++++
    GLfloat firstTriangle[] = {
   -2.0f, -2.0f, 0.0f, 1.0f, 0.0f, 0.0f, // Bottom Left
    0.0f,  0.0f, 0.0f, 1.0f, 0.0f, 0.0f, // Middle Right
   -2.0f,  2.0f, 0.0f, 1.0f, 0.0f, 0.0f, // Top Left
    };
    GLfloat secondTriangle[] = {
          0.0f,  0.0f, 0.0f,  0.0f, 0.0f, 1.0f,// Middle Bottom 
          -2.0f,  2.0f, 0.0f,  0.0f, 0.0f, 1.0f,// Top Left
          2.0f,  2.0f, 0.0f,  0.0f, 0.0f, 1.0f,// Top Right
    };
    GLfloat parallelogram[] = {
        // Triangle 1
        3.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
        4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
       -4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left

       // Triangle 2
       3.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
       4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
       4.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
    };

    GLuint VBOs[3], VAOs[3];
    glGenVertexArrays(3, VAOs);
    glGenBuffers(3, VBOs);

    // First Triangle setup
    glBindVertexArray(VAOs[0]);
    glBindBuffer(GL_ARRAY_BUFFER, VBOs[0]);
    glBufferData(GL_ARRAY_BUFFER, sizeof(firstTriangle), firstTriangle, GL_STATIC_DRAW);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)0);
    glEnableVertexAttribArray(0);
    glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)(3 * sizeof(GLfloat)));
    glEnableVertexAttribArray(1);
    glBindVertexArray(0);

    // Second Triangle setup
    glBindVertexArray(VAOs[1]);
    glBindBuffer(GL_ARRAY_BUFFER, VBOs[1]);
    glBufferData(GL_ARRAY_BUFFER, sizeof(secondTriangle), secondTriangle, GL_STATIC_DRAW);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)0);
    glEnableVertexAttribArray(0);
    glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)(3 * sizeof(GLfloat)));
    glEnableVertexAttribArray(1);
    glBindVertexArray(0);

    // Parallelogram setup
    glBindVertexArray(VAOs[2]);
    glBindBuffer(GL_ARRAY_BUFFER, VBOs[2]);
    glBufferData(GL_ARRAY_BUFFER, sizeof(parallelogram), parallelogram, GL_STATIC_DRAW);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)0);
    glEnableVertexAttribArray(0);
    glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(GLfloat), (GLvoid*)(3 * sizeof(GLfloat)));
    glEnableVertexAttribArray(1);
    glBindVertexArray(0);

    // Build and compile shader program
    GLuint shaderProgram = initShader("vert.glsl", "frag.glsl");

    // Main render loop
    while (!glfwWindowShouldClose(window))
    {
        glClear(GL_COLOR_BUFFER_BIT);

        glUseProgram(shaderProgram);
        GLint transformLoc;

        // First Triangle with rotation
        //glm::mat4 transform = glm::rotate(glm::mat4(1.0f), (GLfloat)glfwGetTime() * 0.5f, glm::vec3(0.0f, 0.0f, 1.0f));
        glm::mat4 transform = glm::mat4(1.0f);
        transform = glm::scale(transform, glm::vec3(0.2f, 0.2f, 1.0f));
        transformLoc = glGetUniformLocation(shaderProgram, "transform");
        glUniformMatrix4fv(transformLoc, 1, GL_FALSE, glm::value_ptr(transform));

        glBindVertexArray(VAOs[0]);
        glDrawArrays(GL_TRIANGLES, 0, 3);

        // Second Triangle static
        // Second Triangle scaled down
        transform = glm::mat4(1.0f);
        transform = glm::scale(transform, glm::vec3(0.2f, 0.2f, 1.0f)); // scale down uniformly
        glUniformMatrix4fv(transformLoc, 1, GL_FALSE, glm::value_ptr(transform));

        glBindVertexArray(VAOs[1]);
        glDrawArrays(GL_TRIANGLES, 0, 3);

        transform = glm::scale(transform, glm::vec3(0.2f, 0.2f, 1.0f)); // scale down uniformly
        transform = glm::translate(transform, glm::vec3(3.0f, 0.0f, 0.0f));
        glUniformMatrix4fv(transformLoc, 1, GL_FALSE, glm::value_ptr(transform));

        glBindVertexArray(VAOs[2]);
        glDrawArrays(GL_TRIANGLES, 0, 6);

        glBindVertexArray(0);

        glfwSwapBuffers(window);
        glfwPollEvents();
    }

    // Cleanup
    glDeleteVertexArrays(2, VAOs);
    glDeleteBuffers(2, VBOs);

    glfwTerminate();
    return 0;
}
```  

How do I fix the paralellogram   

## Co-Pilot
I see the issue in your screenshot: the green shape is skewed incorrectly—it looks more like a triangle stretched out rather than a proper parallelogram. This happens because the vertex coordinates you used don’t form two triangles that share a diagonal in the correct way.  

### Why It’s Wrong  

Your current parallelogram vertices:  

```
(3, 4)   (4, 4)
   *-------*
   |\      |
   | \     |
(-4,-1) (4,-1)
```  

Notice that (-4, -1) is far to the left, so the two triangles don’t align properly. The shape becomes distorted because the points aren’t forming a parallelogram—they’re forming a very long triangle plus a small one.  

### ✅ Correct Approach

For a parallelogram, opposite sides must be parallel. Let’s pick **Top Left**, **Top Right**, **Bottom Left**, **Bottom Right** so that:  

- Top Left: `(2.0f, 4.0f)`
- Top Right: `(4.0f, 4.0f)`
- Bottom Left: `(0.0f, -1.0f)`
- Bottom Right: `(2.0f, -1.0f)`

This keeps the sides parallel and the shape proportional.  

### Fixed Vertex Array  

```cpp
GLfloat parallelogram[] = {
    // Triangle 1
    2.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    2.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
    0.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left

    // Triangle 2
    2.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
    2.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
};
```  

### Why This Works  

- Two triangles share the diagonal between **Top Left** and **Bottom Right**.
- Opposite sides are parallel: `(Top Left → Top Right)` and `(Bottom Left → Bottom Right)`.  

Do you want me to:  
✅ Generate a `diagram` showing the correct parallelogram layout?  
✅ Or give you a `full corrected code snippet` with proper scaling and positioning?  

## Me
Ok with these co-ordinates, how can I make it horizontal instread of vertical:  

```cpp
GLfloat parallelogram[] = {
    // Triangle 1
    2.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    2.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
    0.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left

    // Triangle 2
    2.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    4.0f,  4.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
    2.0f, -1.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
};
```  

## Copilot
Right now, your parallelogram is oriented vertically because the **longer dimension is along the Y-axis**. To make it horizontal, you need to swap the width and height proportions so the longer dimension runs along the X-axis.  

### ✅ Horizontal Parallelogram Coordinates  

Here’s a corrected version:  

```cpp
GLfloat parallelogram[] = {
    // Triangle 1
    4.0f,  2.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
    -1.0f, 2.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Left
    -1.0f, 0.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left

    // Triangle 2
    4.0f,  2.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Top Right
    2.0f,  0.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Right
    -1.0f, 0.0f, 0.0f,  0.0f, 1.0f, 0.0f, // Bottom Left
};
```  

### What Changed  
- **X-axis spread**: Now the parallelogram spans from `-1.0f` to `4.0f` horizontally.
- **Y-axis height**: Reduced to `2.0f` so it looks wider than tall.
- The slant is created by shifting the bottom-right inward (to `2.0f`) instead of aligning directly under the top-right.  

### ✅ Quick Visual Layout  

```
Top Left (-1,2)       Top Right (4,2)
       *----------------*
        \              /
         \            /
          *----------*
Bottom Left (-1,0)   Bottom Right (2,0)
```  

Do you want me to:   
✔ Give you **a version with perfect 45° slant** (like a classic parallelogram)?  
✔ Or **apply a rotation transform in your existing code** so you can keep your original coordinates but rotate it horizontally?  

*End of this Conversation*
