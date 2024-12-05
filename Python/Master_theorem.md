
The given recurrence relation is:

```
T(n) = 4T(n/2) + O(n)
```

with the base case:
```
T(1) = 1
```

We solve this recurrence relation using the **Master Theorem**.

### Master Theorem
For a recurrence of the form:
```
T(n) = aT(n/b) + O(n^d)
```
1. (a) = Number of subproblems.
2. (b) = Factor by which the problem size reduces.
3. (d) = Exponent in the cost outside the recursive calls.

We compare (p = log_b(a)) with (d):
- If \(p < d\): \(T(n) in O(n^d)\)
- If \(p = d\): \(T(n) in O(n^d \log n)\)
- If \(p > d\): \(T(n) in O(n^p)\)

---

### Step 1: Identify Parameters
For the given recurrence:
- \(a = 4\)
- \(b = 2\)
- \(d = 1\) (from \(O(n)\))

### Step 2: Calculate (p = log_b(a))
```
p = log_2(4) = 2
```

### Step 3: Compare \(p\) and \(d\)
- \(p = 2 > d = 1\)

Thus, the complexity is determined by \(p\), and:
```
T(n) \in O(n^p) = O(n^2)
```

---

### Final Answer:
The time complexity of the algorithm is **\(O(n^2)\)**.



Now,    
The **Master Theorem** is a method used in **divide-and-conquer algorithms** to determine the **time complexity** of recurrence relations of the form:

```
T(n) = aT(n / b) + f(n)
```

Where:
- `T(n)` is the total running time.
- `a` is the number of subproblems.
- `n / b` is the size of each subproblem.
- `f(n)` is the cost of dividing the problem and combining the results.

---

### **Master Theorem Conditions**
The Master Theorem applies if:
1. `a >= 1`: At least one subproblem is generated.
2. `b > 1`: The input size decreases for each subproblem.
3. `f(n)` is asymptotically positive.

---

### **The Master Theorem Formula**
Let `p = log_b a` (where `b = base`, `a = number of divisions`).

1. Compare `f(n)` to `n^p` (growth rate of the "divide and combine" step):
   - If `f(n) ∈ O(n^p)`: `T(n) ∈ Θ(n^p log n)` *(logarithmic overhead)*.
   - If `f(n) ∈ Θ(n^p)`: `T(n) ∈ Θ(n^p)` *(balance between divide and combine steps)*.
   - If `f(n) ∈ Ω(n^p)`: `T(n) ∈ Θ(f(n))` *(combine dominates)* **if the regularity condition holds**.

---

### **Steps to Solve Using Master Theorem**
1. Identify the recurrence relation.
2. Write `a`, `b`, and `f(n)`.
3. Compute `p = log_b a`.
4. Compare `f(n)` with `n^p` using Big-O notation.
5. Apply the theorem to find the time complexity.

---

### **Examples**

#### **Example 1**
Solve the recurrence:
```
T(n) = 2T(n / 2) + n
```

1. Identify parameters:
   - `a = 2`, `b = 2`, `f(n) = n`.
2. Compute `p = log_b a = log_2 2 = 1`.
3. Compare `f(n)` with `n^p`:
   - `f(n) = n` matches `n^p` (both are `Θ(n)`).
4. Result:
   - Time complexity: `T(n) ∈ Θ(n^p log n) = Θ(n log n)`.

---

#### **Example 2**
Solve the recurrence:
```
T(n) = 4T(n / 2) + n^2
```

1. Identify parameters:
   - `a = 4`, `b = 2`, `f(n) = n^2`.
2. Compute `p = log_b a = log_2 4 = 2`.
3. Compare `f(n)` with `n^p`:
   - `f(n) = n^2`, which is equal to `n^p` (both are `Θ(n^2)`).
4. Result:
   - Time complexity: `T(n) ∈ Θ(n^p log n) = Θ(n^2 log n)`.

---

#### **Example 3**
Solve the recurrence:
```
T(n) = 3T(n / 4) + n^2
```

1. Identify parameters:
   - `a = 3`, `b = 4`, `f(n) = n^2`.
2. Compute `p = log_b a = log_4 3 ≈ 0.792`.
3. Compare `f(n)` with `n^p`:
   - `f(n) = n^2`, which grows faster than `n^p` (`n^2 ∈ Ω(n^0.792)`).
4. Result:
   - Time complexity: `T(n) ∈ Θ(f(n)) = Θ(n^2)`.

---

### **Key Points**
1. **Master Theorem is not universal**:
   - It does not apply to all recurrence relations (e.g., when `f(n)` is not polynomial).
2. **Growth comparison matters**:
   - Always compare `f(n)` to `n^p`.

By mastering this, you'll be able to solve most divide-and-conquer recurrence relations efficiently!

