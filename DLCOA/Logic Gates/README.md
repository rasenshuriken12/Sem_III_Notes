# Logic Gates & Binary Arithmetic Basics

## **1. Binary Number System**

### **Binary Digits (Bits):**
- Only 2 digits: **0** and **1**
- Each position represents a power of 2
- MSB = Most Significant Bit (leftmost)
- LSB = Least Significant Bit (rightmost)

### **Decimal ↔ Binary Conversion:**
```
Decimal: 0  1  2  3   4   5   6   7   8
Binary:  0  1  10 11 100 101 110 111 1000
```

**Conversion Table (4-bit):**
```
Decimal  Binary
0        0000
1        0001
2        0010
3        0011
4        0100
5        0101
6        0110
7        0111
8        1000
9        1001
10       1010
11       1011
12       1100
13       1101
14       1110
15       1111
```

---

## **2. Logic Gates - The Building Blocks**

### **Basic Gates:**

#### **1. NOT Gate (Inverter)**
- **Symbol:** Triangle with circle
- **Function:** Outputs opposite of input
- **Truth Table:**
  ```
  A | NOT A
  0 | 1
  1 | 0
  ```
- **Boolean Expression:** `Y = NOT A` or `Y = A'` or `Y = Ā`

#### **2. AND Gate**
- **Symbol:** D-shaped
- **Function:** Outputs 1 only if ALL inputs are 1
- **Truth Table (2-input):**
  ```
  A B | A AND B
  0 0 | 0
  0 1 | 0
  1 0 | 0
  1 1 | 1
  ```
- **Boolean Expression:** `Y = A AND B` or `Y = A·B`

#### **3. OR Gate**
- **Symbol:** Curved shape
- **Function:** Outputs 1 if ANY input is 1
- **Truth Table (2-input):**
  ```
  A B | A OR B
  0 0 | 0
  0 1 | 1
  1 0 | 1
  1 1 | 1
  ```
- **Boolean Expression:** `Y = A OR B` or `Y = A+B`

#### **4. XOR Gate (Exclusive OR)**
- **Symbol:** OR gate with curved line
- **Function:** Outputs 1 if inputs are DIFFERENT
- **Truth Table:**
  ```
  A B | A XOR B
  0 0 | 0
  0 1 | 1
  1 0 | 1
  1 1 | 0
  ```
- **Boolean Expression:** `Y = A XOR B` or `Y = A⊕B`

#### **5. NAND Gate (NOT AND)**
- **Function:** Opposite of AND
- **Truth Table:**
  ```
  A B | A NAND B
  0 0 | 1
  0 1 | 1
  1 0 | 1
  1 1 | 0
  ```

#### **6. NOR Gate (NOT OR)**
- **Function:** Opposite of OR
- **Truth Table:**
  ```
  A B | A NOR B
  0 0 | 1
  0 1 | 0
  1 0 | 0
  1 1 | 0
  ```

---

## **3. Binary Addition**

### **Half Adder:**
Adds two single bits and produces **Sum** and **Carry**.

**Logic:**
- Sum = A XOR B
- Carry = A AND B

**Truth Table:**
```
A B | Sum Carry
0 0 | 0    0
0 1 | 1    0
1 0 | 1    0
1 1 | 0    1
```

**Circuit:** XOR gate gives Sum, AND gate gives Carry

### **Full Adder:**
Adds three bits (A, B, and Carry-in) and produces Sum and Carry-out.

**Logic:**
- Sum = A XOR B XOR Cin
- Carry-out = (A AND B) OR (Cin AND (A XOR B))

**Truth Table:**
```
A B Cin | Sum Cout
0 0 0   | 0   0
0 0 1   | 1   0
0 1 0   | 1   0
0 1 1   | 0   1
1 0 0   | 1   0
1 0 1   | 0   1
1 1 0   | 0   1
1 1 1   | 1   1
```

---

## **4. Binary Subtraction**

### **Using 2's Complement Method:**
1. Find 2's complement of subtrahend
2. Add to minuend
3. Ignore any overflow carry

### **Half Subtractor:**
Subtracts B from A, produces **Difference** and **Borrow**.

**Logic:**
- Difference = A XOR B
- Borrow = (NOT A) AND B

**Truth Table:**
```
A B | Diff Borrow
0 0 | 0     0
0 1 | 1     1
1 0 | 1     0
1 1 | 0     0
```

### **Full Subtractor:**
Subtracts B from A with Borrow-in.

**Truth Table:**
```
A B Bin | Diff Bout
0 0 0   | 0    0
0 0 1   | 1    1
0 1 0   | 1    1
0 1 1   | 0    1
1 0 0   | 1    0
1 0 1   | 0    0
1 1 0   | 0    0
1 1 1   | 1    1
```

---

## **5. Complements**

### **1's Complement:**
Simply flip all bits (0→1, 1→0)

**Example:**
```
Number:   1010 1101
1's comp: 0101 0010
```

### **2's Complement:**
1. Take 1's complement
2. Add 1 to LSB

**Example (8-bit):**
```
Original:     0000 1101 (13 decimal)
1's comp:     1111 0010
Add 1:       +0000 0001
2's comp:     1111 0011 (-13 decimal)
```

**Quick Method:** From right, copy bits until first 1, then flip all remaining bits
```
Original:     0011 0100
2's comp:     1100 1100
              ↑    ↑
              flip copy from first 1
```

---

## **6. Practical Examples**

### **Example 1: 4-bit Binary Addition**
```
   0110  (6 decimal)
 + 0101  (5 decimal)
 --------
   1011  (11 decimal)
   
Step-by-step:
   LSB: 0+1 = 1, carry 0
   2nd: 1+0 = 1, carry 0
   3rd: 1+1 = 0, carry 1
   MSB: 0+0+carry1 = 1
```

### **Example 2: 4-bit Binary Subtraction (using 2's complement)**
```
   0110  (6)
 - 0011  (3)
 --------
   
Step 1: Find 2's complement of 0011:
        0011 → 1100 (1's comp) → 1101 (2's comp)
        
Step 2: Add:
   0110  (6)
 + 1101  (-3 in 2's comp)
 --------
  10011  (Discard overflow → 0011 = 3)
```

---

## **7. Boolean Algebra Laws**

### **Basic Laws:**
```
1. Identity:
   A + 0 = A
   A · 1 = A

2. Null:
   A + 1 = 1
   A · 0 = 0

3. Idempotent:
   A + A = A
   A · A = A

4. Inverse:
   A + A' = 1
   A · A' = 0

5. Commutative:
   A + B = B + A
   A · B = B · A

6. Associative:
   (A+B)+C = A+(B+C)
   (A·B)·C = A·(B·C)

7. Distributive:
   A·(B+C) = A·B + A·C
   A+(B·C) = (A+B)·(A+C)

8. De Morgan's:
   (A+B)' = A'·B'
   (A·B)' = A' + B'
```

---

## **8. Universal Gates**

### **NAND Gate as Universal Gate:**
You can create ANY gate using only NAND gates!

```
NOT:   A NAND A = NOT A
AND:   (A NAND B) NAND (A NAND B) = A AND B
OR:    (A NAND A) NAND (B NAND B) = A OR B
```

### **NOR Gate as Universal Gate:**
```
NOT:   A NOR A = NOT A
OR:    (A NOR B) NOR (A NOR B) = A OR B
AND:   (A NOR A) NOR (B NOR B) = A AND B
```

---

## **9. Quick Reference Table**

| Operation | Boolean Expression | Logic Gates | Result When |
|-----------|-------------------|-------------|-------------|
| **AND** | A·B | ![AND] | Both inputs = 1 |
| **OR** | A+B | ![OR] | Any input = 1 |
| **NOT** | A' or Ā | ![NOT] | Opposite of input |
| **XOR** | A⊕B | ![XOR] | Inputs different |
| **NAND** | (A·B)' | ![NAND] | NOT (both = 1) |
| **NOR** | (A+B)' | ![NOR] | NOT (any = 1) |
| **XNOR** | (A⊕B)' | ![XNOR] | Inputs same |

Remember: All digital computers are built from these simple logic gates!
