---
title: Number Systems and Data Representation
draft: false
tags:
  - ICOA
description: Introduction to Computer Architecture
---
# Number Bases

| Base        | Range         | Description                                                |
| ----------- | ------------- | ---------------------------------------------------------- |
| Decimal     | 0 - 9         | Numbers we see day to day                                  |
| Binary      | 0, 1          | It is the language of the computers                        |
| Octal       | 0 - 7         | Represented by 3 binary bits                               |
| Hexadecimal | 0 - 9 and A-F | Represented by 4 binary bits<br>2 hexadecimals is one byte |
# Conversion of Number Bases
Converting *Base 10* numbers to any other *bases* is done via division while the opposite is done via multiplication. However, the conversion of any bases to any other bases can be done by converting to binary or decimal first. 

*Example: Hexadecimal (with floating point) to binary*
$$
\begin{align}
& 1F.C_{16} \\
& 1(16^1) + 15(16^0) + 12(16^{-2}) \\
& = 31.75_{10} & \text{Convert to decimal}
\end{align}
$$
$$
\begin{align}
 31.75_{10} \\ 
 31/2 & = 15 \text{ remainder } 1 \\
 15/2 & = 7  \text{ remainder } 1 \\
 7/2  & = 3  \text{ remainder } 1 \\
 3/2  & = 1  \text{ remainder } 1 \\ 
 1/2  & = 0  \text{ remainder } 1 \\
      & =11111_2 & \text{Convert whole number to binary}
\end{align}
$$
$$
\begin{align}
0.75_{10} \\
0.75 \times 2 &= 1.5 & 1 \\
0.5 \times 2 &= 1.0 & 1 \\
0.0 \times 2 &= 0 & 
\end{align}
$$
Final answer: $0001\; 1111.1100$

Keep in mind that 1 hexadecimal digit is 4 binary digits. So, $0$ is added to fill the empty spots
$$
1|1111.11\text{<add zero here>}
$$


*Example: The shorter way*
$$
\begin{align}
& 1F.C_{16} \\
& = 0001 \; 1111.1100_{2}
\end{align}
$$
# Gray Code and Binary Coded Decimals
## Binary Coded Decimals, BCD
>[!definition] Binary Coded Decimals
>A decimal number from 0 to 9 is represented with 4 binary digits

*Example*
$$
\begin{align}
129_{10} &= 0001 \; 0010 \; 1001_{BCD} \\
1000 \; 0110_{BCD} &= 86_{10} 
\end{align}
$$
## Gray Code
>[!DEFINITION] Gray Code
>A numerical code used in computing in which consecutive integers are represented by binary numbers differing in only one digit.

Gray codes are not weighted by anything.

*So, why does use it?*
1. Reduce the error rate during data transfer

### Conversion
*Example: Binary to Gray code*

$1010_{2} = 1111_{G}$

$0110_{2} = 0101_{G}$

$0011_{2} = 0010_{G}$

$1001_{2} = 1101_{G}$

*Example: Gray code to Binary*

*If same = 0, not same = 1*

$1010_{G} = 1100_{2}$

$0110_{G} = 0110_{2}$

$0011_{G} = 0010_{2}$

$1001_{G} = 1110_{2}$
# Negative Numbers & Arithmetic
## Negative Numbers
Negative numbers are represented by *Signed Magnitude* and *2's Complement*. 

>[!INFO] First digit
>The first digit is the signed bit; 0 is positive and 1 is negative. 
### Signed Magnitude
The rest of the bits are the **true magnitude**. This is true regardless if the values are positive or negative.
### 2's Complement
If the number is positive, the number is known as a **true binary.**

If the number is negative, the following has to be done to determine the value,
1. Invert the 2's complement
2. Add 1
3. Convert into decimal
4. Add a *-*
#### Overflow
2's complement uses complement arithmetic. This means that: 
$$
(A-B) \text{ is } A + (-B) = A + B_{2c}
$$

The issue with digital systems is the limited bits for data representation. The decimal range for an n-bit digital system using 2 complement is $(-2^{n-1}) \leq N \leq (2^{n-1} - 1)$.

>[!EXAMPLE] 8-bit digital system
>Operate on values between $-128 \text{ to } 127$

If the result of an arithmetic operation is out of the range, an overflow occurs. 

>[!NOTE] Things to keep in mind
>- Overflow can never occur for $A = B - C$
>- If two 2's complement numbers with the same sign are added, then overflow occurs if:
>	- Adding two positive numbers give a **negative** result.
>	- Adding two negative numbers give a **positive** result. 
## Arithmetic
### Addition
$$
\begin{align}
0 + 0 &= 0  && \text{Sum of 0 with a carry of 0} \\
0 + 1 &= 1  && \text{Sum of 1 with a carry of 0} \\
1 + 0 &= 1  && \text{Sum of 1 with a carry of 0} \\
1 + 1 &= 10 && \text{Sum of 0 with a carry of 1}
\end{align}
$$
$$
\begin{align*}
11001 \\
+\;\;1101\\
---- \\
100110
\end{align*}
$$
### Subtraction
$$
\begin{align}
&0 - 0 \quad= 0 \\
&0 - 1 \quad= 1 \\
&1 - 0 \quad= 1 \\
&10 - 1 \;\;= 1 && \text{0} - \text{1 with a borrow of 1}
\end{align}
$$

$$
\begin{align*}
101 \\
+\;\;011\\
--- \\
010
\end{align*}
$$
### Multiplication
$$
\begin{align}
0 \times 0 &= 0 \\
0 \times 1 &= 0 \\
1 \times 0 &= 0 \\
1 \times 1 &= 1 
\end{align}
$$
$3 \times 3 = 9$ is, 
$$
\begin{align*}
11 \\
+\;\;11\\
--- \\
11 \\
+\;11\;\;\\
--- \\
1001
\end{align*}
$$
