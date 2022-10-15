# Lab Report 2

## 1.Search Engine

## 2.Bugs

### (1) Bug in reverseInPlace method 
- The failure-inducing input is "2,3,4"
```
public void testReverseInPlace() {
    int[] input1 = { 2,3,4 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 4,3,2 }, input1);
}
```