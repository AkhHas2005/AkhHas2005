# Mock Exam Walkthrough for COS6021-B  

## Me
I have this mock exam for my university module. Can you walk through each question and how to do it?  

## Co-Pilot
Absolutely, Hasan! Let's break down each question from your COS6021-B mock exam and walk through how to approach and solve them. I’ll guide you with the concepts, formulas, and steps you’d use—perfect for revision and confidence-building.

---

## 🧮 Question 1: Transformation Matrices (33 marks)

### A) Reflection about the x-axis (8 marks)
- **Concept**: A reflection across the x-axis flips the y-coordinate.
- **Matrix**:
  \[
  \begin{bmatrix}
  1 & 0 \\
  0 & -1
  \end{bmatrix}
  \]
- **Explanation**: This matrix keeps x the same and negates y.

---

### B) Rotate vertex (1,2) by 45° about origin (12 marks)
- **Rotation matrix**:
  \[
  \begin{bmatrix}
  \cos\theta & -\sin\theta \\
  \sin\theta & \cos\theta
  \end{bmatrix}
  \]
  For \(\theta = 45^\circ\), \(\cos(45^\circ) = \sin(45^\circ) = \frac{\sqrt{2}}{2}\)

- **Apply to (1,2)**:
  \[
  \begin{bmatrix}
  \frac{\sqrt{2}}{2} & -\frac{\sqrt{2}}{2} \\
  \frac{\sqrt{2}}{2} & \frac{\sqrt{2}}{2}
  \end{bmatrix}
  \cdot
  \begin{bmatrix}
  1 \\
  2
  \end{bmatrix}
  =
  \begin{bmatrix}
  \frac{\sqrt{2}}{2}(1 - 2) \\
  \frac{\sqrt{2}}{2}(1 + 2)
  \end{bmatrix}
  =
  \begin{bmatrix}
  -\frac{\sqrt{2}}{2} \\
  \frac{3\sqrt{2}}{2}
  \end{bmatrix}
  \]

---

### C) Rotate (1,2) by 30°, then translate by (2,3) (13 marks)
- **Rotation matrix (30°)**:
  \[
  \begin{bmatrix}
  \cos(30^\circ) & -\sin(30^\circ) \\
  \sin(30^\circ) & \cos(30^\circ)
  \end{bmatrix}
  =
  \begin{bmatrix}
  \frac{\sqrt{3}}{2} & -\frac{1}{2} \\
  \frac{1}{2} & \frac{\sqrt{3}}{2}
  \end{bmatrix}
  \]

- **Apply to (1,2)**:
  \[
  \begin{bmatrix}
  \frac{\sqrt{3}}{2}(1) - \frac{1}{2}(2) \\
  \frac{1}{2}(1) + \frac{\sqrt{3}}{2}(2)
  \end{bmatrix}
  =
  \begin{bmatrix}
  \frac{\sqrt{3}}{2} - 1 \\
  \frac{1}{2} + \sqrt{3}
  \end{bmatrix}
  \]

- **Then translate**:
  Add (2,3) to the result above.

- **Final transformation matrix** (homogeneous coordinates):
  \[
  \begin{bmatrix}
  \frac{\sqrt{3}}{2} & -\frac{1}{2} & 2 \\
  \frac{1}{2} & \frac{\sqrt{3}}{2} & 3 \\
  0 & 0 & 1
  \end{bmatrix}
  \]

---

## 📐 Question 2: Vector Operations (33 marks)

### A) Vectors u = (1,2), w = (3,4) (16 marks)
- **a) u + w** = (1+3, 2+4) = (4,6)
- **b) u - w** = (1−3, 2−4) = (−2,−2)
- **c) |u|** = magnitude = \(\sqrt{1^2 + 2^2} = \sqrt{5}\)

---

### B) Cross product u = (1,2,1), w = (1,2,4) (17 marks)
- Use determinant method:
  \[
  u \times w =
  \begin{vmatrix}
  \mathbf{i} & \mathbf{j} & \mathbf{k} \\
  1 & 2 & 1 \\
  1 & 2 & 4
  \end{vmatrix}
  =
  \mathbf{i}(2\cdot4 - 1\cdot2) - \mathbf{j}(1\cdot4 - 1\cdot1) + \mathbf{k}(1\cdot2 - 2\cdot1)
  =
  \mathbf{i}(8 - 2) - \mathbf{j}(4 - 1) + \mathbf{k}(2 - 2)
  =
  (6, -3, 0)
  \]

---

## 🧵 Question 3: Geometry and Curves (34 marks)

### A) Lines in triangle with vertices (-1,1), (2,3), (1,-1) (12 marks)
- **Find equations of lines** between each pair using:
  \[
  \text{slope} = \frac{y_2 - y_1}{x_2 - x_1}, \quad \text{then use } y - y_1 = m(x - x_1)
  \]
- Do this for:
  - Line AB: (-1,1) to (2,3)
  - Line BC: (2,3) to (1,-1)
  - Line CA: (1,-1) to (-1,1)

---

### B) Linear Bézier curve through (1,4,2) and (3,5,7) (10 marks)
- **Formula**:
  \[
  B(t) = (1 - t)P_0 + tP_1
  \]
  where \(P_0 = (1,4,2)\), \(P_1 = (3,5,7)\), \(t \in [0,1]\)

- **Example**: At \(t = 0.5\),
  \[
  B(0.5) = 0.5(1,4,2) + 0.5(3,5,7) = (2, 4.5, 4.5)
  \]

---

### C) Quadratic curve through (-1,1), (2,3), (1,-1) (12 marks)
- **Quadratic Bézier formula**:
  \[
  B(t) = (1 - t)^2P_0 + 2(1 - t)tP_1 + t^2P_2
  \]
  where \(P_0 = (-1,1)\), \(P_1 = (2,3)\), \(P_2 = (1,-1)\)

- Plug in values for \(t = 0, 0.5, 1\) to sketch or understand the curve.

---

Would you like me to help you build a revision sheet or practice these in Python or C#? I can also help you prep for explaining these in a viva or exam setting.  

## Me
Ok so for the first question (1A), I know what to do but how do I explain my working for the reflection?  

## Co-Pilot
Great question, Hasan — explaining your working clearly is key to scoring full marks. Here's how you can structure your answer for **Question 1A: Reflection about the x-axis**, with clarity and precision:

---

### ✅ Step-by-Step Explanation for Reflection About the x-axis

**1. State the goal:**
> We are asked to find the transformation matrix that reflects a point across the x-axis.

**2. Describe what reflection across the x-axis does:**
> A reflection across the x-axis keeps the x-coordinate the same but negates the y-coordinate.  
> That is, a point \((x, y)\) becomes \((x, -y)\).

**3. Write the general transformation matrix:**
> In 2D transformations, we use a matrix to apply changes to coordinates.  
> The reflection matrix across the x-axis is:
\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\]

**4. Optional — show how it works on a sample point (e.g., (3, 5)):**
> Applying the matrix to point \((3, 5)\):
\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\cdot
\begin{bmatrix}
3 \\
5
\end{bmatrix}
=
\begin{bmatrix}
3 \\
-5
\end{bmatrix}
\]
> This confirms the reflection flips the y-value.

**5. Final statement:**
> Therefore, the transformation matrix for reflection about the x-axis is:
\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\]

---

Would you like help formatting this into a neat LaTeX-style write-up or typing it into your revision notes or IDE project? I can also help you build a cheat sheet for all transformation matrices.  

## Me
Yh so what would be the matrix and calculation to apply it to a point?  

## Co-Pilot
Perfect — let’s walk through both the **matrix** and the **calculation** to apply a reflection about the x-axis to a point.

---

## 🔁 Reflection About the x-axis

### ✅ 1. Transformation Matrix
The reflection matrix across the x-axis is:

\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\]

This matrix keeps the x-coordinate the same and flips the sign of the y-coordinate.

---

### 🧮 2. Applying It to a Point

Let’s say we have a point \( P = (x, y) \). To apply the transformation:

\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\cdot
\begin{bmatrix}
x \\
y
\end{bmatrix}
=
\begin{bmatrix}
x \\
-y
\end{bmatrix}
\]

#### 📌 Example: Reflect point (3, 5)

\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\cdot
\begin{bmatrix}
3 \\
5
\end{bmatrix}
=
\begin{bmatrix}
3 \\
-5
\end{bmatrix}
\]

So the reflected point is **(3, -5)**.

---

### ✍️ How to Write This in Your Exam

> The reflection matrix across the x-axis is:
> \[
> \begin{bmatrix}
> 1 & 0 \\
> 0 & -1
> \end{bmatrix}
> \]
> Applying this to a point \( (x, y) \), we get:
> \[
> \begin{bmatrix}
> x \\
> -y
> \end{bmatrix}
> \]
> For example, reflecting (3, 5) gives (3, -5).

---

Want to try applying it to a few points or build a mini Python function to test it interactively?  

## Me
You didn't give the matrix, I was thinking (1,-1,1) but is that right?  

## Co-Pilot
Ah, I see what you're getting at now — you're trying to express the **reflection matrix** as a compact form like `(1, -1, 1)`. That’s a good instinct, but let’s clarify what that means and why it’s not quite right.

---

## ✅ The Correct Reflection Matrix (About the x-axis)

In **2D transformation matrix form**, a reflection about the x-axis is:

\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\]

This matrix:
- Leaves the **x-coordinate** unchanged
- Multiplies the **y-coordinate** by -1

---

## 🧠 Why `(1, -1, 1)` Isn’t a Matrix

The tuple `(1, -1, 1)` looks like a vector or a shorthand, but it doesn’t represent a 2×2 matrix. If you’re thinking in terms of a transformation matrix, it must be a **2×2** (or **3×3** if using homogeneous coordinates).

If you meant to write the matrix row-wise, it would be:

\[
\text{Matrix as flat list: } [1, 0, 0, -1]
\]

Which corresponds to:

\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\]

---

## 🧪 Applying It to a Point

Let’s apply it to a point \( (x, y) \). For example, \( (3, 5) \):

\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\cdot
\begin{bmatrix}
3 \\
5
\end{bmatrix}
=
\begin{bmatrix}
3 \\
-5
\end{bmatrix}
\]

So the reflected point is **(3, -5)**.

---

If you’re working in homogeneous coordinates (for combining with other transformations), the **3×3 version** would be:

\[
\begin{bmatrix}
1 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 1
\end{bmatrix}
\]

Let me know if you want to practice combining this with other transformations like rotation or translation — or if you want to code this up in Python or C#!  

## Me
So would [1,0,0,-1] work and what's the formula to apply it to the point?  

## Co-Pilot
Yes — you're on the right track! The flat list `[1, 0, 0, -1]` **does** represent the reflection matrix across the x-axis if you're writing it in row-major order for a 2×2 matrix. Here's how it works and how to apply it to a point:

---

## ✅ Matrix Format

The matrix:
\[
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\]

Can be written as a flat array:  
**`[1, 0, 0, -1]`**  
This is useful in code (e.g., Python, C#, OpenGL) where you store matrices as 1D arrays.

---

## 🧮 Applying It to a Point

Let’s say you have a point \( P = (x, y) \). To apply the transformation:

### **Matrix multiplication formula**:
\[
x' = 1 \cdot x + 0 \cdot y = x \\
y' = 0 \cdot x + (-1) \cdot y = -y
\]

So the transformed point is:
\[
(x', y') = (x, -y)
\]

---

### 📌 Example: Reflect point (3, 5)

Using `[1, 0, 0, -1]`:

- \( x' = 1 \cdot 3 + 0 \cdot 5 = 3 \)
- \( y' = 0 \cdot 3 + (-1) \cdot 5 = -5 \)

**Result**: \( (3, -5) \)

---

### 🧑‍💻 In Code (e.g., Python-style pseudocode)

```python
matrix = [1, 0, 0, -1]
x, y = 3, 5

x_prime = matrix[0]*x + matrix[1]*y
y_prime = matrix[2]*x + matrix[3]*y

print(x_prime, y_prime)  # Output: 3, -5
```

---

Let me know if you want to build a reusable function for this — or if you're working in C# or Unity, I can show you how to plug this into a transformation pipeline.  

*End of this Conversation*
