By wikipedia

The two's complement of an N-bit number is defined as its complement with respect to 2N; the sum of a number and its two's complement is 2N. For instance, for the three-bit number 010, the two's complement is 110, because 010 + 110 = 1000.

From the ones' complement
To get the two's complement of a negative binary number, the bits are inverted, or "flipped", by using the bitwise NOT operation; the value of 1 is then added to the resulting value, ignoring the overflow which occurs when taking the two's complement of 0.

For example, using 1 byte (=8 bits), the decimal number 5 is represented by

0000 0101(2)
The most significant bit is 0, so the pattern represents a non-negative value. To convert to −5 in two's-complement notation, first, the bits are inverted, that is: 0 becomes 1 and 1 becomes 0:

1111 1010(2)
At this point, the representation is the ones' complement of the decimal value -5. To obtain the two's complement, 1 is added to the result, giving:

1111 1011(2)

[source](https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec)