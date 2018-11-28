# pgr301-exam-18-infra

Exam repository for PGR301 at Westerdals OSLO ACT/Høyskolen Kristiania, Fall 2018 by candidate number: 100018

1. [  Instructions ](#Instructions)
2. [ Attempted Features ](#AttemptedFeatures)
3. [ Reflections ](#Reflections)
4. [ References ](#References)


<a name="Instructions"></a>
## 1. Instructions

##### Set up infrastructure:
1. Replace the names and URIs in concourse/pipeline.yml
2. 

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
1. Maven: "spring-boot:run"
2. Run tests


<a name="AttemptedFeatures"></a>
## 2. Attempted Features



<a name="Reflections"></a>
## 3. Reflections

##### Infra:
Stuck on pipeline.yml for a while, got mixed up with use of infra/app in ci-file.

##### On the app:
I didn't expect to made an API for this exam so It caught me off guard and delayed the plans I had. 
Anyways, since we've had other courses where we make APIs this semester I had some code I could lean on to fast track the development. 
Since the other courses don't use Java I didn't actually use any code, just looked at the structure. 
I did, however find a lot of guides on the internet I did draw inspiration and a few snippets of code from. 
The links to these sites are of course listed under [References](#References)
I also had to do some things to jerryrig the app toghether, that aren't in line with what we've been though is good code practise. 
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
