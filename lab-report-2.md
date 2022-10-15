# Lab Report 2

## 1.Search Engine

## 2.Bugs

### (1) Bug in reverseInPlace method 
- The failure-inducing input (the code of the test)  

```
public void testReverseInPlace() {
    int[] input1 = { 2,3,4 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 4,3,2 }, input1);
}
```    

The input is "2,3,4" and the expected output is "4,3,2".  

- The symptom (the failing test output)  
  
![Image](https://sara0112.github.io/cse15l-lab-reports/Lab2_Bug_01.png)  

The expected output is "4,3,2", but the output is "4,3,4".  

- The bug (the code fix needed)  
Original code: 
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```   

The bug is in the line
```
for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
}
```   
- Connection between the symptom and the bug.   
Since the the first element was changed to the last element before the last element use the first element to cover itself. This is the reason why the last element does not be changed to the original first element. For example, in the input array "2,3,4", the first element change to the last element and the array changed to "4,3,4". When the last element need to change to the first element, the first element is already changed to "4". So, the final result is "4,3,4".  

To solve this issue, we need to use a temporary place to store the original element before doing switch two elements each time. Also, the for loop do not need to go through all element in the array but go through the first to the middle element.  
Fixed code:  

```
static void reverseInPlace(int[] arr) {
  int n = arr.length;
  for(int i = 0; i < n/2; i += 1) {
    int temp = arr[i];
    arr[i] = arr[n - i - 1];
    arr[n - i - 1] = temp;
  }
}
```    


### (2) Bug in merge method

- The failure-inducing input (the code of the test)  
```
	public void merge() {
    List<String> inputList1 = new ArrayList<String>();
    inputList1.add("1");
    inputList1.add("3");
    List<String> inputList2 = new ArrayList<String>();
    inputList2.add("2");
    inputList2.add("4");
    List<String> expcList = new ArrayList<String>();
    expcList.add("1");
    expcList.add("2");
    expcList.add("3");
    expcList.add("4");
    List<String> outputList = ListExamples.merge(inputList1,inputList2);
    assertEquals(outputList, expcList);
	}
```

The input is {"1","3"}  and {"2","4"} and the expected output is {"1","2","3","4"}.   

- The symptom (the failing test output)  
![Image](https://sara0112.github.io/cse15l-lab-reports/Lab2_Bug_02.png)  

The symptom is OutOfMemoryError. The test never stop.    

- The bug (the code fix needed)  
