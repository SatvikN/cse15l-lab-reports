# Lab Report 4

## Step 4: Log into ieng6
**Keys pressed:** `<up> <enter>`
* The command `ssh s5nayak@ieng6-201.ucsd.edu` was 1 up in the search history so I accessed it using the up arrow.

## Step 5: Clone fork of the repo
**Keys pressed:** `g i t <space> c l o <tab> Command-V <enter>` 
* Pressing `<tab>` completed the `clone` command and added a space after. The the `SSH` URL was already copied into my clipboard using my mouse so I just pasted it in using `Command-V`.

## Step 6: Run the tests (fail)
**Keys pressed:** `c d <space> l <tab> <enter>`, `b a s h <space> t <tab> <enter>`
* First I changed the directory to `lab7`. Since there is only 1 directory starting with the letter _l_ in the home directory, I was able to complete the name using `<tab>`.
* Then I had to run the `test.sh` file using the `bash` command. Within the `lab7` directory there is only 1 file that starts with the letter _t_ so I could finish the file name using `<tab>`.

## Step 7: Edit code
**Keys pressed:** `v i m <space> Shift-L <tab> . <tab> <enter>`, `3 2 9 e x i 2 <esc> : w q <enter>`
* In order to edit the code file to fix the failing test I first had to use the `vim` command. I could type the file name by typing the first letter _L_ and then using tab to write out the other characters. However, there are 2 files in the `lab7` that begin with the letter _L_: `ListExamples.java` and ListExamplesTests.java. Tab filled in the idential characters until it said _ListExamples_. Since the desired file is `ListExamplesTests.java` I added a . so differentiate between the 2 possible files. Then I used `<tab>` to complete the name.
* Next I used the command `329e` in `vim`'s normal mode to move the cursor to the end of the 329th word which was the `index1` that had to be edited to `index2`. Pressing the `x` key in normal mode deleted the character under the cursor which was _1_. Then I pressed the `i` key to switch to `vim`'s insert mode and then pressed `2` to change the code to `index2`. After this, in order to save the edits, I pressed `<esc>` to switch back to normal mode and then used the command `:wq` to write my edits and exit `vim` editor.

## Step 8: Run the tests (pass)
**Keys pressed:** `<up> <up> <enter>`
* The command `bash test.sh` was 2 up in the search history on ieng6 so I used the up arrow key to access it.

## Step 9: Commit and push
**Keys pressed:** `g i t <space> a d <tab> . <enter>`, `g i t <sapce> c o m <tab> <space> - m <space> Shift-" e d i t s Shift-" <enter>`, `g i t <space> p u s h <enter>`
* I used the `git add .` command to move all the modified files to the `git` staging area. Since there is only 1 `git` subcommand that begins with _ad_ I was able to finish the command and add a space just by pressing `<tab>`.
* After moving any modifications to the staging area, I used the `git commit` command to record the changes within the repository. Since there is only 1 `git` subcommand that begins with _com_ I was able to finish the word and add a space by pressing `<tab>`. I also added a commit message by adding `-m "edits"` to the end of the `git commit` command.
* Finally, I used the `git push` command to upload the commit back to a remote repository.
