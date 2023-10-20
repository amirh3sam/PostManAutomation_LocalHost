
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/9e109094-70c0-430f-93c7-288187c27cad)

##:heavy_check_mark: **PostMan Automation**

In order to set up a free server effortlessly, you can generate the server by executing a few lines of code in the command prompt. To learn how to create your own local server for testing HTTP API requests, visit this GitHub page [CLICK HERE](https://github.com/MRSamBadiei/practice-api-server) , which provides instructions on the process. With this server, you can conduct tests involving GET, POST, PUT, PATCH, and DELETE methods on data pertaining to name, gender, and age. Begin by establishing a database on your local host to assess GET and POST operations for data creation. You can also utilize this server to DELETE or UPDATE your database as needed. Once the server is up and running, you can proceed to Postman for automated testing.



after you create the server now we can do some testing and verificaiton on responses :arrow_right: http://localhost:3000

 ---
:pushpin: **STEP 1** : Establish a workspace and assign it any name you prefer, such as "MyAutomationAPI."
 
:arrow_right: now need to create a Collection and give a name like  APIPractice )

after you click on APIPractice you can see the Tab called "Variavles " and click on it.

:pushpin: **STEP 2** : Under **VARIABLE**  column type →  ``` heroUrl ```

Then under **CURRENT VALUE** – > ```http://localhost:3000 ```

**INTIAL VALUE** → is the url that you used to shared it with others

see other type of variable : 

- **Global variable**

- **Collection variable**

- **Environment variable**

- **Data variable**

- **Local variable**
  now high light the variable and choose set as variable and name it HeroBaseUrl choose global
  ![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/3d370534-9f05-4c1b-b316-19adbd319668)
  ![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/c4a918b3-eb39-441f-9265-ac04a1a44c84)
  
---
:pushpin: **STEP 3** :
our first request: <code> **GET  →** save then run it</code>

Click on **Test** tab → on the right side you have method than you can choose

Inside Test you need to type JS code

Click on
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/21935791-c987-477c-84ac-787c41f18780)

**→ to verify status code**.

```javaScript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

** Just need to change that 200 inside the () to any status code you want**

Then run gonna see under Test Results shows pass

→ to verify headers

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/2ac56a9f-69ee-4966-afd0-6d1df1f3e865)

```JavaScript
pm.test("Content-Type is present", function () {
    pm.response.to.have.header("Content-Type");
});
```


→ if you want to verify for example Date is present in the header just need to copy and past same code and change instead “Content-type” chenge to “Date” then click Send
in this API (Header) we do not have date or Contnet-Type


```JavaScript
pm.test("Date is present", function () {
    pm.response.to.have.header("Date");
});
```


#### Is not case sensitive instead Date you can type date

Now want to verify content type is application/json now in second line after “Content-Type” add comma and type “applicaiton/json”

```JavaScript
pm.test("Content-Type is applicaiton/json, function () {
    pm.response.to.have.header("Content-Type","applicaiton/json");
});
```

Another thing want to check header Transfer-Encdoing is chunked:

```JavaScript
pm.test("Transfer-Encdoing is chunked, function () {
    pm.response.to.have.header("Transfer-Encdoing","chunked");
});
```

in this example we do have this Types in header you can Practice =
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/9ad77b69-b3be-45de-b60a-d30bd8588da6)


if you have a API that allow you to post for example after you  create <code> POST {{YOURLINK}} </code>

Under body Choose jason Then add value then send get 201 Status code
as you see on this example we add one json file to our database 

![image24](https://user-images.githubusercontent.com/69331074/234322543-ebf2c659-0742-45b4-b062-2ad49b66f7e2.png)


Now go to **Test** tab

Check status code

![image8](https://user-images.githubusercontent.com/69331074/234322584-d5da10cd-7bed-4f34-b5f0-a03b0c1d27d6.png)
ng)

Now from right click on Respond body: Json value check

![image6](https://user-images.githubusercontent.com/69331074/234322609-584fb0ce-caf9-4ed0-a182-3557b42af808.png)


![image27](https://user-images.githubusercontent.com/69331074/234322626-0b9e8bce-b900-42df-9a59-00411be78266.png)


Now need to change in third line **value** to **success** and **100** to **“A Spartan is Born!”**

![image13](https://user-images.githubusercontent.com/69331074/234322656-e0f7c054-5da7-4355-a39e-aafdc8bc0983.png)


If want to get a name just copy and past same code then change it like this

![image31](https://user-images.githubusercontent.com/69331074/234322693-6a90b676-bace-4bb7-81b0-9e6866c64cbe.png)


**Create Json object:**

<code>Var jsonData = pm.response.json();</code>

**To print name on console:**

<code>console.log(“Spartan name: “ +jsonData.data.name);</code>

![image25](https://user-images.githubusercontent.com/69331074/234322713-a59e1574-9daf-47e9-bd2c-c9e70e3e334c.png)


And this is a out put:

![image17](https://user-images.githubusercontent.com/69331074/234322751-6f0a3b95-e352-4d55-9577-b25d6639c033.png)


Click on your Collection that allows to use PUT HTTP request  right click and create new request :<code> PUT /{{YOURURL}}/:id</code>


And change the phone number to all 1111111111 save your change and send get 204 status code

Now click on Test

Click on status code and change it 204

![image4](https://user-images.githubusercontent.com/69331074/234322777-a3a0d2b1-2e21-4125-91f2-c705bda0b31d.png)


At this point we need to capture the id from POST request

We going back on our POST request and on Test tab need to save our ** json data into global variable **

![image28](https://user-images.githubusercontent.com/69331074/234322880-64993d78-8465-42fd-bf98-60c5f68ab7d0.png)


![image16](https://user-images.githubusercontent.com/69331074/234322900-7a2e9f72-910a-499d-9888-e41b1a4902ad.png)


On the right side click on

![image34](https://user-images.githubusercontent.com/69331074/234322924-2fc04968-1aeb-4503-9439-03ab04e859f8.png)


Then save it

Now we go PUT request and add id with value <code> {{SPARTAN_ID}}</code>

![image3](https://user-images.githubusercontent.com/69331074/234326928-d34b8a6b-37b4-4ca9-a262-36a6f1ee4d6a.png)


Now want to create <code> DELET /{{baseSWAPI}}/api/spartans/:id</code>

![image23](https://user-images.githubusercontent.com/69331074/234322961-2c5d0917-0f81-4b3e-b3d5-079f165adc62.png)


Create <code> GET / {{baseSWAPI}}/api/ Spartans/:id  </code>to check that id does not exist

On Test tab check the status code and error massage

![image11](https://user-images.githubusercontent.com/69331074/234323035-d11121a0-d802-4569-8cf9-93bd68dc04d6.png)


We are using static **post spartan name** right now. We want to **get dynamic name** to **post** and **verify** that **name is posted.**

In order to **use random** **firstname** in **our post request**, we used <code> **{{$randomFirstName}} </code> in request body**.

But the **problem** is, we **cannot verify** after we **post** the name in **Tests field** in **Postman**.

**To overcome this problem.**

we used **Pre-Request Script tab** from postman.

**how can we use <code> {{$randomFirstName}} </code>in pre request script ?**

<code>var name = pm.variables.replaceIn('{{$randomFirstName}}');</code>

-:arrow_right: we set SPARTAN_NAME global variable from name variable

<code>pm.globals.set("SPARTAN_NAME", name);</code>

![image33](https://user-images.githubusercontent.com/69331074/234323124-df3c6a0f-737c-453e-b6cf-59825669a799.png)


![image29](https://user-images.githubusercontent.com/69331074/234323590-14de02b4-2b61-4fb6-a51e-a8ebaf4d6cce.png)


## **:heavy_check_mark: FLOW :arrow_right: **

:heavy_check_mark: First Pre-Req Scrip

:heavy_check_mark: Then API Request

:heavy_check_mark: Then API Response

:heavy_check_mark: Last Test

![image26](https://user-images.githubusercontent.com/69331074/234323614-fdf63b30-3146-4487-9fa8-3160f1eeed75.png)


:heavy_check_mark: Set global name

Then after request and response complete, under Test tab, we read the Global variable SPARTAN_NAME and assign as an expectedName

![image2](https://user-images.githubusercontent.com/69331074/234323638-3c937d2b-0965-4500-b928-5a43461bff5c.png)


![image30](https://user-images.githubusercontent.com/69331074/234323670-fdd7c3f0-5470-4679-bdcb-ef1c24f5831a.png)


## :heavy_check_mark: RUN Collection

You can run whole collection here also can give schedules run

Or manually run or give number of Iterations → how many time

You want to run it or delay or if you have external data like

Excel file you can choose Data and click Run spartan

See all result details after you run it.

##:heavy_check_mark: DDT:

SO IN THIS FLOW, WE USED RANDOM VARIABLE WITH SAVING AND REUSING IT.

CAN WE USE POSTMAN AUTOMATION WITH EXTERNAL DATA/FILE

**I want to use my .csv file to automate Spartan Flow**

Make copy of your Spartans folder and name it **Spartan DDT**

**I have my csv file on my desktop**

**Need to get the URL from Spartans :**YourIpAddress

**And add it to SpartanDDT**

We create one .csv file where we have name, gender and phone fields.

Then our **POST REQUEST BODY** we use **those field names** with **{{}}**
<code>
{

"gender":"{{gender}}",

"name":"{{name}}",

"phone":{{phone}}

}
</code>
**Remove variable name** in **Pre-request** because in this case we do not need it delete everything on the Post → Pre-request

Under **Test** tab **remove** global name

![image15](https://user-images.githubusercontent.com/69331074/234323694-d19e3ce2-cb87-4f21-a401-11a91523ab1b.png)


Now need to add expectedName like this:

![image1](https://user-images.githubusercontent.com/69331074/234323723-491d00ed-8217-4a49-9d22-8a49498e1d08.png)


You can remove the log part too(print json response and print something on the console)

![image36](https://user-images.githubusercontent.com/69331074/234323742-9f8fef48-1d3f-4a0e-998d-4c1e0f624042.png)


Keep the ID!

when we execute through Collection Runner, there is an option to pick file, we just need to click select file and pick our .csv file.

**And click Run Spartan DDT**

if the column names and variable names are matching, postman will provide those information.

To access to same information for each iternation dynamically in the Tests tab, we used following code

<code>var expectedName = pm.iterationData.get("name"); </code> -:arrow_right: this parameter needs to match from csv column name again.

We want to have **different Enviroment**

Click on right side menu bar on **Enviroments**

**Then click on creat Enviroments**

And name it **QA1**

**Now we have to define different Enviroments start with :**

**--------------------instead XXXXXXXXXX  add your actual informaion in Project------------------**

**baseUrl** type it under VARIABLE and add XXXXXXXXXX under **CURRENT VALUE**

Next **VARIABLE** is **tearcher_email** and the **CURRENT VALUE** is **XXXXXXXXXX**

**teacher_password** is **XXXXXXXXXX**

**If you want to password invisible change type to secret**

**Next**

**leader_email is XXXXXXXXXX and leader_passeword is XXXXXXXXXX**

**Then right click on QA1 and choose Duplicate**

**Change name to QA2**

**Now we change only the values**

**baseUrl** is XXXXXXXXXXX**

**tearcher_email** is **XXXXXXXXXX**

**teacher_password** is **XXXXXXXXXX**

**teader_email** is **XXXXXXXXXX**

**leader_passeword** is **XXXXXXXXXX**

**Creat** new **collection** and called it **ANYNAME** And add **new request**

**Name : GET /leader token**

Next from top right where said no environment pick **QA1 now** when you try do your request after GET type <code>{{baseUrl}}</code> gonna see green that comes from Enviroment QA1

<code>**GET {{baseUrl}}/sign** </code> and add **email** and **password**

**Eamil is <code>{{leader_email}}</code>**

**Password is <code>{{leader_password}</code>}**

![image7](https://user-images.githubusercontent.com/69331074/234323773-e28619b1-7d92-4fa1-a6fa-5dde800549c6.png)


If right now just change the QA1 to QA2 and send it again you gonna get a new token from Enviroment QA2

In **Test** tab want to check **status code** and **get a token** and save as an leader Token env variable.

![image10](https://user-images.githubusercontent.com/69331074/234323797-d86b3f2b-5d7d-401a-b6ce-42ba701e5b04.png)


From right side click on status code and click on Respond body : Json value check

Then we delete first line and third line and only keep the

<code>**var jsonData = pm.response.json();**</code>

**And add**

<code>**console.log(jsonData.accessToken);**</code>

**Add this to var → <code>var accessToken = jsonData.accessToken;</code>**

**After we print Token I need to add it in to my Enviroment Variable**

![image22](https://user-images.githubusercontent.com/69331074/234323819-06837e75-7f62-4776-94ae-b95b1e0eb1a2.png)


click on Set an envriment variable

So you gonna see this :

<code>**pm.environment.set(“leaderToken”, accessToken);**</code>

After run goona see it on your environment QA1 and QA2

Then right click on Bookit and create another request

<code>**GET → {{baseUrl}}//api/users/me**</code>

**Click on Authorization and Token → type → <code>{{leaderToke}}</code>**

![image20](https://user-images.githubusercontent.com/69331074/234323845-0d14c44d-efa1-4954-9024-447614bddc78.png)


##:heavy_check_mark: **DDT** with **schedule** **after click** on **Run collection** from **Spartan collection**

On there

**:heavy_check_mark: Schedule configuration**

give **name** like **SMOKE TEST EVERY DAY** at **8:00AM** and can choose **Environment** like **QA1** and Click **Schudel Run**

![image38](https://user-images.githubusercontent.com/69331074/234323868-2a56c7c8-358a-4803-9bfe-b4536145bce2.png)


Another way to run the collection is choose by Automate runs **via CLI**

Run on postman CLI need to install :

[https://go.pstmn.io/install-cli-win64](https://go.pstmn.io/install-cli-win64)

then with command line deponds on your operation system and how is work by type code on command line can execute test. Copy past the API key on command line and run!

**Or**

##:heavy_check_mark: **Run on CI/CD pipe line**

**You can pick Jenkins and run it !**

**[https://learning.postman.com/docs/collections/using-newman-cli/integration-with-jenkins/](https://learning.postman.com/docs/collections/using-newman-cli/integration-with-jenkins/)**

![image37](https://user-images.githubusercontent.com/69331074/234323956-2396bca1-442e-4595-9728-9c25a432fa62.png)


**:heavy_check_mark: Now want to do Schema**

<code>**Get {{baseSWAPI}}/api/spartans**</code>

**Test tab type :**

<code>**Var Schema = {add your schema all json objects here};**</code>

![image19](https://user-images.githubusercontent.com/69331074/234323981-8dd9cd77-b6c4-4796-8516-2f80cbcf0445.png)


After that type:

<code>**Var response= JSON.parse(responseBody);**</code>

<code>**Tests[“schema is Valid”] = tv4.validate(response,schema);**</code>

<code>**console.log(tv4.error);**</code>

![image14](https://user-images.githubusercontent.com/69331074/234324002-6e6ddbc0-ddcd-4cb0-8814-5fe3a4c6985e.png)


**Then Send should get 200 Status code**

If some one ask you how to validate schema you can tell with tv4.validate library .
