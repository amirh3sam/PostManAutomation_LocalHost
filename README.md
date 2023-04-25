# PostMan Automation

**PostMan Automation**

**1- create workspace**

then name it : MyAutomationWorkSpace

**Test Tab →** verify response

So we set our URL in Collection Level(Spartan folder)

You are in Spartan Collection click on Variavles tab

Under **VARIABLE** → sUrl

Then **CURRENT VALUE** – > YourIpAddress

**INTIAL VALUE** → is the url that you used to shared it with others

**Global variable**

**Collection variable**

**Environment variable**

**Data variable**

**Local variable**

Start one request: **GET {{sUrl}}/api/spartans →** save then run it

Click on **Test** tab → on the right side you have method than you can choose

Inside Test you need to type JS code

![image35](https://user-images.githubusercontent.com/69331074/234320102-de0e7c3e-3402-4574-8072-e4cfdb2bbf68.png)

Click on

**→ to verify status code**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/61a8b0b5-a0d9-4b81-8ead-d4b2fae23f3b/image12.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/61a8b0b5-a0d9-4b81-8ead-d4b2fae23f3b/image12.png)

Just need to change that 200 inside the () then your code will test other Status code

Then run gonna see under Test Results shows pass

→ to verify headers

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4cf88b18-9abd-4628-ae3a-d990186705b6/image9.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4cf88b18-9abd-4628-ae3a-d990186705b6/image9.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ce5915c-5ddd-4e08-821a-800459ac3218/image32.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ce5915c-5ddd-4e08-821a-800459ac3218/image32.png)

→ if you want to verify for example Date is present in the header just need to copy and past same code and change instead “Content-type” chenge to “Date” then click Send

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/35253a18-1d00-4763-99fc-d61740f15775/image21.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/35253a18-1d00-4763-99fc-d61740f15775/image21.png)

Is not case sensitive instead Date you can type date

Now want to verify content type is application/json now in second line after “Content-Type” add comma and type “applicaiton/json”

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/30f33052-f089-44b4-8d76-25b47544940f/image5.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/30f33052-f089-44b4-8d76-25b47544940f/image5.png)

Another thing want to check header Transfer-Encdoing is chunked:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/28d0ca90-d758-4124-a7ac-59d5c3a95889/image18.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/28d0ca90-d758-4124-a7ac-59d5c3a95889/image18.png)

Under Spartans right click create POST {{sUrl}}/api/spartans

Under body Choose jason Then add value then send get 201 Status code

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37529758-4e0c-4fcb-a9cc-e0eb1a118fa1/image24.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37529758-4e0c-4fcb-a9cc-e0eb1a118fa1/image24.png)

Now go to **Test** tab

Check status code

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc68abfe-4e38-4115-9fa6-20411af4ab3d/image8.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc68abfe-4e38-4115-9fa6-20411af4ab3d/image8.png)

Now from right click on Respond body: Json value check

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/256c1d16-16ec-4dd1-9852-e7c5155662da/image6.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/256c1d16-16ec-4dd1-9852-e7c5155662da/image6.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d50469b-1455-4295-8e21-79e8ed2c1f93/image27.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d50469b-1455-4295-8e21-79e8ed2c1f93/image27.png)

Now need to change in third line **value** to **success** and **100** to **“A Spartan is Born!”**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6ff0db4-8e00-457d-bcda-7d4a53df1fe1/image13.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6ff0db4-8e00-457d-bcda-7d4a53df1fe1/image13.png)

If want to get a name just copy and past same code then change it like this

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b8b5bb6b-c249-46ea-9a96-79abcfb4d15c/image31.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b8b5bb6b-c249-46ea-9a96-79abcfb4d15c/image31.png)

**Create Json object:**

Var jsonData = pm.response.json();

**To print name on console:**

console.log(“Spartan name: “ +jsonData.data.name);

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bed43901-6de3-489a-975e-c7f9108c9e00/image25.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bed43901-6de3-489a-975e-c7f9108c9e00/image25.png)

And this is a out put:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d711b45-e86b-4670-be09-1d057e8b32fe/image17.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d711b45-e86b-4670-be09-1d057e8b32fe/image17.png)

Click on Spartan Colloction right click and create new request : PUT /{{sUrl}}/api/spartans/:id

And change the phone number to all 1111111111 save your change and send get 204 status code

Now click on Test

Click on status code and change it 204

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5893d9bb-6c6e-4b9d-aa09-a0ca06a9e52f/image4.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5893d9bb-6c6e-4b9d-aa09-a0ca06a9e52f/image4.png)

At this point we need to capture the id from POST request

We going back on our POST request and on Test tab need to save our jsondata into global variable

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0a05e0df-ee72-47ef-9fd7-57719aca5ea7/image28.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0a05e0df-ee72-47ef-9fd7-57719aca5ea7/image28.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6defecb-66ac-47d9-9718-34b6f32b9de5/image16.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6defecb-66ac-47d9-9718-34b6f32b9de5/image16.png)

On the right side click on

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/77e0077a-8e03-4054-ae4f-110b47a82678/image34.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/77e0077a-8e03-4054-ae4f-110b47a82678/image34.png)

Then save it

Now we go PUT request and add id with value {{SPARTAN_ID}}

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d84b484a-a490-4427-aa7e-5b86ba4161fe/image3.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d84b484a-a490-4427-aa7e-5b86ba4161fe/image3.png)

Now want to create DELET /{{sUrl}}/api/spartans/:id

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1f8b3cc0-bdbf-4900-a838-4a65eb51daf0/image23.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1f8b3cc0-bdbf-4900-a838-4a65eb51daf0/image23.png)

Create GET / {{sUrl}}/api/ Spartans/:id to check that id does not exist

On Test tab check the status code and error massage

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a8a25416-97b7-40e9-9c92-fcd157922fde/image11.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a8a25416-97b7-40e9-9c92-fcd157922fde/image11.png)

We are using static **post spartan name** right now. We want to **get dynamic name** to **post** and **verify** that **name is posted.**

In order to **use random** **firstname** in **our post request**, we used **{{$randomFirstName}} in request body**.

But the **problem** is, we **cannot verify** after we **post** the name in **Tests field** in **Postman**.

**To overcome this problem.**

we used **Pre-Request Script tab** from postman.

**how can we use {{$randomFirstName}} in preq request script ?**

var name = pm.variables.replaceIn('{{$randomFirstName}}');

//we set SPARTAN_NAME global variable from name variable

pm.globals.set("SPARTAN_NAME", name);

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c33c7fa-b14a-49e2-91bf-d7cdd8cd944f/image33.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c33c7fa-b14a-49e2-91bf-d7cdd8cd944f/image33.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60114900-66b7-4b9e-a3df-66c8a1558aed/image29.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60114900-66b7-4b9e-a3df-66c8a1558aed/image29.png)

## **FLOW—>**

First Pre-Req Scrip

Then API Request

Then API Response

Last Test

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/214aa104-2eb2-4c0b-ab9d-87b3ff153df9/image26.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/214aa104-2eb2-4c0b-ab9d-87b3ff153df9/image26.png)

Set global name

Then after request and response complete, under Test tab, we read the Global variable SPARTAN_NAME and assign as an expectedName

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f16f42d6-4d36-4fca-8b3c-c6ab46b68c6a/image2.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f16f42d6-4d36-4fca-8b3c-c6ab46b68c6a/image2.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3c9626a2-fce6-4099-b9bf-47396ae669bc/image30.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3c9626a2-fce6-4099-b9bf-47396ae669bc/image30.png)

## RUN Collection

You can run whole collection here also can give schedules run

Or manually run or give number of Iterations → how many time

You want to run it or delay or if you have external data like

Excel file you can choose Data and click Run spartan

See all result details after you run it.

DDT:

SO IN THIS FLOW, WE USED RANDOM VARIABLE WITH SAVING AND REUSING IT.

CAN WE USE POSTMAN AUTOMATION WITH EXTERNAL DATA/FILE

**I want to use my .csv file to automate Spartan Flow**

Make copy of your Spartans folder and name it **Spartan DDT**

**I have my csv file on my desktop**

**Need to get the URL from Spartans :**YourIpAddress

**And add it to SpartanDDT**

We create one .csv file where we have name, gender and phone fields.

Then our **POST REQUEST BODY** we use **those field names** with **{{}}**

{

"gender":"{{gender}}",

"name":"{{name}}",

"phone":{{phone}}

}

**Remove variable name** in **Pre-request** because in this case we do not need it delete everything on the Post → Pre-request

Under **Test** tab **remove** global name

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d320f653-9bc9-41eb-af5c-acbc3f8a1be2/image15.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d320f653-9bc9-41eb-af5c-acbc3f8a1be2/image15.png)

Now need to add expectedName like this:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d2de7061-1359-4360-acfb-7f7f5e4648d6/image1.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d2de7061-1359-4360-acfb-7f7f5e4648d6/image1.png)

You can remove the log part too(print json response and print something on the console)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/318c3a53-58cd-4f24-a322-51677f99ee34/image36.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/318c3a53-58cd-4f24-a322-51677f99ee34/image36.png)

Keep the ID!

when we execute through Collection Runner, there is an option to pick file, we just need to click select file and pick our .csv file.

**And click Run Spartan DDT**

if the column names and variable names are matching, postman will provide those information.

To access to same information for each iternation dynamically in the Tests tab, we used following code

var expectedName = pm.iterationData.get("name"); --> this parameter needs to match from csv column name again.

We want to have **different Enviroment**

Click on right side menu bar on **Enviroments**

**Then click on creat Enviroments**

And name it **QA1**

**Now we have to define different Enviroments start with :**

**baseUrl** type it under VARIABLE and add [https://api.qa.bookit.cydeo.com](https://api.qa.bookit.cydeo.com/) under **CURRENT VALUE**

Next **VARIABLE** is **tearcher_email** and the **CURRENT VALUE** is **[blyst6@si.edu](mailto:blyst6@si.edu)**

**teacher_password** is **barbabaslyst**

**If you want to password invisible change type to secret**

**Next**

**leader_email is lfinnisz@yolasite.com and leader_passeword is lissiefinnis**

**Then right click on QA1 and choose Duplicate**

**Change name to QA2**

**Now we change only the values**

**baseUrl** is [https://api.qa2.bookit.cydeo.com](https://api.qa.bookit.cydeo.com/)

**tearcher_email** is **teacherilsamnickel@gmail.com**

**teacher_password** is **samnickel**

**teader_email** is **daldie7l@seattletimes.com**

**leader_passeword** is **ruthannjohnes**

**Creat** new **collection** and called it **Bookit** And add **new request**

**Name : GET /leader token**

Next from top right where said no environment pick **QA1 now** when you try do your request after GET type {{baseUrl}} gonna see green that comes from Enviroment QA1

**GET {{baseUrl}}/sign** and add **email** and **password**

**Eamil is {{leader_email}}**

**Password is {{leader_password}}**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e414b4d2-10ac-4aea-a750-d81968ce33f4/image7.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e414b4d2-10ac-4aea-a750-d81968ce33f4/image7.png)

If right now just change the QA1 to QA2 and send it again you gonna get a new token from Enviroment QA2

In **Test** tab want to check **status code** and **get a token** and save as an leader Token env variable.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd060a14-f9e1-434e-b454-2a0e5e8b928b/image10.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd060a14-f9e1-434e-b454-2a0e5e8b928b/image10.png)

From right side click on status code and click on Respond body : Json value check

Then we delete first line and third line and only keep the

**var jsonData = pm.response.json();**

**And add**

**console.log(jsonData.accessToken);**

**Add this to var → var accessToken = jsonData.accessToken;**

**After we print Token I need to add it in to my Enviroment Variable**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9eef41b8-0603-447e-8375-4a51efc0e72e/image22.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9eef41b8-0603-447e-8375-4a51efc0e72e/image22.png)

click on Set an envriment variable

So you gonna see this :

**pm.environment.set(“leaderToken”, accessToken);**

After run goona see it on your environment QA1 and QA2

Then right click on Bookit and create another request

**GET → {{baseUrl}}//api/users/me**

**Click on Authorization and Token → type → {{leaderToke}}**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6d919c83-ea6f-41de-976f-aeb39480721a/image20.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6d919c83-ea6f-41de-976f-aeb39480721a/image20.png)

## **DDT** with **schedule** **after click** on **Run collection** from **Spartan collection**

On there

**Schedule configuration**

give **name** like **SMOKE TEST EVERY DAY** at **8:00AM** and can choose **Environment** like **QA1** and Click **Schudel Run**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d1cbb0e1-1bd0-4918-94b8-445ffd801a2e/image38.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d1cbb0e1-1bd0-4918-94b8-445ffd801a2e/image38.png)

Another way to run the collection is choose by Automate runs **via CLI**

Run on postman CLI need to install :

[https://go.pstmn.io/install-cli-win64](https://go.pstmn.io/install-cli-win64)

then with command line deponds on your operation system and how is work by type code on command line can execute test. Copy past the API key on command line and run!

**Or**

## **Run on CI/CD pipe line**

**You can pick Jenkins and run it !**

**[https://learning.postman.com/docs/collections/using-newman-cli/integration-with-jenkins/](https://learning.postman.com/docs/collections/using-newman-cli/integration-with-jenkins/)**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e5ecfeff-ab02-422b-83ae-36cf41a20945/image37.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e5ecfeff-ab02-422b-83ae-36cf41a20945/image37.png)

**Now want to do Schema**

**Get {{sUrl}}/api/spartans**

**Test tab type :**

**Var Schema = {add your schema all json objects here};**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b6fe50f-7f20-48fb-a2a0-34f02f4ca793/image19.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b6fe50f-7f20-48fb-a2a0-34f02f4ca793/image19.png)

After that type:

**Var response= JSON.parse(responseBody);**

**Tests[“schema is Valid”] = tv4.validate(response,schema);**

**console.log(tv4.error);**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/087c05e4-5a52-43ca-b954-81a4734b2fc0/image14.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/087c05e4-5a52-43ca-b954-81a4734b2fc0/image14.png)

**Then Send should get 200 Status code**

If some one ask you how to validate schema you can tell with tv4.validate library .
