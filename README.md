
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/9e109094-70c0-430f-93c7-288187c27cad)

##:heavy_check_mark: **PostMan Automation**

To set up a free server effortlessly, you can generate the server by executing a few lines of code in the command prompt. To learn how to create your local server for testing HTTP API requests, visit this GitHub page [CLICK HERE](https://github.com/MRSamBadiei/nodejs-api-server), which provides instructions on the process. With this server, you can conduct tests involving GET, POST, PUT, PATCH, and DELETE methods on data about name, gender, and age. Begin by establishing a database on your local host to assess GET and POST operations for data creation. You can also utilize this server to DELETE or UPDATE your database as needed. Once the server is up and running, you can proceed to Postman for automated testing.



after you create the server now we can do some testing and verification on responses :arrow_right: http://localhost:3001

 ---
:pushpin: **STEP 1**: 
Establish a workspace and assign it any name you prefer, such as "MyAutomationAPI."
 
:arrow_right: now need to create a Collection and give a name like  APIPractice )

after you click on APIPractice you can see the Tab called "Variables" and click on it.

:pushpin: **STEP 2**: 
Under **VARIABLE**  column type →  ``` heroUrl ```

Then under **CURRENT VALUE** – > ```http://localhost:3000 ```

**INITIAL VALUE** → is the URL that you used to share it with others

see other type of variable : 

- **Global variable**

- **Collection variable**

- **Environment variable**

- **Data variable**

- **Local variable**
  
---
:pushpin: **STEP 3**:
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/6a41b55c-140c-41f7-9e93-cd4e2cfd4641)

our first request: <code> **GET  →** save then run it</code>

:pushpin: **STEP 4**:
Verification: Click on the **Test** tab → then on the right side you have some methods that you can pick
**Inside Test you need to type JS code**

Click on
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/21935791-c987-477c-84ac-787c41f18780)

**→ to verify status code**.

```javaScript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

**For checking other status codes: Just need to change that 200 inside the () to any other status code**

after clicking on "Send" gonna see under Test Results that shows a pass

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/1f21cea7-e898-49b0-8d5b-4c34514e9737)

:pushpin: **STEP 5**:
→ to verify headers:
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/2ac56a9f-69ee-4966-afd0-6d1df1f3e865)

```JavaScript
pm.test("Content-Type is present", function () {
    pm.response.to.have.header("Content-Type");
});
```

→ if you want to verify for example Date is present in the header just need to copy and paste same code and change instead “Content-type” chenge to “Date” then click Send

```JavaScript
pm.test("Date is present", function () {
    pm.response.to.have.header("Date");
});
```

#### Is not case sensitive instead Date you can type the date

Now want to verify content type is **application/json** now in the second line after “Content-Type” add a comma and type “application/json”
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/08d2f7ae-d1e5-462c-b339-9e34095afac6)

```JavaScript
pm.test("Content-Type is application/json", function () {
    pm.response.to.have.header("Content-Type","application/json; charset=utf-8");
});

```

Another thing wants to check header Transfer-Encoding is chunked:

```JavaScript
pm.test("Transfer-Encoding is chunked", function () {
    pm.response.to.have.header("Transfer-Encoding", "chunked");
});
```


Now you can see we have 5 Tests that all Pass :
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/e86465e6-8a32-4970-87e5-37e92b3a3e8a)


:pushpin: **STEP 6**:
For **POST HTTP Request**  : <code> POST: http://localhost:3000/addHero </code>
on the body tab Choose Jason Then add value then after sending  you're going to get a 201 Status code!
as you see in this example we added one json file to our database 

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/8979b115-dcf8-4643-b7dc-5521b8b5f35f)



Now go to the **Test** tab

Check status code

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/c05dd243-b382-42fe-93cf-c6823449955f)

Now from the right side click on Respond body: Json value check

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/16b8abf1-2925-43b4-a090-ab8644162ee3)

Now need to change in third line **value** to **msg** and **100** to **"Your hero successfully added to the database."**
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/da95b891-5de6-4129-96a5-82c1d8de93d2)


##Create Json object:
```javaScript
var jsonData = pm.response.json();
```
To print the name on the console:
```javaScript
console.log("Hero name: " +jsonData.data.name);
```
Also age and gender of specific ID:

```javaScript
console.log("Hero age: " +jsonData.data.age);
```
```javaScript
console.log("Hero gender: " +jsonData.data.gender);
```
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/60840449-e204-4f8e-b7f9-a87927be0753)

on the console, we can see the result :
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/c00f68e1-0ceb-44f8-9b3b-459917f54ce7)

:pushpin: **STEP 7**:
Click on the Collection that allows you to use PUT HTTP request, Right click and create a new request:<code> PUT:  http://localhost:3000/heros/:id</code>

Change the age number to something different from any user id then save your change and send get 204 status code
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/ee5dfe9c-2b2d-4262-bd2b-e075e9660511)

Now click on Test

Click on the status code and change it to 204

At this point, we need to capture the ID from the POST request

We going back to our POST request and Test tab need to save our **json data into global variable**

On the right side click on:
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/98fda85d-d1c1-46ae-bed0-68edff21edcf)

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/0dab2aa5-36ab-4238-be1b-889e6f49771b)

Then save it.

Now we go PUT request in Path Param and add id with global value 

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/19c4de15-adfc-4b2c-960b-d28b4ca223da)


and in the Body tab, we can change the age to a different value and save and run;

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/1cae6079-f68a-41f9-84db-2cbea599710a)


Now want to delete that Global variable that we create with post and edit it with Put:
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/88051914-c36e-4d24-ae00-bc8d4ddc31cc)

we can create another request to see if the delete works fine or not :
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/f2ff56e5-c5f0-4ad5-b1fd-08e4db8f0641)

On the Test tab check the status code and error message

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/31af0ded-6adc-4e79-a2e4-2b9afc7ea9e7)


We are using static **post Hero name** right now. We want to **get dynamic name** to **post** and **verify** that **name is posted.**

In order to **use random** **firstname** in **our post request**, we used <code> **{{$randomFirstName}} </code> in request body**.

But the **problem** is, that we **cannot verify** after we **post** the name in the **Tests field** in **Postman**.

**To overcome this problem.**

we used the **Pre-Request Script tab** from Postman.


**how can we use <code> {{$randomFirstName}} </code>in pre request script ?**

<code>var name = pm.variables.replaceIn('{{$randomFirstName}}');</code>

:arrow_right: we set HERO_NAME global variable from name variable

<code>pm.globals.set("SPARTAN_NAME", name);</code>

![image33](https://user-images.githubusercontent.com/69331074/234323124-df3c6a0f-737c-453e-b6cf-59825669a799.png)


![image29](https://user-images.githubusercontent.com/69331074/234323590-14de02b4-2b61-4fb6-a51e-a8ebaf4d6cce.png)


## ** :heavy_check_mark: FLOW :arrow_right: **

:heavy_check_mark: First Pre-Req Scrip

:heavy_check_mark: Then API Request

:heavy_check_mark: Then API Response

:heavy_check_mark: Last Test

:heavy_check_mark: Set global name
Then after the request and response are complete, under the Test tab, we read the Global variable HERO_NAME and assign it as an expectedName
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/85e73473-69ba-4a4c-b026-744a91277105)


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
