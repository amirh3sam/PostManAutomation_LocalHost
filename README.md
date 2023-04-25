PostMan Automation 1
PostMan Automation
PostMan Automation
1- create workspace
then name it : MyAutomationWorkSpace
Test Tab → verify response
So we set our URL in Collection Level(Spartan folder)
You are in Spartan Collection click on Variavles tab
Under VARIABLE → sUrl
Then CURRENT VALUE – > YourIpAddress
INTIAL VALUE → is the url that you used to shared it with others
Global variable
Collection variable
Environment variable
Data variable
Local variable
Start one request: GET {{sUrl}}/api/spartans → save then run it
Click on Test tab → on the right side you have method than you can choose
PostMan Automation 2
Inside Test you need to type JS code
Click on
→ to verify status code
Just need to change that 200 inside the () then your code will test other Status code
Then run gonna see under Test Results shows pass
→ to verify headers
→ if you want to verify for example Date is present in the header just need to copy and
past same code and change instead “Content-type” chenge to “Date” then click Send
Is not case sensitive instead Date you can type date
PostMan Automation 3
Now want to verify content type is application/json now in second line after “ContentType” add comma and type “applicaiton/json”
Another thing want to check header Transfer-Encdoing is chunked:
Under Spartans right click create POST {{sUrl}}/api/spartans
Under body Choose jason Then add value then send get 201 Status code
Now go to Test tab
Check status code
Now from right click on Respond body: Json value check
PostMan Automation 4
Now need to change in third line value to success and 100 to “A Spartan is Born!”
If want to get a name just copy and past same code then change it like this
Create Json object:
Var jsonData = pm.response.json();
To print name on console:
console.log(“Spartan name: “ +jsonData.data.name);
And this is a out put:
PostMan Automation 5
Click on Spartan Colloction right click and create new request : PUT
/{{sUrl}}/api/spartans/:id
And change the phone number to all 1111111111 save your change and send get 204
status code
Now click on Test
Click on status code and change it 204
At this point we need to capture the id from POST request
We going back on our POST request and on Test tab need to save our jsondata into
global variable
On the right side click on
Then save it
PostMan Automation 6
Now we go PUT request and add id with value {{SPARTAN_ID}}
Now want to create DELET /{{sUrl}}/api/spartans/:id
Create GET / {{sUrl}}/api/ Spartans/:id to check that id does not exist
On Test tab check the status code and error massage
PostMan Automation 7
We are using static post spartan name right now. We want to get dynamic name to
post and verify that name is posted.
In order to use random firstname in our post request, we used
{{$randomFirstName}} in request body.
But the problem is, we cannot verify after we post the name in Tests field in
Postman.
To overcome this problem.
we used Pre-Request Script tab from postman.
how can we use {{$randomFirstName}} in preq request script ?
var name = pm.variables.replaceIn('{{$randomFirstName}}');
//we set SPARTAN_NAME global variable from name variable
pm.globals.set("SPARTAN_NAME", name);
PostMan Automation 8
FLOW—>
First Pre-Req Scrip
Then API Request
Then API Response
Last Test
Set global name
Then after request and response complete, under Test tab, we read the Global variable
SPARTAN_NAME and assign as an expectedName
PostMan Automation 9
RUN Collection
You can run whole collection here also can give schedules run
Or manually run or give number of Iterations → how many time
You want to run it or delay or if you have external data like
Excel file you can choose Data and click Run spartan
PostMan Automation 10
See all result details after you run it.
DDT:
SO IN THIS FLOW, WE USED RANDOM VARIABLE WITH SAVING AND REUSING IT.
CAN WE USE POSTMAN AUTOMATION WITH EXTERNAL DATA/FILE
I want to use my .csv file to automate Spartan Flow
Make copy of your Spartans folder and name it Spartan DDT
I have my csv file on my desktop
Need to get the URL from Spartans :YourIpAddress
And add it to SpartanDDT
We create one .csv file where we have name, gender and phone fields.
Then our POST REQUEST BODY we use those field names with {{}}
{
"gender":"{{gender}}",
"name":"{{name}}",
"phone":{{phone}}
}
Remove variable name in Pre-request because in this case we do not need it delete
everything on the Post → Pre-request
Under Test tab remove global name
Now need to add expectedName like this:
You can remove the log part too(print json response and print something on the
console)
PostMan Automation 11
Keep the ID!
when we execute through Collection Runner, there is an option to pick file, we just need
to click select file and pick our .csv file.
And click Run Spartan DDT
if the column names and variable names are matching, postman will provide those
information.
To access to same information for each iternation dynamically in the Tests tab, we used
following code
var expectedName = pm.iterationData.get("name"); --> this parameter needs to match
from csv column name again.
We want to have different Enviroment
Click on right side menu bar on Enviroments
Then click on creat Enviroments
And name it QA1
Now we have to define different Enviroments start with :
baseUrl type it under VARIABLE and add https://api.qa.bookit.cydeo.com under
CURRENT VALUE
Next VARIABLE is tearcher_email and the CURRENT VALUE is blyst6@si.edu
teacher_password is barbabaslyst
If you want to password invisible change type to secret
Next
leader_email is lfinnisz@yolasite.com and leader_passeword is lissiefinnis
Then right click on QA1 and choose Duplicate
Change name to QA2
PostMan Automation 12
Now we change only the values
baseUrl is https://api.qa2.bookit.cydeo.com
tearcher_email is teacherilsamnickel@gmail.com
teacher_password is samnickel
teader_email is daldie7l@seattletimes.com
leader_passeword is ruthannjohnes
Creat new collection and called it Bookit And add new request
Name : GET /leader token
Next from top right where said no environment pick QA1 now when you try do your
request after GET type {{baseUrl}} gonna see green that comes from Enviroment QA1
GET {{baseUrl}}/sign and add email and password
Eamil is {{leader_email}}
Password is {{leader_password}}
If right now just change the QA1 to QA2 and send it again you gonna get a new token
from Enviroment QA2
In Test tab want to check status code and get a token and save as an leader Token
env variable.
PostMan Automation 13
From right side click on status code and click on Respond body : Json value check
Then we delete first line and third line and only keep the
var jsonData = pm.response.json();
And add
console.log(jsonData.accessToken);
Add this to var → var accessToken = jsonData.accessToken;
After we print Token I need to add it in to my Enviroment Variable
click on Set an envriment variable
So you gonna see this :
pm.environment.set(“leaderToken”, accessToken);
After run goona see it on your environment QA1 and QA2
Then right click on Bookit and create another request
GET → {{baseUrl}}//api/users/me
Click on Authorization and Token → type → {{leaderToke}}
PostMan Automation 14
DDT with schedule after click on Run collection from
Spartan collection
On there
Schedule configuration
give name like SMOKE TEST EVERY DAY at 8:00AM and can choose Environment
like QA1 and Click Schudel Run
PostMan Automation 15
Another way to run the collection is choose by Automate runs via CLI
Run on postman CLI need to install :
https://go.pstmn.io/install-cli-win64
PostMan Automation 16
then with command line deponds on your operation system and how is work by type
code on command line can execute test. Copy past the API key on command line and
run!
Or
Run on CI/CD pipe line
You can pick Jenkins and run it !
https://learning.postman.com/docs/collections/using-newman-cli/integration-withjenkins/
Now want to do Schema
Get {{sUrl}}/api/spartans
Test tab type :
Var Schema = {add your schema all json objects here};
PostMan Automation 17
After that type:
Var response= JSON.parse(responseBody);
Tests[“schema is Valid”] = tv4.validate(response,schema);
console.log(tv4.error);
Then Send should get 200 Status code
If some one ask you how to validate schema you can tell with tv4.validate library .
