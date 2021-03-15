# ISAGEe-Arabic: Integrated Short Answer Grader for e-learning environment (For Arabic)
 
  
                                    Version 1.0
                                    
=======================        

License : http://www.gnu.org/copyleft/gpl.html GNU GPL v3 or later

=======================
CONTENTS
1. Introduction
2. The Folder Structure

2.a. The Moodle Plugin ISAGEe-Arabic  /V1/

2.b. External Grader code on Distant server

3. How to deploy ?
4. Feedback
5. Acknowledgments

=======================
1. Introduction

The grader is integrated into the online quiz system deployed on Moodle. 
The Question Engine, the core module of the quiz system, is extended with our new Question Type ISAGe. 
The grader architecture highlights two modules: 
• The ISAGe Question Type Plugin. Extends the Question Engine of the quiz system to our new question type. 
The plugin controls the communication flow with the other modules of the quiz system and inherits the question behavior, question bank, quiz reports, …   from the e-learning system. 
• The external grader. Deployed on the Cloud, implements the trained model to predict grades
  
Actually, the Grader is used on our Moodle University Plateform in formative and summative tasks using open short answers. 
 
=======================
2. Folder Structure (Plugin Moodle + Grader code on distant server)

 2.a.ISAGe Question Type Plugin-Arabic
 
 2.b.ISAGe External Grader-Arabic

=====
2.a. The Moodle Plugin  V1 (ISAGEearabic) 

This is our Moodle Plugin using  Moodle question type template  and adapted to grade Arabic short answers scoring using NLP computation and supervised learning.  

* Please see here for more information about : Moodle-Short Answer Question Type : 
https://docs.moodle.org/37/en/Short-Answer_question_type
 

=========================
2.b. Grader code on Distant server /

- The grader function is deployed on a distant server (Pythonanywhere) to release the platform 
from the assessment task for this question type, particularly when scoring a large number of online students at the same time.

- The code in this folder  is deployed via a web application on Pythonanywhere using the framework Flask.
A PHP cURL script is used to connect the plugin to the Flask API which deploys the grader on PythonanyWhere. 

- Python version : Python 3.7

- The grader can be used and tested in a desktop version : 

#############" Instructions to run the code  #################

1. The folder "Requirements" includes files data(the trained model, semantic space, Word Embeddings, words-dictionary,stop words, Min-Max dictionary(TFlog Wheights))

2. Put the content of the link bolow in the "requirements" folder : 
   https://drive.google.com/drive/folders/1wGI8jdHtk1Ny0h171RUa1qEKcjp3fznh?usp=sharing
   
3. Introduce (question, student answer, reference answer and difficulty) to the getScore function as in the example in the main function. 

5. The code is written to test several pairs of reference answers and student answers. 
That's why we used "Arrays" for the questions and answers each time.
If the code is to be used to test a single pair then put the question, the reference answer and the student answer each in an "Array".
All functions that take the parameters named "AllQuestionCorpus" or "ResponsesCorpus" must be in the folowing syntax:
AllQuestionCorpus=[[response1Question1,response2Question1,...],[response1Question2,response2Questio2,...],....]
ModelAnswers=[Model1,Model2 , ... ]

=======================
3. How to deploy the plugin ?

- The Plugin must be installed on a Moodle plateform  to be used:
(Install the ISAGEearabic.zip)
  (Dashboard / Site administration / Plugins / Install plugins). 

- A PHP cURL script is used to connect the plugin to the Flask API which deploys the grader on PythonanyWhere(already done in the plugin).
(see: question.php in the section : // Call the grader )


 
