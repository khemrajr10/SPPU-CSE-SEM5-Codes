def accept_array(A): 
   n = int(input("Enter the total no. of student : "))
   for i in range(n):
      x = float(input("Enter the  first year percentage of student %d : "%(i+1)))
      A.append(x)
   print("Array accepted successfully\n\n");

def display_array(A): 
   n = len(A)
   if(n == 0) :
      print("\nNo records in the database")
   else :
      print("Array of FE Marks : ",end=' ')
      for i in range(n) :
         print("%.2f  "%A[i],end=' ')
      print("\n");


def Selection_sort(A) :
   n = len(A)
   for pos in range(n-1):
      min_ind = pos
      for i in range(pos + 1, n) :
         if(A[i] < A[min_ind]) :
            min_ind = i
      temp = A[pos]
      A[pos] = A[min_ind]
      A[min_ind] = temp

def Bubble_sort(A) :
   n = len(A)
   for Pass in range(1,n) :
      for i in range(n-Pass) :
         if(A[i] < A[i+1]) :
            temp = A[i]
            A[i] = A[i+1]
            A[i+1] = temp
      
def Main() :   
   A = []
   while True :
      print ("\t1 : Accept & Display the FE Marks")
      print ("\t2 : Selection Sort Ascending order")
      print ("\t3 : Bubble sort Descending order and display top five scores")
      print ("\t4 : Exit")
      ch = int(input("Enter your choice : "))
      if (ch == 4):
         print ("End of Program")
         quit()
      elif (ch==1):
         accept_array(A)
         display_array(A)
      elif (ch==2):
         print("Marks before sorting")
         display_array(A)
         Selection_sort(A)
         print("Marks after sorting")
         display_array(A)
      elif (ch==3):
         print("Marks before sorting")
         display_array(A)
         Bubble_sort(A)
         print("Marks after sorting")
         display_array(A)
         if(len(A) >= 5) :
            print("Top Five Scores : ")
            for i in range(5) :
               print("\t%.2f"%A[i])
         else :
            print("Top Scorers : ")
            for i in range(len(A)) :
               print("\t%.2f"%A[i])                  
      else :
           print ("Wrong choice entered !! Try again")


Main()










---

# 1. Selection Sort

*(Important 4M / 6M question)*

In Data Structures and Algorithms, Selection Sort is a simple comparison-based sorting technique.

---

## 📌 Definition

Selection Sort is a sorting algorithm in which:

* the **minimum element is repeatedly selected**
* and placed at its correct position in the sorted part of array.

---

## ⚙️ Working Principle

```text id="ss1"
Find minimum element
      ↓
Swap with first unsorted position
      ↓
Move boundary of sorted part
      ↓
Repeat
```

---

## 🔄 Example

Array:

```text id="ss2"
[64, 25, 12, 22, 11]
```

### Pass 1:

Minimum = 11 → swap with 64

```text id="ss3"
[11, 25, 12, 22, 64]
```

### Pass 2:

Minimum = 12

```text id="ss4"
[11, 12, 25, 22, 64]
```

### Pass 3:

Minimum = 22

```text id="ss5"
[11, 12, 22, 25, 64]
```

---

## ⏱ Time Complexity

O(n^2)

---

## 🧠 Space Complexity

O(1)

---

## 👍 Advantages

* Simple logic
* Less swapping compared to Bubble Sort
* No extra memory required

---

## 👎 Disadvantages

* Very slow for large data
* Always O(n²)

---

# 2. Bubble Sort

*(Very important viva question)*

---

## 📌 Definition

Bubble Sort is a sorting algorithm in which:

* adjacent elements are compared
* swapped if they are in wrong order
* largest element “bubbles” to end after each pass

---

## ⚙️ Working Principle

```text id="bs1"
Compare adjacent elements
        ↓
Swap if required
        ↓
Repeat passes
        ↓
Largest element settles at end
```

---

## 🔄 Example

Array:

```text id="bs2"
[5, 1, 4, 2]
```

### Pass 1:

```text id="bs3"
[1, 4, 2, 5]
```

### Pass 2:

```text id="bs4"
[1, 2, 4, 5]
```

---

## ⏱ Time Complexity

Worst / Average:
O(n^2)

Best case (already sorted):
O(n)

---

## 🧠 Space Complexity

O(1)

---

## 👍 Advantages

* Very easy to understand
* Stable sorting algorithm
* Good for small datasets

---

## 👎 Disadvantages

* Very slow
* Too many swaps
* Not suitable for large data

---

# 3. Quick Sort

*(Most important algorithm for exams)*

---

## 📌 Definition

Quick Sort is a divide and conquer algorithm in which:

* a **pivot element** is selected
* array is partitioned into two parts:

  * elements smaller than pivot
  * elements greater than pivot
* recursively sorted

---

## ⚙️ Working Principle

```text id="qs1"
Choose Pivot
     ↓
Partition Array
     ↓
Left < Pivot < Right
     ↓
Recursively sort subarrays
```

---

## 🔄 Example

Array:

```text id="qs2"
[50, 30, 70, 10, 90]
```

### Step 1: Pivot = 50

Partition:

```text id="qs3"
[30, 10, 50, 70, 90]
```

### Step 2: Sort left part:

```text id="qs4"
[10, 30]
```

### Step 3: Right part already sorted:

```text id="qs5"
[70, 90]
```

---

## ⏱ Time Complexity

Best / Average:
O(n\log n)

Worst case:
O(n^2)

---

## 🧠 Space Complexity

O(\log n)

---

## 👍 Advantages

* Very fast in practice
* Efficient for large datasets
* In-place sorting

---

## 👎 Disadvantages

* Worst case is O(n²)
* Depends on pivot selection
* Recursive overhead

---

# 📊 Final Comparison Table

| Algorithm      | Time Complexity | Space    | Efficiency |
| -------------- | --------------- | -------- | ---------- |
| Quick Sort     | O(n log n)      | O(log n) | Best       |
| Selection Sort | O(n²)           | O(1)     | Slow       |
| Bubble Sort    | O(n²)           | O(1)     | Slowest    |

---

# 🎯 Final Viva Answer

> Selection Sort selects minimum element, Bubble Sort compares adjacent elements repeatedly, and Quick Sort uses divide and conquer with pivot partitioning for efficient sorting.

---

If you want next, I can give:
✔ 10 viva questions from these 3 algorithms
✔ difference table (very important 4M answer)
✔ or handwritten-style short notes for revision

