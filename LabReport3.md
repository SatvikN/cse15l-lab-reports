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

**The Symptom**<br/>
<img width="895" alt="Screenshot 2024-02-13 at 12 20 01 PM" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/751f2508-5bd3-4b29-8d7d-4fa6679c79bb">


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

Explanation<br/>
The method was only properly copying values for half the array. This is because the method is iterating through the entire array so for the first half it copies the elemnts from the end to the front, however for the second half the method is copying the new elements from the front rather than the original elements. The proper implementation would be to swap the values on the 2 ends of the array and only iterate through half of the list.

## Part 2 - Researching Commands
**Command: grep**

*-i Case sensitive*
*
working directory: ./docsearch/technical/biomed
```
$ grep "DNA" *.txt > grep-output.txt
$ wc grep-output.txt
    5993   56210  487525 grep-output.txt
```
* The command searchs for the pattern "DNA" in all files with the .txt extension within the current working directory. It then stores the output in the file grep-output.txt
* This is useful because we can find out how many times "DNA" occurs in all the text files in the biomed directoy. Based on the output we know that "DNA" was found 5993 times in the directory.
  
working directory: ./docsearch/technical
```
$ grep "policy" ./government/media/*
./government/media/Anthem_Payout.txt:Anthem Inc., issued to policyholders as part of the insurer's
./government/media/Anthem_Payout.txt:that, to 1 million eligible policyholders in four states. About
./government/media/Anthem_Payout.txt:from a mutual company, owned by its policyholders, to a publicly
./government/media/Anthem_Payout.txt:eligibility policy for Kentucky Department for Medicaid Services.
./government/media/Anthem_Payout.txt:premiums in advance on Medicare supplement health-insurance policy
./government/media/Coup_Reshapes_Legal_Aid.txt:policy wonk in Iwasaki's outfit, agreed.
./government/media/Coup_Reshapes_Legal_Aid.txt:Dudovitz's desire to spend money influencing social policy and
./government/media/Coup_Reshapes_Legal_Aid.txt:care, policy advocacy, homelessness, domestic-violence assistance,
./government/media/Domestic_Violence_Ruling.txt:director of family violence law and policy for the National Council
./government/media/Farm_workers.txt:policy requires that incidents of pesticide exposure be reported
./government/media/NJ_Legal_Services.txt:On the policy side, Atlas and Thorne contend that the combined
./government/media/Survey.txt:the nation in its regulation, policy development and oversight
./government/media/pro_bono_efforts.txt:helped create the firm's policy. "In fact, you're going to be
./government/media/pro_bono_efforts.txt:policy narrows the definition to providing legal advice or
```


*-w Whole words*

*-r Recursive search*
