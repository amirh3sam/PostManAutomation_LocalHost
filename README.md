
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/9e109094-70c0-430f-93c7-288187c27cad)

## :heavy_check_mark: **PostMan Automation**

To set up a free server effortlessly, you can generate the server by executing a few lines of code in the command prompt. To learn how to create your local server for testing HTTP API requests, visit this GitHub page [The GitHub Page](https://github.com/MRSamBadiei) or you can download it here [Download zip file HERE](https://github.com/amirh3sam/Post-Man-Automation/files/13933170/nodejs-api-server_lastUPdate.zip) , after you download the zip file extract it to desktop after open the folder rightclick somewhere and choose open in Terminal then type ```npm i``` Enter Then Type ```npm run dev``` Enter wait to see on Green that Running mean server is ready :) 

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/fc73b8c6-0b5c-4fe3-ac20-f8f131f19057)

With this server, you can conduct tests involving ```GET, POST, PUT, PATCH, and DELETE``` methods on data  ```name, gender, age```. Begin by establishing a database on your local host to assess GET and POST operations for data creation. You can also utilize this server to DELETE or UPDATE your database as needed. Once the server is up and running, you can proceed to Postman for automated testing.



after you create the server now we can do some testing and verification on responses :arrow_right: http://localhost:3000

if for a reason your 3000 PORT was used by another project, you can easily change that PORT to 3001 or any open port, to do that you need to open the Project and on package.json there is a dev object change that PORT=3001 and save and run again!
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/308fedf7-8ea7-4425-bcf3-7f7d7af8b66b)


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

<code>pm.globals.set("HERO_NAME",name);</code>

![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/b81c3309-6c87-467a-87f7-95832f291366)


!![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/d7a21876-667c-409d-9fa8-70b6eed5aa3d)



## ** :heavy_check_mark: Lets Summmery the FLOW :arrow_right: **

:heavy_check_mark: First Pre-Req Scrip

:heavy_check_mark: Then API Request

:heavy_check_mark: Then API Response

:heavy_check_mark: Last Test

:heavy_check_mark: Set global name
Then after the request and response are complete, under the Test tab, we read the Global variable HERO_NAME and assign it as an expectedName
![image](https://github.com/amirh3sam/Post-Man-Automation/assets/69331074/85e73473-69ba-4a4c-b026-744a91277105)


Run on postman CLI need to install :

[https://go.pstmn.io/install-cli-win64](https://go.pstmn.io/install-cli-win64)

then with command line depends on your operation system and how it works Typing code on the command line can execute tests. Copy past the API key on the command line and run!

**Or**

## :heavy_check_mark: Run on CI/CD pipeline

**You can pick Jenkins and run it !**

**[https://learning.postman.com/docs/collections/using-newman-cli/integration-with-jenkins/](https://learning.postman.com/docs/collections/using-newman-cli/integration-with-jenkins/)**

![image37](https://user-images.githubusercontent.com/69331074/234323956-2396bca1-442e-4595-9728-9c25a432fa62.png)


I hope you guys enjoying this Topic, Good luck!!✌️

