# Selection Sort with New Data Values  

## Me
How could I do this question but with different data values e.g. 90, 41, 27, 19, 88, 64, 15, 36, 49, 58, 13 [Uploaded Image Expired]  

## Co-Pilot
Got it! Let's tackle the question with the new data values: 90, 41, 27, 19, 88, 64, 15, 36, 49, 58, 13. 

### Selection Sort Using a Priority Queue (Unsorted Array)

**Input Phase:**
Insert each key into the priority queue and record the state of the queue after each insertion.

| Input | Priority Queue             | Output |
|-------|----------------------------|--------|
| 90    | 90                         |        |
| 41    | 90, 41                     |        |
| 27    | 90, 41, 27                 |        |
| 19    | 90, 41, 27, 19             |        |
| 88    | 90, 41, 27, 19, 88         |        |
| 64    | 90, 41, 27, 19, 88, 64     |        |
| 15    | 90, 41, 27, 19, 88, 64, 15 |        |
| 36    | 90, 41, 27, 19, 88, 64, 15, 36 |    |
| 49    | 90, 41, 27, 19, 88, 64, 15, 36, 49 | |
| 58    | 90, 41, 27, 19, 88, 64, 15, 36, 49, 58 | |
| 13    | 90, 41, 27, 19, 88, 64, 15, 36, 49, 58, 13 | |

**Output Phase:**
Extract the minimum key from the priority queue, record the output, and update the state of the queue after each extraction.

| Input | Priority Queue                         | Output               |
|-------|----------------------------------------|----------------------|
|       | 90, 41, 27, 19, 88, 64, 15, 36, 49, 58 | 13                   |
|       | 90, 41, 27, 19, 88, 64, 36, 49, 58     | 13, 15               |
|       | 90, 41, 27, 88, 64, 36, 49, 58         | 13, 15, 19           |
|       | 90, 41, 88, 64, 36, 49, 58             | 13, 15, 19, 27       |
|       | 90, 88, 64, 36, 49, 58                 | 13, 15, 19, 27, 36   |
|       | 90, 88, 64, 49, 58                     | 13, 15, 19, 27, 36, 41 |
|       | 90, 88, 64, 58                         | 13, 15, 19, 27, 36, 41, 49 |
|       | 90, 88, 64                             | 13, 15, 19, 27, 36, 41, 49, 58 |
|       | 90, 88                                 | 13, 15, 19, 27, 36, 41, 49, 58, 64 |
|       | 90                                     | 13, 15, 19, 27, 36, 41, 49, 58, 64, 88 |
|       |                                        | 13, 15, 19, 27, 36, 41, 49, 58, 64, 88, 90 |

And there you have it! By following this method, you can sort any sequence of data values using selection sort and a priority queue implemented as an unsorted array. Let me know if you need more help or if there's something else you'd like to explore!  

## Me
Extend the table of Exercise 1 by two additional columns: 
(a) the number of keys that have to be examined in order to select which to output  
(b) the number of objects in the queue that have to be “shuffled up” when the selected object is output.  
At the end of the table, enter the totals of each of those two columns.  
What is the relation between the column total of number of examinations and the number of items in the input sequence?  

## Co-Pilot
Sure thing! Let's extend the table with the additional columns.

### Selection Sort Using a Priority Queue (Unsorted Array)

**Input Phase:**
Insert each key into the priority queue and record the state of the queue after each insertion.

**Output Phase:**
Extract the minimum key from the priority queue, record the output, and update the state of the queue after each extraction.

**Extended Table:**

| Input | Priority Queue                         | Output               | Examinations | Shuffle-Ups |
|-------|----------------------------------------|----------------------|--------------|-------------|
|       | 90, 41, 27, 19, 88, 64, 15, 36, 49, 58 | 13                   | 11           | 0           |
|       | 90, 41, 27, 19, 88, 64, 36, 49, 58     | 13, 15               | 10           | 1           |
|       | 90, 41, 27, 88, 64, 36, 49, 58         | 13, 15, 19           | 9            | 2           |
|       | 90, 41, 88, 64, 36, 49, 58             | 13, 15, 19, 27       | 8            | 3           |
|       | 90, 88, 64, 36, 49, 58                 | 13, 15, 19, 27, 36   | 7            | 4           |
|       | 90, 88, 64, 49, 58                     | 13, 15, 19, 27, 36, 41 | 6          | 5           |
|       | 90, 88, 64, 58                         | 13, 15, 19, 27, 36, 41, 49 | 5      | 6           |
|       | 90, 88, 64                             | 13, 15, 19, 27, 36, 41, 49, 58 | 4  | 7           |
|       | 90, 88                                 | 13, 15, 19, 27, 36, 41, 49, 58, 64 | 3 | 8          |
|       | 90                                     | 13, 15, 19, 27, 36, 41, 49, 58, 64, 88 | 2 | 9       |
|       |                                        | 13, 15, 19, 27, 36, 41, 49, 58, 64, 88, 90 | 1 | 10  |
| **Total** |                                    |                      | **66**       | **55**      |

### Relation Between Examinations and Number of Items

The total number of examinations is the sum of the numbers of keys examined each time an output is selected. For an array of \( n \) items, it requires examining:
\[ n, (n-1), (n-2), ..., 1 \]
Thus, the total number of examinations \( E \) for an array of \( n \) items is:
\[ E = n + (n-1) + (n-2) + ... + 1 = \frac{n(n+1)}{2} \]

So, in this case, with 11 items, the total examinations \( E \) is:
\[ E = \frac{11(11+1)}{2} = \frac{11 \times 12}{2} = 66 \]

This matches our table's total, confirming that the number of examinations is proportional to the sum of the first \( n \) natural numbers, which is quadratic in nature, specifically \( O(n^2) \).

### Additional Explanation

- **Examinations:** Represents the number of items checked to find the minimum.
- **Shuffle-Ups:** Represents the number of items that need to be repositioned after removing the minimum.

Let me know if you need anything else!  

*End of this Conversation*
