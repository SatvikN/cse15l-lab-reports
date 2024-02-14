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

**The Symptom**<br/><br/>
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

***-i Case sensitive***<br/>
working directory: `./docsearch/technical/biomed`
```
$ grep "DNA" *.txt > grep-output.txt
$ wc grep-output.txt
    5993   56210  487525 grep-output.txt
```
* The command searches for the pattern "DNA" in all files with the `.txt` extension within the current working directory. It then stores the output in the file `grep-output.txt`.
* This is useful because we can find out how many times "DNA" occurs in all the text files in the `biomed` directoy. Based on the output we know that "DNA" was found 5993 times in the directory.
  
working directory: `./docsearch/technical`
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
* The command searches for the pattern "policy" in all files within the media directory.
* This is useful because it shows us all the 14 times "policy" was in files directly within the `./government/media/` directory. However, it will not search within subdirectories of './government/media/'.


***-w Whole words***
working directory: `./docsearch/technical/biomed`
```
$ grep -w "DNA" *.txt > grep-output.txt
$ wc grep-output.txt
    3723   35275  300548 grep-output.txt
```
* The command searches for the exact word "DNA" in all files with the `.txt` extension within the current working directory. It then stores the output in the file `grep-output.txt`.
* This is useful because we can find out how many times the word "DNA" occurs not including when it is a substring of another word. Based on the output we know that "DNA" was found 3723 times in the `biomed` directory.

working directory: `./docsearch/technical`
```
$ grep -w "policy" ./government/media/*  
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
* The command searches for the exact word "policy" in all files within the `media` directory.
* This is useful because it shows us all the 11 times "policy" was in files directly within the directory without being a substring of another word.

***-c Word count***

working directory: `./docsearch/technical`
```
$ grep -c "carbon" ./government/Env_Prot_Agen/*
./government/Env_Prot_Agen/1-3_meth_901.txt:0
./government/Env_Prot_Agen/atx1-6.txt:4
./government/Env_Prot_Agen/bill.txt:4
./government/Env_Prot_Agen/ctf1-6.txt:4
./government/Env_Prot_Agen/ctf7-10.txt:4
./government/Env_Prot_Agen/ctm4-10.txt:7
./government/Env_Prot_Agen/final.txt:3
./government/Env_Prot_Agen/jeffordslieberm.txt:19
./government/Env_Prot_Agen/multi102902.txt:19
./government/Env_Prot_Agen/nov1.txt:1
./government/Env_Prot_Agen/ro_clear_skies_book.txt:1
./government/Env_Prot_Agen/section-by-section_summary.txt:2
./government/Env_Prot_Agen/tech_adden.txt:1
./government/Env_Prot_Agen/tech_sectiong.txt:1
```
* The command counts the number of matching lines for the pattern "carbon" in all files within the `./government/Env_Prot_Agen/` directory. However, if "carbon" appears twice on a single line it only counts as 1 match.
* This is useful because we can find out how many lines contain the word "DNA" within a directory. This displays the information in a simpler way rather then printing out every instance the word is found. Using this we can easliy find how prevalent a word is within a directory and which files have the most occurrences of the word.

working directory: `./docsearch/technical/911report`
```
$ grep -c "international" *.txt
chapter-1.txt:0
chapter-10.txt:4
chapter-11.txt:3
chapter-12.txt:26
chapter-13.1.txt:3
chapter-13.2.txt:2
chapter-13.3.txt:3
chapter-13.4.txt:1
chapter-13.5.txt:8
chapter-2.txt:3
chapter-3.txt:8
chapter-5.txt:4
chapter-6.txt:3
chapter-7.txt:5
chapter-8.txt:2
chapter-9.txt:0
preface.txt:0
```
* The command counts the number of matching lines for the pattern "international" in all files within the current working directory. However, if "international" appears twice on a single line it only counts as 1 match.
* This is useful because we can find out how many lines contain the word "international" within a directory. This tells us how prevalent a word is within a each file in a directory.
