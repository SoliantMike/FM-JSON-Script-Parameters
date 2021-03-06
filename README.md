FM-JSON Script Parameters
=========================

Passing Script Parameters Using the While function and JSON

The While function, introduced in FileMaker 18, makes it easy to perform looping operations in FileMaker calculations without having to create complicated recursive custom functions. It is also more performant and efficient than recursive custom functions. I have found it to be very handy for passing script parameters when writing FileMaker scripts. This helps for consolidating several similar scripts into a single script, which allows me to try to normalize scripting logic.

JSON (Javascript Object Notation) makes a lot of sense to use for Script Parameters, due to its readability and portability. This example builds off a technique shown here (https://www.soliantconsulting.com/blog/auto-create-variable-json-filemaker/) for automatically defining local variables for use in a script, based on some JSON that you feed into it. 

If you are not familiar with FileMaker’s JSON functions, they are very easy to use. Using the JSONSetElement function takes care of properly forming and escaping any JSON we produce. There is a very handy way of writing out this function in the calculation dialog, to make it very easy to add or delete elements as needed.

JSONSetElement ( "" <br />
 ; [ "action" ; "build" ; JSONString ]<br />
 ; [ "id" ; $id ; JSONString ]<br />
)

Note that each line with square brackets can be copied and pasted to add another element. The square brackets allow for additional parameters assigned in this FileMaker function. Even if you only have one element to define, the square brackets will work. There are several FileMaker functions that behave this way, like the Substitute function.

In the above example, the resulting variables that get set will look like the following:

$_action = build<br />
$_id = 123456890

Now, any time you need to pass a script parameter when calling a script, all you need to do is feed it JSON as a parameter. Then in your script, call the custom function in an If script step. If there was any evaluation error, it will return a non-zero result that evaluates as true, where you can show a custom dialog and exit the script if you wish. Otherwise, a zero result equates to false, where you can continue in your script. 

You can also pass JSON Objects and Arrays as parameters. Passing in an Object allows you to easily create three dimensional arrays of data and makes them easy to consume.

The custom functions used can be downloaded here<br />
https://github.com/SoliantMike/FM_Custom-Functions/blob/master/JsonToVars.txt<br />
https://github.com/SoliantMike/FM_Custom-Functions/blob/master/GetErrorDesc_en.txt


Read more here: <a href="https://www.soliantconsulting.com/blog/filemaker-while-function/">https://www.soliantconsulting.com/blog/filemaker-while-function/</a>

