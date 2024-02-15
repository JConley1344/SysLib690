# Week 6-Grep Searching
## **Reproducing the Examples**

For this weeks work I started in the UK database Scopus. I first started by recreating what 
I saw in the video and found the articles and information. I then used that metadata to follow 
along with the weekly video to work through kystrokes and understanding. I felt comfortable enough
to try pulling different data and seeing if I could understand the results.

## **New Data**
*Searching using the term "social emotional learning"*
This search yelded **1506** results. I took the first two pages of results to download, which was *20*
total titles.

## Uploading the File
I opened the terminal. I connected to the terminal, and connected via gcloud command. I then created a file
named `scopus.bib`. I then started to explore the `grep` codes with this file. 

Using the `grep -Eio "^@(A|B)[A-Z]*" scopus.bib | sort | uniq -c` I was able to see that of the *20* files 
19 were articles and 1 was a book.
     `19 @ARTICLE
      1 @BOOK`




