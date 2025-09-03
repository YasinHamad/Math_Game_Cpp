# Math_Game_Cpp

## Brief Description
The purpose of this game is to practice programming basics. It is a math game. The program gives you math questions to answer.

## Table of Contents
- [Math\_Game\_Cpp](#math_game_cpp)
	- [Brief Description](#brief-description)
	- [Table of Contents](#table-of-contents)
	- [Introduction](#introduction)
	- [Tools used to build the project](#tools-used-to-build-the-project)
	- [Project Requirements](#project-requirements)
	- [High Level Explanation](#high-level-explanation)
	- [Low Level Explanation](#low-level-explanation)
		- [Enums](#enums)
		- [Structures](#structures)
		- [Functions](#functions)
	- [Things I learned](#things-i-learned)
	- [References and Links](#references-and-links)

## Introduction
I've built this game while studying programming basics at ProgrammingAdvices.com. You can find this project in Course[05]. It is the second project in that course. I'm grateful to this academy for teaching programming in a structured and practical way.

## Tools used to build the project
- Language: C++
- IDE: Visual Studio

## Project Requirements
1. To see the game in action, watch this video [Math_Game](https://youtu.be/b6-b7Sa6F5k).
2. Take from the user the number of questions they want to answer.
3. Take from the user the operation type they want to be tested in. [ '+' , '-' , '/' , 'x' , 'Mix' ]. When they choose Mix, you need to select a random operation for each question.
4. Take from the user the questions level. [ 'Easy' , 'Medium' , 'Hard' , 'Mix' ]. 
	- Easy -> the program generates numbers from 1-10.
	- Medium -> the program generates numbers from 11-30.
	- Hard -> the program generates numbers from 31-60.
	- Mix -> the program selects a random level for each question.
5. Start the questions. For each question print:
	- The number of the question out of the number of all questions like [1/3], this means, question one out of 3 questions.
	- The numbers and the operation related to this question.
	- All the above in a formatted way.
6. Take the user's answer and correct it.
	- If it's right, print "Right answer", and turn the font color green.
	- Otherwise print "Wrong answer", turn the font color red, and ring a bell sound.
7. At the end of the game print :
	- "You Pass" If ( right answers >= wrong answers ) and turn the font color green.
	- "You Fail" If ( right answers < wrong answers ) + turn the font color red + ring a bell.
	- Number of questions.
	- Questions level.
	- Number of right answers.
	- Number of wrong answers.
8. Ask the user if they want to play again, if they enter 'y' or 'Y':
	- Clear the screen.
	- Turn it black and white.
	- Restart the game.
9. End the program otherwise.

## High Level Explanation
The program begins by taking from the user the number of questions, the operation type, and the questions level. Then, it lets the user answer the questions one after another, corrects them, and prints the game results at the end.

## Low Level Explanation
The program follows the functional programming approach.

### Enums
1. **enResult**: Helps to determine whether the user's answer is correct.
2. **enPassFail**: Helps to determine whether the user passes the whole test. You can use a "bool is_pass" variable instead of using this enum.
3. **enQuestionsLevel**: Collects the levels we have in this game.
4. **enOperations**: Collects all operations in the game.

### Structures
1. **stRoundInfo**: Stores all the info about a question(round).
2. **`stGameInfo`**: Stores all the info about the game, like the operation type and questions level.

### Functions
1. **ReadPositiveNum**: Takes a message and keeps asking the user using this message until they enter a positive number.

2. **IsNumberInArray**: Takes an array and a number. It returns whether the number is in the array or not. 

3. **ReadOperation** and **ReadQuestionsLevel**: Keeps asking the user to enter one of the numbers showen on the screen, converts this number to enOperations(enQuestionsLevel) and returns it.

4. **ResetScreen**: Clears the screen and turns it to black and white.

5. **ChangeScreenStyle**: Takes an enResult variable  and changes the screen style based on it according to the point number 6 in the project requirements section.

6. **PrintTabs** and **PrintBreakLine**: `PrintBreakLine(3)` is easier than `cout << "\n\n\n";`

7. RandomNumber: Takes two numbers and uses rand() to return a number between these two numbers.

8. GetRandomOperation and **GetRandomQuestionsLevel**: Use function number 7 to return enOperations(enQuestionsLevel).

9. **GetRandomNumberBasedOnLevel**: Takes enQuestionsLevel and stRoundInfo variables. It makes a switch on the enQuestionsLevel variable and fills number_one and number_two with the appropriate values according to point number 4 in the project requirements section.

10. **CalculateRoundResult**: Takes stRoundInfo variable and makes a switch on the operation variable in it. It performs and saves in stRoundInfo.result the appropriate answer.

11. **SetOperationInRound**: Takes enOperations and stRoundInfo variable. It puts in stRoundInfo.operation the appropriate operation. If the enOperations variable is enOperations::mix_operation, it uses function number 8.1 to get a random operation.

12. **GetOperationAsString** and **GetQuestionLevelAsString**: These functions are responsible for returning the string version of an enOperations(enQuestionsLevel) variable.

13. **GetFinalResult**: This function is responsible for checking if the user answer is correct or not. It returns an enResult variable.

14. **AddElementToArray**: Takes an element and an array with its size(by reference). It increments the size by one and adds the element to it.

15. **ResetGameInfo**: This function is responsible for setting all the variables needed to restart the game to their default values.

16. **ReadGameInfo**: Takes an stGameInfo variable(by reference) and fills:
	- stGameInfo.number_of_rounds using function number 1.
	- stGameInfo.operation and stGameInfo.questions_level using funcions in number 3.

17. **PrintRoundBody**: This function is responsible for printing a question according to point number 5 in the project requirements section. It used functions number 6 and 12.

18. **PrintResultBody**: Prints the appropriate result on the screen according to point number 6 in the project requirements section. It uses function number 5 to change the screen style.

19. **play_a_round**: This function lets the user play a complete question. It uses functions (9, 11, 10, 17, 13, and 18).

20. **StartRounds**: This function is responsible for playing x questions based on the number of questions the user has chosen. It uses function number 14 to add each question the array we have (stGameInfo.rounds).

21. **CountNumberOfWinningTimes**: Takes an array and counts the number of right answers the user has in it.

22. **GetGameFinalResult**: Returns and enPassFail value based on points number 7.1 and 7.2 logic in the project requirements section.

23. **ChangeScreenToFinalStyle**: Changes the screen to the final style at the end of the game. It uses function number 5.

24. **PrintGameResultsHeader**: Prints the appropriate sentence according to points number 7.1 and 7.2 logic in the project requirements section.

25. **PrintGameResults**: Prints the game results at the end of the game according to point number 7 in the project requirements section. It uses functions (21, 22, 23, 24, and 12).

26. **StartGame**: This is the main function for this game. It makes a do-while to keep restarting the game when the user enters 'y' or 'Y'. It uses:
	- Function number 4 to reset the screen.
	- Function number ResetGameInfo to set the appropriate variables to their default values at the beginning of each time the user plays the game.
	- Function number 16 to read the game information from the user.
	- Function number 20 to let the user play and answer the questions.
	- Function number 24 to print the results. 

## Things I learned
1. If you have a lot of variables related to each other -> put them all in a structure.
2. In C++ you cannot use the same value in two different enums, like this (mix)
```c++
enum enQuestionsLevel {
	easy = 1, medium = 2, hard = 3, mix = 4
};

enum enOperations {
	add = 1, div_operation = 2, mul = 3, sub = 4, mix = 5
};
```
3. Having a lot of functions, structures and enums is good and makes things easier (of course when needed).
4. Be realistic and clear in function and variable names.

## References and Links
- [Academy website](#https://programmingadvices.com)
- [My video on YouTube about this game](#https://youtu.be/b6-b7Sa6F5k)
- My email : yasinhamadbusiness@gmail.com