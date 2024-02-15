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
**I was able to open a SSH-in-browser window and just select **upload file** without issues, it opened undermy normal gcloud name.*

Using the `grep -Eio "^@(A|B)[A-Z]*" scopus.bib | sort | uniq -c` 
I was able to see that of the *20* files 19 were articles and 1 was a book.
     `19 @ARTICLE
      1 @BOOK`

I then wanted to look at citations because I noted everything I had pulled was published in 2024. I Found that interesteing. Using 
` grep -o "Cited by: [0-9]*" scopus.bib | \
    awk -F":" \
    'BEGIN { printf "Total Citations: "} \
    { sum += $2; } \
    END { print sum }'`
I was able to see that there was a total of 6 citations. Which is more than I thought they might have due to the dates. 

Also I sorted the journal titles out using
`grep "journal =" scopus.bib | cut -d"=" -f2 | \
    sed 's/ {//' | sed 's/},//' | \
    sort | uniq -c | sort`
and found that there were 20 different journal/book titles, not one that might have more infomraiton regularly on the topic. 

## Playing with More Data






