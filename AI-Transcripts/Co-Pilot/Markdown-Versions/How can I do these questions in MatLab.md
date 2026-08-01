# How can I do these questions in MatLab  

## Me
How can I do these questions in matlab:  

### Task 2.1  
Plot the functions `x`, `x3`, `ex` and `ex2` over the interval `0 < x < 4`.  
### Task 2.2  
Make a good plot of the function `f (x) = sin(1/x)` for `0.01 < x < 0.1`. How did you create x so that the plot looked good?  
### Task 2.3  
Write a script to create a vector `x` with the elements, `xn = (−1)n+1/(2n − 1)`  
Add up the elements of the version of this vector that has **100 elements**.  

## Copilot
Sure, I can help you with that! Here are the steps and **MATLAB code** for each task:  

### Task 2.1  

To plot the functions `x`, `x^3`, `e^x`, and `e^{x^2}` over the interval `0 < x < 4`:  

```Matlab
x = linspace(0, 4, 100); % Create a vector of 100 points between 0 and 4
y1 = x;
y2 = x.^3;
y3 = exp(x);
y4 = exp(x.^2);

figure;
plot(x, y1, 'r', x, y2, 'g', x, y3, 'b', x, y4, 'k');
legend('x', 'x^3', 'e^x', 'e^{x^2}');
xlabel('x');
ylabel('y');
title('Plot of functions x, x^3, e^x, and e^{x^2}');
grid on;
```

### Task 2.2  

To make a good plot of the function `f(x)=sin⁡(1/x)` for `0.01 < x < 0.1`:  

```Matlab
x = linspace(0.01, 0.1, 1000); % Create a vector of 1000 points between 0.01 and 0.1
y = sin(1 ./ x);

figure;
plot(x, y);
xlabel('x');
ylabel('f(x) = sin(1/x)');
title('Plot of f(x) = sin(1/x) for 0.01 < x < 0.1');
grid on;
```  

To make the plot *look good*, I used a **high number of points (1000)** to ensure smoothness.  

### Task 2.3  

To create a vector `x` with the elements `xn={(-1)^{n+1}}/{2n - 1}` and **sum the first 100 elements**:  

```Matlab
n = 1:100; % Create a vector of integers from 1 to 100
x = (-1).^(n+1) ./ (2*n - 1); % Calculate the elements of the vector

sum_x = sum(x); % Sum the elements of the vector
disp(sum_x); % Display the sum
```  

Feel free to ask if you have any questions or need further assistance!  

*End of this conversation*  
