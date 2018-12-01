# pgr301-exam-18-infra

Exam repository for PGR301 at Westerdals OSLO ACT/Høyskolen Kristiania, Fall 2018 by candidate number: 100018

1. [  Instructions ](#Instructions)
2. [ Attempted Features ](#AttemptedFeatures)
3. [ Reflections ](#Reflections)
4. [ References ](#References)


<a name="Instructions"></a>
## 1. Instructions

##### Set up infrastructure:
1. Replace the names and URIs the project. For simplicity, all name/URI variables have been tagged with "TODO", which will automatically pop up in the tab named "TODO" in the bottom of IntelliJ
2. Replace Heroku variables (optional).

##### Run the app manually:
1. Stop any running applications that run on port 8080
2. Run the Application class, generate target
3. Maven: "spring-boot:run"
4. Go to one of the endpoints listed below

 - http://localhost:8080/add-item?item=Go skydiving
 - http://localhost:8080/get-list
 - http://localhost:8080/get-item?id=1
 - http://localhost:8080/update-item?id=1&item=Dance all the Fortnite dances
 - http://localhost:8080/delete-item?id=1
 - http://localhost:8080/delete-all

##### Testing:
1. Run Application
2. Maven: "spring-boot:run"
3. Run tests


<a name="AttemptedFeatures"></a>
## 2. Attempted Features

Basic Pipeline


<a name="Reflections"></a>
## 3. Reflections

In case there is any questions to the usernames used to commit on GitHub: 
I, the candidate 100018, is the only human that has committed anything to the repositories. The Concourse bot has of course committed too, but this is expected.
I have used two computers (home- and school computer), with different display names because I thought it would simplify the overview. 
I noticed recently that it makes less sense with aliases because they don't directly link back to the profile of the user which can look very suspicious. 
All contributors should appear under "Insights/Contributors", though, even if the Concourse bot does not appear there. Otherwise, runnig the "git log | grep Author: | sort | uniq" in the commandline in the repo folder shows that at least one of the candidate aliases has the same email.
Nonetheless, I understand if this looks fishy, so I choose to highlight it and my confidence in it being resolved.

##### Infra:

The infra-part of the project started off pretty good. I was confident because the assignment sounded similar to the exercises that was assigned in class. This soon turned around when it came to testing the pipeline. 
First off I had some issues because I put the name of the infra-repository in one of the fields which should have the name of the app-repository. The small error was simple to fix, though it took some time before I found where the error was.
The second issue was much, much worse. concourse/terraform/task.yml, the file runs the shellscript "terraform.sh". For a while the error messages fluxed between "file not found" and "permission denied". 
"File not found" is self explaining, but lack of experience with containers and how they ran made it slightly more difficult. In the end, with trial an error, as well as looking at some examples from the provided exam repository. 
"Permission denied" was much worse to figure out. Scouring the internet I found a few people with similar issues, but none of them had the same setup with concourse and docker. Again, using trial end error, 
with close to 50 attempts and a lot of pushing to GitHub (commits with "pathtest", "test" or simply a number can be ignored, mostly pushed for figuring this problem out) I found a was to run the script. 
I still don't know why the file was denied permission, but I tried various ways of setting file read/write/executables, but ended up running the file though the terminal in the image (I think). 
To make matters worse the internet was cut for 2 and a half days so I had limited access though shared wifi though my phone.
Once it seemed like the pipeline found the fine and could execute it, the pipeline halted, prompting me for an API key for Statuscake. Simply removing anything that had to do with Statuscake fixed this, even though I had the key in my credentials-file (correct key name and value).

In the later parts of getting the Basic Pipeline requirement to work, 
I wasn't entirely sure what the last bullet point under Application was supposed to mean.
The text reads: "Should any of the tests fail, the build should fail", where the of "tests" is clear, 
referring to unit-tests in the bullet point above, however, what "build" isn't entirely clear. I originally thought it meant the pipeline build,
but after some attempts trying to get it to work I'm grew more uncertain. I don't recall going though this is class. 
The only references to testing I could find in the course assignments was in the course 9 assignments, being part of a 
Docker run-command, building an application with no unit tests (example app from lessons 7 and 8).
Due to this, and the context of the bullet point being under the application header, I assume this means that the Maven (mentioned in a bullet point above) 
build on the machine should fail, not the pipeline. 


TODO:
documentation
 - Attempted features
 - Reflections
Other features
check examionator walkthough
Final go though, check for names, todos, fixmes etc.

##### On the app:
I didn't expect to made an API for this exam so It caught me off guard and delayed the plans I had. 
Anyways, since we've had other courses where we make APIs this semester I had some code I could lean on to fast track the development. 
Since the other courses don't use Java I didn't actually use any code, just looked at the structure. 
I did, however find a lot of guides on the internet I did draw inspiration and a few snippets of code from. 
The links to these sites are of course listed under [References](#References)
I also had to do some things to jerryrig the app together, that aren't in line with what we've been though is good code practise. 
One example is that I used a test method to clear the data in the map (IMDB) in the @Before method. 
Ideally you shouldn't rely on tests or network methods to perform utility operations like resetting variables or databases, but with API you sort of have to.
Some of the test where the appropriate status code would be "201 created" results in an error, will fail since the status code is 200. 
This is due to poor implementation of the API. Luckily though, the API is not the focus in the exam.

<a name="References"></a>
## 4. References


##### App references:

General pointers to make API from Spring.io:
https://spring.io/guides/gs/rest-service/

setup method in BucketlistApiTest, from Semaphoreci.com:
https://semaphoreci.com/community/tutorials/testing-rest-endpoints-using-rest-assured
