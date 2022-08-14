You are tasked with writing a piece of software to do a token generation for cashless registration.
Your microservice should expose 2 different APIs
You must use the .Net core platform to develop the solution.
We really encourage you to bring up any specific questions you might have about it.
Requirements:
• The application must be executable both in Windows and Unix based machines;
• You don't have to worry about databases; it's fine to use in-process, in-memory storage;
• It must be production quality according to your understanding of it - tests, README, Swagger,
etc.
General notes:
• Feel free to expand your design in writing;
• You will submit the source code to git;
Things we're looking for:
• Immutability;
• Proper concurrency handling;
• Separation of concerns;
• Unit and integration tests;
• API design;
• Code readability;
• Error handling.

1 – API that receive customer card and save it on the db
Request information:
CustomerId - int
Card Number – long - max 16 characters
CVV – int - max 5 characters
Response information:
Registration date – Date now in UTC
Token – long – (Size of token may vary)
CardId - int
2 – API that validate that token based on data provided in the request
Request information:
CustomerId – int
CardId - int
Token – long – (Size of token may vary)
CVV – int - max 5 characters
Response information:
Validated – bool
Algorithm
The algorithm used to create the token is:
a) Get last 4 digits of card
b) Apply algorithm described below in Problem #1 and the number of rotations would be the
CVV number.
The algorithm to validate the token
1. If creation date of token is more than 30 min, return as not valid
2. Use the cardid to locate the card number
3. If customer is not the owner of the card, return as not valid
4. Print the card number in the console
5. Process the algorithm described above in creation process to create the token again and
compare with the token received in the request, if match return true otherwise false.



Problem #1
The operation called right circular rotation on an array of integers consists of moving the last array
element to the first position and shifting all remaining elements right one. Given an array of integers,
perform the rotation operation a number of times.
For each array, perform a number of right circular rotations and return this array.
For example, array a = [3, 4, 5], number of rotations k = 2.
First we perform the two rotations:
[3, 4, 5] ð [5, 3, 4] ð [4, 5, 3]
The result of that would be [4, 5, 3]
Explanation
Given the array [1, 2, 3] after the first rotation, the array becomes [3, 1, 2].
After the second (and final) rotation, the array becomes [2, 3, 1].
