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
I went ahead and searched in scopus "social emotional learning" from just 2023. It resultsed in 300 doucments. I uploaded the file title scopus1.bib to gcloud
and went off to explore. 

I first ran the code `grep -Eio "@(A|B)[A-Z]*" scopus1.bib | sort | uniq -c` to breakdown the sources of the documents. The results were 249 articles, 39 books, 
and a bunch of different sources. 
`   249 @ARTICLE
     39 @BOOK
      2 @achva
      1 @act
      1 @andrew
      1 @angelo
      2 @ankara
      1 @arizona
      1 @assumption
      1 @asu
      1 @barrcenter
      1 @branksome
      1 @brocku
      1 @brown
      2 @bsu
      1 @bu
      3 @buffalo
      1 @byu`

Then I decided to run the code
`grep -o "Cited by: [0-9]*" scopus1.bib | \
> awk -F":" \
> 'BEGIN {printf "Total Citations: "} \
> { sum += $2; } \
> END { print sum }'`
> and found that only 274 total citations had come from these articles. I wondered if this was common.
>
Lastly I ran the code *after a few typos*
`grep "journal =" scopus1.bib | cut -d"=" -f2 | sed s'/ {//' | sed 's/}, //' | \
> sort | uniq -c | sort`.
> I was able to put together a list of the journal titles. 

     `1 2nd International Conference on Sustainable Computing and Data Communication Systems, ICSCDS 2023 - Proceedings},
      1 31st International Conference on Computers in Education, ICCE 2023 - Proceedings},
      1 ACM Transactions on Human-Robot Interaction},
      1 AERA Open},
      1 ASEE Annual Conference and Exposition, Conference Proceedings},
      1 American Journal of Community Psychology},
      1 American Journal of Health Education},
      1 Applied Research in Quality of Life},
      1 Art Education},
      1 Assessing Writing},
      1 Assessment for Effective Intervention},
      1 Assessment},
      1 Behavioral Disorders},
      1 Behavioral Sciences},
      1 British Journal of Educational Technology},
      1 Bulletin of the Menninger Clinic},
      1 Cambridge Journal of Education},
      1 Cases on Enhancing Business Sustainability Through Knowledge Management Systems},
      1 Child Indicators Research},
      1 Child Psychiatry and Human Development},
      1 Childhood Education},
      1 Children's Literature in Education},
      1 Children},
      1 Classroom Discourse},
      1 Clinical Child and Family Psychology Review},
      1 Cogent Psychology},
      1 College Teaching},
      1 Computer-Supported Collaborative Learning Conference, CSCL},
      1 Computers and Education},
      1 Contemporary Educational Research Quarterly},
      1 Counseling Outcome Research and Evaluation},
      1 Critical Cultural Studies of Childhood},
      1 Current Opinion in Pediatrics},
      1 Current Research in Ecological and Social Psychology},
      1 Developing Inclusive Environments in Education: Global Practices and Curricula},
      1 Dynamic Curriculum Development and Design Strategies for Effective Online Learning in Higher Education},
      1 Early Childhood Research Quarterly},
      1 Education 3-13},
      1 Education Finance and Policy},
      1 Educational Action Research},
      1 Educational Evaluation and Policy Analysis},
      1 Educational Forum},
      1 Educational Philosophy and Theory},
      1 Educational Policy},
      1 Educational Research},
      1 Elementary School Journal},
      1 Embracing Adult SEL: An Educator's Guide to Personal Social Emotional Learning Success},
      1 Emergent Practices of Learning Analytics in K-12 Classrooms},
      1 Encyclopedia of Child and Adolescent Health, First Edition},
      1 European Journal of Educational Research},
      1 European Journal of Psychological Assessment},
      1 European Journal of Psychology of Education},
      1 European Journal of Teacher Education},
      1 European Psychologist},
      1 Frontiers in Sociology},
      1 Frontiers in Sports and Active Living},
      1 Handbook of Research on Current Trends in Cybersecurity and Educational Technology},
      1 Honing Self-Awareness of Faculty and Future Business Leaders: Emotions Connected with Teaching and Learning},
      1 How People Learn in Informal Science Environments},
      1 Infant Mental Health Journal},
      1 Innovation in Language Learning and Teaching},
      1 International Journal of Bullying Prevention},
      1 International Journal of Christianity and Education},
      1 International Journal of Developmental Sciences},
      1 International Journal of Early Childhood},
      1 International Journal of Education and Practice},
      1 International Journal of Educational Research Open},
      1 International Journal of Environmental Research and Public Health},
      1 International Journal of Inclusive Education},
      1 International Journal of Music Education},
      1 International Journal of School and Educational Psychology},
      1 International Journal of Technology Enhanced Learning},
      1 International Review of Education},
      1 Intervention in School and Clinic},
      1 Investigations in Mathematics Learning},
      1 Irish Educational Studies},
      1 JAMA Network Open},
      1 JMIR Serious Games},
      1 Journal for Multicultural Education},
      1 Journal for ReAttach Therapy and Developmental Diversities},
      1 Journal for Specialists in Group Work},
      1 Journal of Applied Learning and Teaching},
      1 Journal of Autism and Developmental Disorders},
      1 Journal of Child and Family Studies},
      1 Journal of Creativity in Mental Health},
      1 Journal of Dance Education},
      1 Journal of Early Childhood Literacy},
      1 Journal of Education Policy},
      1 Journal of Education},
      1 Journal of Educators Online},
      1 Journal of Evidence-Based Psychotherapies},
      1 Journal of Experiential Education},
      1 Journal of Latinos and Education},
      1 Journal of Loss and Trauma},
      1 Journal of Medical Humanities},
      1 Journal of Mental Health},
      1 Journal of Mixed Methods Research},
      1 Journal of Multilingual and Multicultural Development},
      1 Journal of Positive Psychology},
      1 Journal of Psychologists and Counsellors in Schools},
      1 Journal of Research in Music Education},
      1 Journal of Research on Educational Effectiveness},
      1 Journal of Research on Leadership Education},
      1 Journal of School Health},
      1 Journal of Special Education Technology},
      1 Journal of Teacher Education for Sustainability},
      1 Journal of Teaching and Learning},
      1 Journal of Transformative Education},
      1 Journal of Youth and Adolescence},
      1 Kappa Delta Pi Record},
      1 Learning Disabilities Research and Practice},
      1 Learning Disorders Across the Lifespan: A Mental Health Framework},
      1 Methods in Psychology},
      1 Mindfulness},
      1 Motivation and Momentum in Adult Online Education},
      1 Pediatrics},
      1 Perceptual and Motor Skills},
      1 Personality and Individual Differences},
      1 Phenomenological Studies in Education},
      1 Policy and Practice},
      1 Preventing School Failure},
      1 Proceedings of the 2023 IEEE 6th International Conference on Knowledge Innovation and Invention, ICKII 2023},
      1 Reading Teacher},
      1 Remedial and Special Education},
      1 Research in Mathematics Education},
      1 Review of Education},
      1 Revista Cubana de Investigaciones Biomedicas},
      1 Revista Electronica Educare},
      1 Roczniki Humanistyczne},
      1 School Psychology International},
      1 School Psychology},
      1 Soccer and Society},
      1 Social Development},
      1 Springer International Handbooks of Education},
      1 Strategies},
      1 Studies in Art Education},
      1 Studying Teacher Education},
      1 TESOL Journal},
      1 Teachers as Mentors: Models for Promoting Achievement With Disadvantaged and Underrepresented Students by Creating Community},
      1 Teaching Education},
      1 Teaching Multicultural Children’s Literature in a Diverse Society: From a Historical Perspective to Instructional Practice},
      1 Teaching and Teacher Education},
      1 The Faculty Factor: Developing Faculty Engagement With Living–Learning Communities},
      1 The Oxford Handbook of Care in Music Education},
      1 The Social-Emotional Learning Upgrade: Merging SEL and Technology Curricula to Support Young Learners},
      1 Theory and Research in Social Education},
      1 Trauma, Violence, and Abuse},
      1 Trials},
      1 Understanding Emotion Regulation},
      1 VISUAL Review. International Visual Culture Review / Revista Internacional de Cultura },
      1 Youth and Society},
      2 AIP Conference Proceedings},
      2 Conference on Human Factors in Computing Systems - Proceedings},
      2 Current Psychology},
      2 Cyberbullying and Values Education: Implications for Family and School Education},
      2 Educational Studies - AESA},
      2 Frontiers in Public Health},
      2 International Journal of Emotional Education},
      2 Journal of Community Psychology},
      2 Journal of Early Adolescence},
      2 Journal of Educational and Psychological Consultation},
      2 Journal of General Music Education},
      2 Journal of Moral Education},
      2 Journal of Psychoeducational Assessment},
      2 Journal of School Psychology},
      2 Kinesiology Review},
      2 Lecture Notes in Networks and Systems},
      2 Pediatric Reports},
      2 RMLE Online},
      2 Research on Social Work Practice},
      2 School Psychology Review},
      2 School Violence and Primary Prevention, Second Edition},
      2 Scientific Reports},
      2 Social Psychology of Education},
      2 Social Sciences and Humanities Open},
      2 Theory into Practice},
      3 Child and Youth Care Forum},
      3 Early Education and Development},
      3 Education and Urban Society},
      3 PLoS ONE},
      3 Phi Delta Kappan},
      3 Proceedings of IDC 2023 - 22nd Annual ACM Interaction Design and Children Conference: Rediscovering Childhood},
      4 Handbook of Resilience in Children},
      4 Journal of Intelligence},
      5 Psychology in the Schools},
      6 Education Sciences},
      7 Journal of Physical Education, Recreation and Dance},
      7 School Mental Health},
     10 Early Childhood Education Journal},
     11 Frontiers in Education},
     13 Exploring Social Emotional Learning in Diverse Academic Settings},
     14 Frontiers in Psychology}`

### Review
I continue to struggle with flashcards. I just struggle with confience in the moment with this class. I am learning a lot and really taking the time throughout the week to practice with the intent of learning everything we do.
I feel very confident on learn-the-cli and learn-thefilesystem. 



