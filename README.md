Download Link: https://assignmentchef.com/product/solved-us-crime-solved
<br>
This assignment demonstrates your understanding of the concepts from the CMIS 141 class.

Before attempting this project, be sure you have completed all of the reading assignments, hands-on labs, discussions, and assignments to date.

Design a Java application that will read a file containing data related to the US. Crime statistics from 1994-2013. The description of the file is at the end of this file. The application should provide statistical results on the data including:

a. Population growth in percentages from each consecutive year (e.g. 1994-1995 calculation is ((262803276 – 260327021)/260327021)*100 = 0.9512%, 1995-1996 would be ((265228572 – 262803276)/262803276)*100 = 0.9229%)

b. Years where the maximum and minimum Murder rates occurred.

c. Years where the maximum and minimum Robbery rates occurred.

The following are some design criteria and specific requirements that need to be addressed:

a. Use command line arguments to send in the name of the US Crime Data file.

b. You should also use Java classes to their full extent to include multiple methods and at least two classes

c. You are not allowed to modify the Crime.csv Statistic data file included in this assignment.

d. Use arrays and Java classes to store the data. (Hint: You can and should create a USCrimeClass to store the fields. You can also have an Array of US Crime Objects.)

e. You should create separate methods for each of the required functionality. (e.g. getMaxMurderYear() will return the Year where the Murder rate was highest. )

f. A user-friendly and well-organized menu should be used for users to select which data to return. A sample menu is shown in run example. You are free to enhance your design and you should add additional menu items and functionality.

g. The menu system should be displayed at the command prompt, and continue to redisplay after results are returned or until Q is selected. If a user enters an invalid menu item, the system should redisplay the menu with a prompt asking them to enter a valid menu selection

h. The application should keep track of the elapsed time (in seconds) between once the application starts and when the user quits the program. After the program is exited, the application should provide a prompt thanking the user for trying the US Crime Statistics program and providing the total time elapsed.

i. Hint: When reading the Crimes file, read one line at a time (See ReadEmail.java) and then within the loop parse each line into the USCrimeClass fields and then store that USCrimeClass Object into an array. Note you can use String.split(“,”) to split the CSV line into a the fields for setting the USCrimeClass Object.

Here is sample run:

java TestUSCrime Crime.csv 2

********** Welcome to the US Crime Statistical Application **************************

Enter the number of the question you want answered. Enter ‘Q’ to quit the program :

1. What were the percentages in population growth for each consecutive year from 1994 – 2013?

2. What year was the Murder rate the highest?

3. What year was the Murder rate the lowest?

4. What year was the Robbery rate the highest?

5. What year was the Robbery rate the lowest?

Q. Quit the program

Enter your selection: 2

The Murder rate was highest in 1994

Enter the number of the question you want answered. Enter ‘Q’ to quit the program :

1. What were the percentages in population growth for each consecutive year from 1994 – 2013?

2. What year was the Murder rate the highest?

3. What year was the Murder rate the lowest?

4. What year was the Robbery rate the highest?

5. What year was the Robbery rate the lowest?

Q. Quit the program

Enter your selection: 5

The Robbery rate was lowest in 2013

Enter the number of the question you want answered. Enter ‘Q’ to quit the program :

1. What were the percentages in population growth for each consecutive year from 1994 – 2013?

2. What year was the Murder rate the highest?

3. What year was the Murder rate the lowest?

4. What year was the Robbery rate the highest?

5. What year was the Robbery rate the lowest?

Q. Quit the program

Enter your selection: Q

Thank you for trying the US Crimes Statistics Program

<strong>I have a code for the assignment. But is has error in code lines. How can I fix it I have tried but it keeps redflagging “crimeinfo”. I don’t know how to fix the red line errors int it.</strong>

<strong>Any help on how to fix this code?? </strong>

<strong>It is final exam</strong>

<strong>This is the test case code it will not let me attach</strong>

//import java.util, java.time, java.io

import java.util.*;

import java.time.*;

import java.io.*;

public class Testcasecrime {

/**

* @param args the command line arguments

*/

public static void main(String[] args) {

//Time counting starts

Instant start = Instant.now();

//greeting user

System.out.println(“n***************************************************”);

System.out.println(“***** Welcome to US Crimes Statistics Program *****”);

//construct needed io and util

Scanner scannerIn = null;

BufferedReader inputStream = null;

BufferedWriter outputStream = null;

FileInputStream in = null;

try {

if(args.length == 1){

if(args[0] == “Crime.csv”){

in = new FileInputStream(args[0]);

inputStream = new BufferedReader(new FileReader(args[0]));

scannerIn = new Scanner(inputStream);

outputStream = new BufferedWriter(new FileWriter(“CrimeCopy.csv”));

System.out.println(“CrimeCopy.csv is made. nLet’s look for US Crime information.n”);

} else{

System.out.println(“Invalid file namen”);

}

} else{

System.out.println(“Enter 1 valid file namen”);

}

} catch(FileNotFoundException nf){

System.err.println(“File not foundn”);

} catch(IOException io){

System.err.println(“General I/O error occuredn”);

} finally{

try{

if(outputStream !=null){

outputStream.close();

}

if(inputStream !=null){

inputStream.close();

}

if(in !=null){

in.close();

}

} catch(IOException io){

System.out.println(“Issue closing the file”);

}

}

//Answer the question to user

String userAnswer;

Object records = new UScrime(userAnswer);

do{

//List the questions

System.out.println(“Enter the number of the question you want answered.”

+ “nEnter ‘Q’ to quit the program.n”);

System.out.println(“1. What were the percentages in population growth for each consecutive year from 1994 – 2013?”

+ “n2. What year was the Murder rate the highest?”

+ “n3. What year was the Murder rate the lowest?”

+ “n4. What year was the Robbery rate the highest?”

+ “n5. What year was the Robbery rate the lowest?”

+ “n6. What was the total percentage change in Motor Vehicle Theft between 1998 and 2013?”

+ “n7. What year has the assault rate decreased the most?”

+ “n8. What year has the assault rate decreased the least?”

+ “nQ. Quit the programn”);

System.out.print(“Enter your selection: “);

userAnswer = scannerIn.nextLine();

boolean flag = false;

int index = 0;

for (int answerNum=0;answerNum&lt;records.crimeInfo.length;answerNum++){

if(records.crimeInfo[answerNum][0].equalsIgnoreCase(userAnswer)){

index=answerNum;

flag=true;

}else if(!records.crimeInfo[answerNum][0].equalsIgnoreCase(userAnswer)){

}

}if (flag){

} else{

System.out.println(records.crimeinfo[index][1]);

System.out.println(“You entered invalid question number. Try it again.”);

}

} while(!userAnswer.equalsIgnoreCase(“Q”));

if(userAnswer.equalsIgnoreCase(“Q”)){

System.out.println(“Thank you for trying the US Crimes Statistics Programn”);

}

Instant end = Instant.now();

System.out.println(“Elapsed time was: ”

+ Duration.between(start, end).toNanos()/1_000_000_000.0

+ ” seconds.n”);

System.exit(0);

}

}