# Lab Report 3

## Part 1 - Bugs
**Failure-inducing input**
```
@Test 
public void testReverseInPlaceThree(){
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
}
```

**Input that doesn't induce a failure**
```
@Test 
public void testReverseInPlace(){
    int[] input1 = {3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3}, input1);
}
```

**The Symptom**
<img width="906" alt="pic1" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/4af9347a-caee-4c28-81c6-5d49e65e2e21">



**The bug**<br/>
Before
```
static void reverseInPlace(int[] arr){
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}
```

After
```
static void reverseInPlace(int[] arr){
    for(int i = 0; i < arr.length / 2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
}
```

## Part 2 - Researching Commands
