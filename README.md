# Using-regular-expressions-in-the-development-of-UiPath
This article describes how to use regular expression when developing processes.

Using regular expressions in the development of UiPath

This article describes how to use regular expression when developing processes.

Regular expression (regex) is a pattern (sequence of characters and metasymbols) which corresponds (or not) to the sequence of characters in the text. As a rule, regular expressions are used to specify the rule of searching for a sequence in the text.

The service was used to check the regular visions https://regex101.com/

Places of use

Regular expressions can be used:
•	For the comparison of the corresponding values;
•	In selectors;
•	For changing the values;
•	Data retrieval;

These are the main ways of using regular expressions in UiPath. 
Let's proceed to the applications.


Regular expressions to compare the corresponding values

Create a text file that contains the row. 
“Hello, my name is Bohdan Ovcharenko, I'm 20 years old”. 
Check if the developer has entered his age by means of regular expressions.
 

Create a process using the "is match" activity and the "Regex.IsMatch" method.
Let's create the changes:

![image](https://user-images.githubusercontent.com/75396764/143205664-8e60fa7b-6117-48ff-b617-2c6971f32076.png)
 

The process code looks like this:

![image](https://user-images.githubusercontent.com/75396764/143205731-de6ff50e-2ce8-41a0-8959-0b69f992cd8a.png)





















Setting up the activity “Read Text File”.

 

Setting up the activity “Is Match”.

 






We also carry out the operation of assignment through activity “Assign”.

 

The result is outputted through Boolean changes. Check the correctness of the search by running the process.
 

As we can see - we found the necessary data for us.













Let's conduct another test to check the presence of three digits with the help of the activity “Is Match”.

 

The result is unsuccessful, because there is no such text.

 














Regular expressions In selectors

More theoretical information can be found here   About RegEx Search

In our case, we will write a process that will click on the LinkedIn link in Edge browser, but the name of the link can be 2 variants: 
1.	LinkedIn
 
2.	Linkedin
 


The selector will also be different.

 
 


In this case it is necessary to prescribe possible changes by means of the structure :

matching:name='regex'

 


In this way we write down the letters that change.
































Regular expressions for changing the values

Symbol substitution is done using the method or the Replacе activity.

Let's take the application from 1 point and replace "IsMatch" with "Replace".
The arrangement of the "Replace" asset looks like this:

 


We replace the text after the first comma with "I am RPA Developer".
The output change must be STRING, in our case, we just overwrite the existing text.












As in the first point , you can use the operation of assignment, it looks like this:

 

Replace "Hello" with "Hi."

The code looks like this:

 



After starting the process, we got the same result:

 








































Regular expressions for data retrieval

You can extract individual values by using the "Match" method or the "Matches" asset.
Let's take the application from 1 point and replace "IsMatch" with "Matches".

Create a text file with the line "Hello, my name is Bohdan Ovcharenko, I QA Engineer".

The activity of Matches have the following appearance:

 

Since the output of this activity is a variable list, we use For each to output the data.












As in the first point, you can use the operation of assignment, it looks like this:

 

The code looks like this:

 

With the help of the "Matches" activity and the regular expression "QA.*" we "cut" everything from the text "QA" and after it.

And using the "Regex.Match" method and the regular phrase ".*(?=QA)" we "cut" everything that is before the text "QA".

We got the same result:

 

That's all!
Successful developments!




