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

**The symptom**<br/><br/>
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

**Explanation**<br/>
The method was only properly copying values for half the array. This is because the method is iterating through the entire array so for the first half it copies the elemnts from the end to the front, however for the second half the method is copying the new elements from the front rather than the original elements. The proper implementation would be to swap the values on the 2 ends of the array and only iterate through half of the list.

## Part 2 - Researching Commands
**Command: grep**

***`-i` Ignoring case***
* Source: <https://man7.org/linux/man-pages/man1/grep.1.html>

working directory: `./docsearch/technical/biomed`
```
$ grep -i "dna" *.txt > grep-output.txt
$ wc grep-output.txt
    6141   57570  499162 grep-output.txt
```
* The command searches for the pattern "dna" in all files with the `.txt` extension within the current working directory ignoring the case of the text. It then stores the output in the file `grep-output.txt`.
* This is useful because we can find out how many times "dna" occurs in all the text files in the `biomed` directoy. Based on the output we know that "dna" was found 6141 times in the directory.
  
working directory: `./docsearch/technical`
```
$ grep  -i "policy" ./government/media/*
./government/media/Anthem_Payout.txt:Poorest Policyholders could lose Medicaid, other Benefits
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
* The command searches for the pattern "policy" in all files within the `./government/media/` directory while ignoring the case of the text.
* This is useful because it shows us all the 15 times "policy" was in files directly within the `./government/media/` directory. However, it will not search within subdirectories of './government/media/'.


***`-w` Whole words***
* Source: <https://man7.org/linux/man-pages/man1/grep.1.html>

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
* The command searches for the exact word "policy" in all files within the `./government/media/` directory.
* This is useful because it shows us all the 11 times "policy" was in files directly within the directory without being a substring of another word.

***`-c` Word count***
* Source: <https://www.geeksforgeeks.org/grep-command-in-unixlinux/>

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
* This is useful because we can find out how many lines contain the word "carbon" within a directory. This displays the information in a simpler way rather then printing out every instance the word is found. Using this we can easliy find how prevalent a word is within a directory and which files have the most occurrences of the word.

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
* This is useful because we can find out how many lines contain the word "international" within a directory and how prevalent the word is in each file.

***`-n` Word count***
* Source: <https://www.geeksforgeeks.org/grep-command-in-unixlinux/>

working directory: `./docsearch/technical`
```
$ grep -n "carbon" ./government/Env_Prot_Agen/*
./government/Env_Prot_Agen/atx1-6.txt:1325:carbon filtration, laboratory water conditioning units, or the use
./government/Env_Prot_Agen/atx1-6.txt:1354:vapors can be removed using activated carbon filters (BALSTON®, C-1
./government/Env_Prot_Agen/atx1-6.txt:1368:carefully chosen. Tempered glass and perfluorocarbon plastics
./government/Env_Prot_Agen/atx1-6.txt:2031:carbon or undergravel filter to remove dissolved metabolites.
./government/Env_Prot_Agen/bill.txt:356:The term "gasify" means to convert carbon-containing
./government/Env_Prot_Agen/bill.txt:357:material into a gas consistingprimarily of carbon monoxide and
./government/Env_Prot_Agen/bill.txt:6566:combustion practices to minimizeemissions of carbon
./government/Env_Prot_Agen/bill.txt:7052:title IV of the Clean Air Act shall also monitor carbon dioxide
./government/Env_Prot_Agen/ctf1-6.txt:1437:by carbon filtration, or the use of sodium thiosulfate. Use of 3.6
./government/Env_Prot_Agen/ctf1-6.txt:1444:using activated carbon filters (BALSTON®, C-1 filter, or
./government/Env_Prot_Agen/ctf1-6.txt:1466:carefully chosen. Tempered glass and perfluorocarbon plastics
./government/Env_Prot_Agen/ctf1-6.txt:2011:carbon or undergravel filter to remove dissolved metabolites.
./government/Env_Prot_Agen/ctf7-10.txt:105:(1) ion exchange, (2) ion exchange, (3) carbon, and (4) organic
./government/Env_Prot_Agen/ctf7-10.txt:290:carbon filter. Tap water can be dechlorinated by deionization,
./government/Env_Prot_Agen/ctf7-10.txt:291:carbon filtration, or the use of sodium thiosulfate. Use of 3.6
./government/Env_Prot_Agen/ctf7-10.txt:303:through a deionizer and carbon filter to remove toxic metals and
./government/Env_Prot_Agen/ctm4-10.txt:757:activated carbon filters (BALSTON®, C-1 filter, or
./government/Env_Prot_Agen/ctm4-10.txt:779:carefully chosen. Tempered glass and perfluorocarbon plastics
./government/Env_Prot_Agen/ctm4-10.txt:1244:activated carbon or undergravel filter to remove dissolved
./government/Env_Prot_Agen/ctm4-10.txt:1475:(1) ion exchange, (2) ion exchange, (3) carbon, and (4) organic
./government/Env_Prot_Agen/ctm4-10.txt:1675:into portable containers (20-L CUBITAINERS® or polycarbonate water
./government/Env_Prot_Agen/ctm4-10.txt:1710:deionization, carbon filtration, or the use of sodium thiosulfate.
./government/Env_Prot_Agen/ctm4-10.txt:1722:carbon filter to remove toxic metals and organics, and to control
./government/Env_Prot_Agen/final.txt:156:six pollutants: ozone, carbon monoxide (CO); particulate matter
./government/Env_Prot_Agen/final.txt:278:mercury. (Power generation has other emissions, such as carbon
./government/Env_Prot_Agen/final.txt:535:forests there that sequester carbon. The complex challenge of
./government/Env_Prot_Agen/jeffordslieberm.txt:18:mercury (Hg), and carbon dioxide (CO2) emissions from the US
./government/Env_Prot_Agen/jeffordslieberm.txt:43:Reduce carbon dioxide (CO2) emissions to 1990
./government/Env_Prot_Agen/jeffordslieberm.txt:188:sulfur dioxide (SO2), and carbon dioxide (CO2). Although a
./government/Env_Prot_Agen/jeffordslieberm.txt:196:air pollutants and carbon dioxide (CO2) emissions. The study,
./government/Env_Prot_Agen/jeffordslieberm.txt:303:emissions, and 475 million metric tons (MtC) of carbon
./government/Env_Prot_Agen/jeffordslieberm.txt:442:to accelerate the development and deployment of low-carbon, energy
./government/Env_Prot_Agen/jeffordslieberm.txt:557:a $50 carbon charge applied in the CEF Advanced Scenario), drove a
./government/Env_Prot_Agen/jeffordslieberm.txt:601:technologies reduces both carbon and NOx emissions by 10.7 and 8.1
./government/Env_Prot_Agen/jeffordslieberm.txt:757:required to actually hit the target in 2007. In 2015, carbon and
./government/Env_Prot_Agen/jeffordslieberm.txt:767:tons for carbon, 1.3 million tons for SO2, 0.2 million tons for NOx
./government/Env_Prot_Agen/jeffordslieberm.txt:768:and 25 tons for mercury. In the case of carbon, the bank would last
./government/Env_Prot_Agen/jeffordslieberm.txt:842:The marginal cost of carbon reductions range from $46 to
./government/Env_Prot_Agen/jeffordslieberm.txt:845:and more energy-efficient and/or low carbon technologies penetrate
./government/Env_Prot_Agen/jeffordslieberm.txt:858:estimates of $15.2 billion for carbon, $1.1 billion for SO2, $2.7
./government/Env_Prot_Agen/jeffordslieberm.txt:860:cost estimates are $8.6 billion for carbon, $1.6 billion for SO2,
./government/Env_Prot_Agen/jeffordslieberm.txt:868:increases as the marginal cost of carbon decreases. The reason
./government/Env_Prot_Agen/jeffordslieberm.txt:870:and reduces carbon prices, more of a price signal is required to
./government/Env_Prot_Agen/jeffordslieberm.txt:873:the increased use of gas tends to reduce carbon emissions. But gas
./government/Env_Prot_Agen/jeffordslieberm.txt:1115:energy-efficient and low-carbon energy supply technologies,
./government/Env_Prot_Agen/multi102902.txt:144:control of SO2, SCR for the control of NOX, and activated carbon
./government/Env_Prot_Agen/multi102902.txt:229:activated carbon is expected to slightly increase as a result of
./government/Env_Prot_Agen/multi102902.txt:230:the Clear Skies Act. Activated carbon is traded on a global basis
./government/Env_Prot_Agen/multi102902.txt:406:AC Activated carbon
./government/Env_Prot_Agen/multi102902.txt:407:ACI Activated carbon injection
./government/Env_Prot_Agen/multi102902.txt:486:activated carbon injection (ACI) for the control of SO2, NOX, and
./government/Env_Prot_Agen/multi102902.txt:640:projects due to the global sourcing of carbon steel.
./government/Env_Prot_Agen/multi102902.txt:1223:carbonates that produced a high quality, fine calcium and magnesium
./government/Env_Prot_Agen/multi102902.txt:1224:carbonate FGD reagent. In addition to reducing the facility's
./government/Env_Prot_Agen/multi102902.txt:1859:carbon (AC) may ultimately prove to be superior for this
./government/Env_Prot_Agen/multi102902.txt:2192:will require the most activated carbon consumption and the most
./government/Env_Prot_Agen/multi102902.txt:2252:consumption and to segregate carbon from the ash. In this case,
./government/Env_Prot_Agen/multi102902.txt:2315:carbon injection occurrs in the ductwork between the air preheater
./government/Env_Prot_Agen/multi102902.txt:2430:ammonia, catalyst, or activated carbon, the "Cumulative Total MWe"
./government/Env_Prot_Agen/multi102902.txt:3065:granular and powdered carbon, powdered being preferable to granular
./government/Env_Prot_Agen/multi102902.txt:3307:Although U.S. demand for activated carbon is expected to increase
./government/Env_Prot_Agen/multi102902.txt:3309:activated carbon is traded on a global basis, and there is
./government/Env_Prot_Agen/multi102902.txt:3315:activated carbon demand from what is estimated here.
./government/Env_Prot_Agen/multi102902.txt:3467:http://www.roskill.co.uk/acarbon.html 
./government/Env_Prot_Agen/nov1.txt:527:carbon emissions in the developing world.
./government/Env_Prot_Agen/ro_clear_skies_book.txt:86:of carbon dioxide from electric power generators. The legislation
./government/Env_Prot_Agen/section-by-section_summary.txt:788:matter and carbon monoxide emissions. Where there is a modification
./government/Env_Prot_Agen/section-by-section_summary.txt:904:Amendments of 1990 to retain the existing carbon dioxide monitoring
./government/Env_Prot_Agen/tech_adden.txt:761:commercial timber sales yields) Ozone impacts on carbon
./government/Env_Prot_Agen/tech_sectiong.txt:24:emissions of sulfur dioxide (SO2), nitrogen oxides (NOx), carbon
```
* The command displays the matching lines and the line numbers for the pattern "carbon" in all files within the `./government/Env_Prot_Agen/` directory.
* This is useful because we can find out which lines contain the word "carbon" and exaclty where in the file it is located. Using this we can better understand the context of every instance of "carbon" within the `./government/Env_Prot_Agen/` directory. 

working directory: `./docsearch/technical/911report`
```
$ grep -n "international" *.txt
chapter-10.txt:176:                international, took place before the reopening of national airspace on the morning
chapter-10.txt:244:                international terrorist organizations in the Middle East.
chapter-10.txt:305:                Defense would plan to build an international coalition to go into Afghanistan. Both
chapter-10.txt:560:                    overwhelming international sympathy for the United States.
chapter-11.txt:45:                led an international coalition to reverse Iraq's invasion of Kuwait. Other examples
chapter-11.txt:48:                contain new nuclear dangers; and international involvement in the wars in Bosnia and
chapter-11.txt:81:                We believe American and international public opinion might have been different--and
chapter-12.txt:14:                on both Iraq and Afghanistan), homeland security, and international affairs rose
chapter-12.txt:31:                rather than international. That is the defining quality of world politics in the
chapter-12.txt:173:            The 9/11 attack was a complex international operation, the product of years of
chapter-12.txt:179:            A complex international terrorist operation aimed at launching a catastrophic attack
chapter-12.txt:345:                2001, the U.S.-led international coalition and its Afghan allies toppled the Taliban
chapter-12.txt:389:                    their efforts in Afghanistan so far. Now the United States and the international
chapter-12.txt:393:                    international crime and terrorism. The United States and the international
chapter-12.txt:406:                    Currently, the United States and the international community envision enough
chapter-12.txt:417:                    south and southeast. The U.S.government can do its part if the international
chapter-12.txt:454:                Welfare, charities and international relief agencies, such as the World Assembly of
chapter-12.txt:481:                bases remained there until 2003, as part of an international commitment to contain
chapter-12.txt:677:                The international community is moving toward setting a concrete goal-to cut
chapter-12.txt:707:                especially international commerce, requires ongoing cooperation and compromise, the
chapter-12.txt:731:            Practically every aspect of U.S.counterterrorism strategy relies on international
chapter-12.txt:752:                future of the Arab and Muslim world. These new international efforts can create
chapter-12.txt:760:                for the detention and humane treatment of captured international terrorists who are
chapter-12.txt:767:                set of standards for prisoners in internal conflicts. Since the international
chapter-12.txt:777:                    standards are generally accepted throughout the world as customary international
chapter-12.txt:811:                Therefore, the United States should work with the international community to develop
chapter-12.txt:812:                laws and an international legal regime with universal jurisdiction to enable the
chapter-12.txt:832:                redoubled its international commitments to support this program, and we recommend
chapter-12.txt:879:            The U.S. financial community and some international financial institutions have
chapter-12.txt:939:                them, international travel presents great danger, because they must surface to pass
chapter-12.txt:1005:            When people travel internationally, they usually move through defined channels, or
chapter-12.txt:1171:            The international community arrives at international standards for the design of
chapter-12.txt:1183:                    extensive international cooperation.
chapter-13.1.txt:261:                    preserving an agency's operational control. In the international context, NATO
chapter-13.1.txt:926:                    working intelligence investigations concerning the same international terrorism
chapter-13.1.txt:1005:                    with educational and professional backgrounds in intelligence, international
chapter-13.2.txt:428:                destroyed. The international hijacking crisis turned into a civil war, as the
chapter-13.2.txt:924:                internationally accepted within the aviation accident investigation community.
chapter-13.3.txt:576:                international terrorism criminal cases were designated as 265 matters. In 2003,
chapter-13.3.txt:577:                these designations were eliminated; all international terrorism matters now receive
chapter-13.3.txt:1348:                other sticks, such as blocking loans from international financial institutions,
chapter-13.4.txt:865:                Africa. The international community has tried to restrict trade in such gems. FBI
chapter-13.5.txt:814:            50. Thomas Pickard interview (Apr. 8, 2004). For example, an international terrorism
chapter-13.5.txt:1166:            95. The FISA definition of "foreign power" includes "a group engaged in international
chapter-13.5.txt:2344:                exchanges or international components. The White House efforts during the crisis
chapter-13.5.txt:2457:                international terrorism operations section, also heard from an FBI official in
chapter-13.5.txt:2644:                Iraq might negate progress made with the international coalition the administration
chapter-13.5.txt:2646:                international coalition. Ibid.
chapter-13.5.txt:2832:                homeland security, and international affairs).
chapter-13.5.txt:2912:                Mar. 19, 2003 (online at www.house.gov /international_relations/108/burn0319.htm).
chapter-2.txt:336:            The international environment for Bin Ladin's efforts was ideal. Saudi Arabia and the
chapter-2.txt:433:            Bin Ladin now had a vision of himself as head of an international jihad
chapter-2.txt:830:            Now effectively merged with Zawahiri's Egyptian Islamic Jihad, al Qaeda promised to become the general headquarters for international
chapter-3.txt:194:                together on international terrorism. While it was distinctly a CIA entity, the FBI
chapter-3.txt:314:                intelligence matters involving international terrorism, however, the rules were
chapter-3.txt:644:                provide security on international departures. This policy reflected the FAA's view
chapter-3.txt:874:                enemies. The cultural effects ran even deeper. In a more fluid international
chapter-3.txt:1334:                international criminal organization. . . . Finally, we must do more to protect our
chapter-3.txt:1443:                selective in their use of political capital for international issues.
chapter-3.txt:2126:                "champion a national effort to take up the gauntlet that international terrorists
chapter-3.txt:2201:                international terrorism"by supporting attacks on civilian targets in Kashmir. This
chapter-5.txt:56:                Water. Although he engaged in extensive international travel during his tenure at
chapter-5.txt:1005:                references to dozens of international trips. Operations required travel, as did
chapter-5.txt:1089:                Qaeda sympathizers in specific foreign branch offices of large, international
chapter-5.txt:1185:                organize and conduct a complex international terrorist operation to inflict
chapter-6.txt:566:                al Qaeda's financial transactions among the vast sums moving in the international
chapter-6.txt:587:                drug trafficking and high-level international fraud. Large-scale scandals, such as
chapter-6.txt:1512:                developed an international coalition to undermine the regime. In phase three, if
chapter-7.txt:388:                his previous international travel.
chapter-7.txt:638:                just wanted to pick up Atta's international driver's license and some money. This
chapter-7.txt:806:                to be known to international security agencies were purposefully selected for the
chapter-7.txt:933:                branches of major international banks and smaller regional banks. All of the
chapter-7.txt:978:            Our knowledge of the international travels of the al Qaeda operatives selected for
chapter-8.txt:190:            To enlist more international help, Vice President Cheney contacted Saudi Crown Prince
chapter-8.txt:790:                on international terrorism squads in the New York Field Office, advising of the
```

* The command displays the matching lines and the line numbers for the pattern "international" in all files within the current working directory. 
* This is useful because we can find out what lines contain the word "international" and the its position relative to its file for all the files within a directory.
