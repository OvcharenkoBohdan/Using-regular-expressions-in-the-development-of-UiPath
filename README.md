# Using regular expressions in the development of UiPath
This article describes how to use regular expression when developing processes.


Regular expression (regex) is a pattern (sequence of characters and metasymbols) which corresponds (or not) to the sequence of characters in the text. As a rule, regular expressions are used to specify the rule of searching for a sequence in the text.

The service was used to check the regular visions https://regex101.com/



## Places of use




Regular expressions can be used:

•	For the comparison of the corresponding values;

•	In selectors;

•	For changing the values;

•	Data retrieval;

These are the main ways of using regular expressions in UiPath. 
Let's proceed to the applications.

 ## Regular expressions to compare the corresponding values



Create a text file that contains the row. 
“Hello, my name is Bohdan Ovcharenko, I'm 20 years old”. 
Check if the developer has entered his age by means of regular expressions.
 

Create a process using the "is match" activity and the "Regex.IsMatch" method.
Let's create the changes:
<p>
  <img src="https://user-images.githubusercontent.com/75396764/143205664-8e60fa7b-6117-48ff-b617-2c6971f32076.png" height="100"/>
</p>
 

The process code looks like this:

<p>
  <img src="https://user-images.githubusercontent.com/75396764/143205731-de6ff50e-2ce8-41a0-8959-0b69f992cd8a.png" height="500"/>
</p>




Setting up the activity “Read Text File”.

<p>
  <img src="https://user-images.githubusercontent.com/75396764/143206115-a9b7cdb4-b039-49e5-bb1f-60652a04dd73.png" height="300"/>
</p>


 

Setting up the activity “Is Match”.

 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143206128-e3873e19-e41a-4239-827e-8f3bc7f125da.png" height="300"/>
</p>




We also carry out the operation of assignment through activity “Assign”.
 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143206161-753417af-f6d5-45f6-a518-85af1b0d248f.png" height="220"/>
</p>
 


The result is outputted through Boolean changes. Check the correctness of the search by running the process.

  <p>
  <img src="https://user-images.githubusercontent.com/75396764/143206169-a97d4a40-f531-45a7-8013-03dab8c0b4e4.png" height="100"/>
</p>
 


As we can see - we found the necessary data for us.

Let's conduct another test to check the presence of three digits with the help of the activity “Is Match”.

  <p>
  <img src="https://user-images.githubusercontent.com/75396764/143206204-c37ba88a-45b9-424c-95d8-ea18c6b3008a.png" height="100"/>
</p>


The result is unsuccessful, because there is no such text.

 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143206228-4eafe75e-fcde-4d94-8b7e-b00bd281b07c.png" height="100"/>
</p>



## Regular expressions in selectors



More theoretical information can be found here   About RegEx Search

In our case, we will write a process that will click on the LinkedIn link in Edge browser, but the name of the link can be 2 variants: 
1.	LinkedIn
 
 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143207581-79023395-9467-46be-8ea7-2d5868ac89b3.png" height="100"/>
</p>
 
2.	Linkedin
 
 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143207613-416c71df-0781-4b11-8565-46438813140a.png" height="90"/>
</p>



The selector will also be different.


  <p>
  <img src="https://user-images.githubusercontent.com/75396764/143207652-e57a85f9-cb3d-480a-a52a-62d9c67ea7f9.png" height="100"/>
</p>
  <p>
  <img src="https://user-images.githubusercontent.com/75396764/143207687-b4026730-1ead-43bb-938b-a69049fee429.png" height="80"/>
</p>


In this case it is necessary to prescribe possible changes by means of the structure :

matching:name='regex'

 
 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143207755-22100939-5154-40e4-ae5b-8b72c41e3639.png" height="90"/>
</p>


In this way we write down the letters that change.



## Regular expressions for changing the values



Symbol substitution is done using the method or the Replacе activity.

Let's take the application from 1 point and replace "IsMatch" with "Replace".
The arrangement of the "Replace" asset looks like this:

  <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208176-5779d66c-df47-4d11-9b36-216765815acd.png" height="300"/>
</p>


We replace the text after the first comma with "I am RPA Developer".
The output change must be STRING, in our case, we just overwrite the existing text.


As in the first point , you can use the operation of assignment, it looks like this:

  <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208258-220df30e-158e-45a8-b06c-6a8d449137e8.png" height="220"/>
</p>


Replace "Hello" with "Hi."

The code looks like this:

 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208318-9ba4aeb9-3599-4c1b-8e6d-fdd3ee55bdd6.png" height="500"/>
</p> 



After starting the process, we got the same result:

 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208411-487f2e44-0937-455f-80e4-a5cd2b29300c.png" height="100"/>
</p> 


## Regular expressions for data retrieval



You can extract individual values by using the "Match" method or the "Matches" asset.
Let's take the application from 1 point and replace "IsMatch" with "Matches".

Create a text file with the line "Hello, my name is Bohdan Ovcharenko, I QA Engineer".

The activity of Matches have the following appearance:

  <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208548-47de9503-7128-46df-88e0-2f2ef5cbb344.png" height="300"/>
</p> 


Since the output of this activity is a variable list, we use For each to output the data.


As in the first point, you can use the operation of assignment, it looks like this:

 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208631-257c8d25-fd39-44f5-a21f-3ce2561985b1.png" height="220"/>
</p> 


The code looks like this:

 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208711-6066f2ba-41f2-4c96-bc8b-773d409ed0dc.png" height="500"/>
</p> 


With the help of the "Matches" activity and the regular expression "QA.*" we "cut" everything from the text "QA" and after it.

And using the "Regex.Match" method and the regular phrase ".*(?=QA)" we "cut" everything that is before the text "QA".

We got the same result:

 <p>
  <img src="https://user-images.githubusercontent.com/75396764/143208783-49ccb764-83c9-4f5a-a212-b6dc23c7e09e.png" height="100"/>
</p> 

That's all!
Successful developments!




