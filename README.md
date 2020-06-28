## Table of Content
- [Meaningful names](#meaningful-names)
    - [Intension-Revealing Names](#intension-revealing-names)
    - [avoid disinformation](#avoid-disinformation)
    - [Meaningful Distinction](#meaningful-distinction)
    - [Pronounceable Names](#pronounceable-names)
    - [Use Searchable Names](#use-searchable-names)
    - [Avoid Encoding](#avoid-encoding)
    - [Avoid Mental Mapping](#avoid-mental-mapping)
    - [Pick One Word Per One Concept](#pick-one-word-per-one-concept)
    - [Dont Pun](#dont-pun)
- [Functions](#functions)
    - [Small](#small)
    - [Indent](#indent)
    - [Just one thing](#just-one-thing)
    - [One Level of Abstraction per Function](#one-level-of-abstraction-per-function)
    - [Reading Code from Top to Bottom: The Stepdown Rule](#reading-code-from-top-to-bottom--the-stepdown-rule)
    - [Switch Statements](#switch-statements)
    - [Use Descriptive Names](#use-descriptive-names)
    - [Function Arguments](#function-arguments)
    - [Command query sepration](#command-query-sepration)
    - [prefer exception to return error code](#prefer-exception-to-return-error-code)
    - [Don’t repeat your self](#don-t-repeat-your-self)
    - [How do you write function like this](#how-do-you-write-function-like-this)
- [Comments](#comments)
  * [Comments Do Not Make Up for Bad Code](#comments-do-not-make-up-for-bad-code)
  * [Explain Yourself in Code](#explain-yourself-in-code)
  * [Good Comments](#good-comments)
    + [Legal Comments](#legal-comments)
    + [Informative Comments](#informative-comments)
    + [Explanation of Intent](#explanation-of-intent)
    + [Warning of concequences](#warning-of-concequences)
    + [TODO Comments](#todo-comments)
  * [Bad Comments](#bad-comments)
    + [Redundant Comments](#redundant-comments)
    + [Mandated Comments](#mandated-comments)
    + [Journal Comments](#journal-comments)
    + [Noise Comments](#noise-comments)
    + [Don’t Use a Comment When You Can Use a Function or a Variable](#don-t-use-a-comment-when-you-can-use-a-function-or-a-variable)
    + [Position Markers](#position-markers)
    + [Closing Brace Comments](#closing-brace-comments)
    + [Attributions and Bylines](#attributions-and-bylines)
    + [Commented-Out Code](#commented-out-code)
    + [Nonlocal Information](#nonlocal-information)
    + [Too Much Information](#too-much-information)
- [Formatting](#formatting)
    - [Vertical Formatting](#vertical-formatting)
    - [The Newspaper Metaphor](#the-newspaper-metaphor)
    - [Vertical Openness Between Concepts](#vertical-openness-between-concepts)
    - [Vertical Distance](#vertical-distance)
    - [Dependent Functions](#dependent-functions)
    - [Horizontal Formatting](#horizontal-formatting)
    - [Indentation](#indentation)
    - [Team Rules](#team-rules)
- [Error Handeling](#error-handeling)
    - [Use Exceptions Rather Than Return Codes](#use-exceptions-rather-than-return-codes)
    - [Write Your Try-Catch-Finally Statement First](#write-your-try-catch-finally-statement-first)
    - [Provide Context with Exceptions](#provide-context-with-exceptions)
    - [Don’t Return Null](#dont-return-null)
    - [Don’t Pass Null](#dont-pass-null)
- [Boundaries](#boundaries)
    - [Using Third-Party Code](#using-third-party-code)
    - [Exploring and Learning Boundaries](#exploring-and-learning-boundaries)
    - [Learning Tests Are Better Than Free](#learning-tests-are-better-than-free)
    - [Using Code That Does Not Yet Exist](#using-code-that-does-not-yet-exist)
    - [Clean Boundaries](#clean-boundaries)
- [Unit Tests](#unit-tests)
    - [The Three Laws of TDD](#the-three-laws-of-tdd)
    - [Clean Tests](#clean-tests)
    - [One Assert per test](#one-assert-per-test)
    - [F.I.R.S.T](#first)
- [Classes](#classes)
    - [Encapsulation](#encapsulation)
    - [Classes Should be Small](#classes-should-be-small)
    - [The Single Responsibility Principle](#the-single-responsibility-principle)
    - [Cohesion](#cohesion)
    - [Maintaining Cohesion Results in Many Small Classes](#maintaining-cohesion-results-in-many-small-classes)
    - [Organizing for change](#organizing-for-change)



  
## Meaningful names
### Intension-Revealing Names

Bad:
```java
int a;
```

Good:
```java
int downTimeCounterToLifeEnded;
```
### avoid disinformation

Bad:
```java
int a = l; 
if ( O == l )
   a=O1;
else
   l=01;
```

Good:
```java
int allMrBugIssues = loadOfWeb;

int zeroNumberOfServer= 0;
int oneNumberOfServer= 1;
int originalNumberOfBugs= 2;
int originalNumberOfHumer= 3;

 if ( originalNumberOfHumer == loadOfWeb )
   allMrBugIssues=originalNumberOfBugs;
 else
   loadOfWeb=oneNumberOfServer;
```
### Meaningful Distinction

Bad:
```csharp
string deadManProperty;
string deadManInfo;
string deadManData;
```

Good:
```csharp
string killedManId;
string nameOfKilledMan;
string allInfoAboutKilledWoman; 
```


### Pronounceable Names

Bad:
```csharp
string ymdstr = datetime.today().strftime("%y-%m-%d");
```

Good:
```csharp
string currentTimeOfHappyMan = datetime.today().strftime("%y-%m-%d");
```

### Use Searchable Names

Bad:
```java
// What is the number 86400 for again?
human.sleep(86400) ;
```

Good:
```java
// Declare them in the global namespace for the module.
int SECONDS_IN_A_DAY = 60     - 60     - 24 ; 
human.sleep(SECONDS_IN_A_DAY) ;
```

### Avoid Encoding

Bad:
```csharp
int iHumanCapacity= 1;
string strMyName= "MrBug";
DateTime dLifeLength;
bool impCalculateLifeSuffering(int nPeopleArroundYou){
   bool bSuffering=false;
   if(nPeopleArroundYou > iHumanCapacity)
      bSuffering=true;
   
   return bSuffering;

}
```

Good:
```csharp
int humanCapacity= 1;
string myName= "MrBug";
DateTime LifeLength;

bool CalculateLifeSuffering(int PeopleArroundYou){
   bool Suffering=false;
   if(PeopleArroundYou > 0)
      Suffering=true;
   
   return Suffering;

}
```

### Avoid Mental Mapping

Bad:
```python
bestTimesOfDay = ("Morning", "Befor Morning", "After Morning")

for item in bestTimeOfDay:
    #do_stuff()
    #do_some_other_stuff()

    # Wait, what's `item` again?
    print(item)
```

Good:
```python
bestTimeOfDay = ("Morning", "Befor Morning", "After Morning")

for timeOfDay in bestTimeOfDay:
    #do_stuff()
    #do_some_other_stuff()

    print(timeOfDay)
```

### Pick One Word Per One Concept

Bad:
```python
FetchHumanOverthinkingData(sadness, happiness)

GetHumanOverthinkingData(sadness, happiness)

RetrieveHumanOverthinkingData(sadness, happiness)
```

Good:
```python
GetHumanOverthinkingData(sadness, happiness)
```

### Dont Pun

Bad:
```python
time = calculateMyBirthday()

# ... some code are happening ....

time = calculateDeathTime()

```

Good:
```python
timeOfBirthday = calculateMyBirthday()

# ... some code are happening ....

timeOfEndingThisShit = calculateDeathTime()
```



## Functions
### Small

Bad:
```java
int calcBeautyOfLife(){
   // here is full of messy condistion and long over 20 lines
   // ...
   // .. 
   // ..
   // ..
   return 0;
}
```

Good:
```java
int calcHappinessOfLife(){
   if(isHumanAlive)
      return 0;
   // keep it small and simple
}
```

### Indent

Bad:
```csharp
string howCanIBeAGentleman(){
   for ...
      if ...
        for ...
            if ...
               for ...
                  if ...
                     return "you can not !"
}  
```

Good:
```csharp
// break into multi function and max indent of each function is 2
int howCan(){}
int IBe(){}
string AGentleman(){ return "you can not !" }
```

### Just one thing

Bad:
```csharp
string getFullPackageOfData(string name){
   // some code to eval life problems
   for ...
      if ...
   
   // some code to get information about coffee
   for ...
      if ...

   // some another junk code to eval nothing
   ... 
   ...

}
```

Good:
```csharp
string getCoffeeInfo() { }

long evalLifeProblems() { }

void evalNothing() { }

```

### One Level of Abstraction per Function

Bad:
```csharp
void multiLevelOfAbstraction(){
   // getNameOfUser
   for ...
    if ... 
   
   // check user have a lot of money or not
   for ...
     if ...
}
```

Good:
```csharp
string getNameOfUser() { }

bool hasAlotOfMoney()  { }
```

### Reading Code from Top to Bottom: The Stepdown Rule

Bad:
```csharp
getUserInfo()
getName()
getLastSeen()
getDataFromServer()
```

Good:
```csharp
getName()
getLastSeen()
getUserInfo()
getDataFromServer()

```

### Switch Statements

Bad:
```java
void deadManOrLiveWoman(){
   switch ...
    case:

    case:
}
```

Good:
```java
void deadManOrLiveWoman(){
   
}
```

### Use Descriptive Names

Bad:
```java
int handle(string life){
   // some complecated code to calc value of input
   // ...
   // ...
   // ...

   return 0;
}
```

Good:
```java
int calculateValueOfLife(string life){
   // some complecated code to calc value of input
   // ...
   // ...
   // ...
   
   return 0;
}
```

### Function Arguments

Bad:
```java
int humanDetection(int name, int job, int personality, int degree, int lastTweet, ...){
   return 0;
}
```

Good:
```java
int humanDetection(){
   return 0;
}
// or max args =3
int humanDetection(int name, int job, int personality){
   return 0;
}
```

### Side effects

Bad:
```java
int evalLifeProblems(){
   changeLifePain();
   changeHumanSadness();
   changeAllOfPeople();

   for ...
      if ...
   
   return 99999999999999999999999999999999999
}
```

Good:
```java
int evalLifeProblems(){

   for ...
      if ...
   
   return 99999999999999999999999999999999999
}
```

### Command query sepration

Bad:
```java
string timeToDeath(){
   If(Set("username","you")){
      ...
   }
   return "i am cpu not god !" 
}
```

Good:
```java
string timeToDeath(){
   if(attributeExist("username")){
      ...
   }
   else
      setAtrribute("username","you")

   return "i am cpu not god !" 
}
```

### prefer exception to return error code

Bad:
```java
int findCrazyManInClass(){
   if(!isMan())
      return 1;
  
   if(!isInClass())
      return 2;
  
   if(!isCrazy())
      return 3;
   
   return 1000;
}
```

Good:
```java
int findCrazyManInClass(){
   try{
   ...
   
   return 1000;

   }
   catch(Error){
      return 0;
   }
   
}
```

### Don’t repeat your self

Bad:
```java
string coolFunction(){
   return "i am not cool";
};

copyOfCoolFunction(){
   return "i am not cool";
}
copyOfCoolFunction(){
   return "i am not cool";
}
copyOfCoolFunction(){
   return "i am not cool";
}
copyOfCoolFunction(){
   return "i am not cool";
}
copyOfCoolFunction(){
   return "i am not cool";
}
```

Good:
```java
string coolFunction(){
   return "i am not cool";
};

// import cool function and use it
coolFunction();

```



## Comments
   
### Comments Do Not Make Up for Bad Code
   
Bad:
```python
# a is sum of you and me 
a = b + c
```

Good:
```python
we = you + me
```


### Explain Yourself in Code
   
Bad:
```java
// here is function explaination 
// too boring 
// . . . 
// . . . 
iAmComplicatedFunction()
```

Good:
```java
simple()
function()
toUnderstand()
withoutComments()
```


### Good Comments
   
#### Legal Comments

Good:
```java
// Copyright (C) 2020 by mrBug, Inc. All rights reserved.
```


#### Informative Comments
   

Good:
```java
// format matched kk:mm:ss EEE, MMM dd, yyyy 
Pattern timeMatcher = Pattern.compile("\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```


#### Explanation of Intent
   
Bad:
```java
int isBetter(string human){
   if(human == "woman")
      return 0; 
}
```

Good:
```java
int isBetter(string human){
   if(human == "woman")
      return 0;  // i mean woman is not better 
}
```


#### Warning of concequences
   
Bad:
```java
void relaxFunction(){
   system.sleep(1000000)
}
```

Good:
```java
// Don't run unless you have some time
void relaxFunction(){
   system.sleep(1000000)
}
```


#### TODO Comments
   
Bad:
```java
void makeSomeDangerInSoftware(){
   
}
```

Good:
```java
// TODO write this function  when company doesn't pay the money
void makeSomeDangerInSoftware(){
   
}
```


### Bad Comments
   
#### Redundant Comments
   
Bad:
```java
// this function input is name of user and check if the name is you return false becouse you
// are not cool enough
bool isCoolPerson(string name){
   if(name == "you")
      return false;
}
```

Good:
```java
bool isCoolPerson(string name){
   if(name == "you")
      return false;
}
```


#### Mandated Comments
   
Bad:
```java
/**
* The Manager implementation with which this Container is * associated.
*/
protected Manager manager = null;
/**
* The cluster with which this Container is associated. */
protected Cluster cluster = null;
/**
* The human-readable name of this Container. */
protected String name = null;
/**
* The parent Container to which this Container is a child. */
protected Container parent = null;
/**
* The parent class loader to be configured when we install a * Loader.
*/
protected ClassLoader parentClassLoader = null;

```

Good:
```java

protected Manager manager = null;

protected Cluster cluster = null;

protected String name = null;

protected Container parent = null;

protected ClassLoader parentClassLoader = null;

```


#### Journal Comments
   
Bad:
```java
* Changes (from 20-Oct-2020)
* --------------------------
* fixed and report

```

Good:
```java
// keep it clean
```


#### Noise Comments
   
Bad:
```java
/** The day of the month. */
private int dayOfMonth;
```

Good:
```java
private int dayOfMonth;
```


#### Don’t Use a Comment When You Can Use a Function or a Variable
   
Bad:
```java
// this function gain the pain 
// long long description
void a(){
   ...
}
```

Good:
```java
void painGainer(){
   ...
}
```


#### Position Markers
   
Bad:
```java
///////////////////////////////////////////
///////////////// mrBug ///////////////////
///////////////////////////////////////////
```

Good:
```java
// mrBug
```


#### Closing Brace Comments
   
Bad:
```java
while (deadLine != null) {

   work++;
   if(life == null){
      ...
      ...
      ...
      ...
      if(time == "night" ){
         ...
         ...
         ...
         ...
         ...
         ...
         ...
      } // if : time == night
      ...
      ...
      ...
      break;
   }// if : life == null

} //while deadLine
```

Good:
```java
while (deadLine != null) {

   work++;
   if(life == null){
      anotherSimpleFunction()
      ...
      break;
   }

} 
```


#### Attributions and Bylines
   
Bad:
```java
/* Added by MrBug */
```

Good:
```java
// keep it clean, let version-contrlol do !
```


#### Commented-Out Code
   
Bad:
```java
this.bytePos = writeBytes(pngIdBytes, 0);
//hdrPos = bytePos;
writeHeader(); writeResolution();
 //dataPos = bytePos; 
 if (writeImageData()) {
   writeEnd();
   // this.pngBytes = resizeByteArray(this.pngBytes, this.maxPos); 

   }
```

Good:
```java
this.bytePos = writeBytes(pngIdBytes, 0);
writeHeader(); writeResolution();
 if (writeImageData()) {
   writeEnd();
   }
```


#### Nonlocal Information
   
Bad:
```java
/**
* nonLocalFunction description
* nonLocalFunction description
* nonLocalFunction description
* nonLocalFunction description
* nonLocalFunction description
* nonLocalFunction description
*
*
*
* Port on which fitnesse would run. *
* @param fitnessePort
*/
public void setFitnessePort(int fitnessePort) {
   this.fitnessePort = fitnessePort; 
}

```

Good:
```java
/**
* Port on which fitnesse would run. *
* @param fitnessePort
*/
public void setFitnessePort(int fitnessePort) {
   this.fitnessePort = fitnessePort; 
}
```


#### Too Much Information
  
Bad:
```java
/*
RFC 2045 - Multipurpose Internet Mail Extensions (MIME)
Part One: Format of Internet Message Bodies
section 6.8. Base64 Content-Transfer-Encoding
The encoding process represents 24-bit groups of input bits as output strings of 4 encoded characters. Proceeding from left to right, a 24-bit input group is formed by concatenating 3 8-bit input groups. These 24 bits are then treated as 4 concatenated 6-bit groups, each of which is translated into a single digit in the base64 alphabet. When encoding a bit stream via the base64 encoding, the bit stream must be presumed to be ordered with the most-significant-bit first. That is, the first bit in the stream will be the high-order bit in the first 8-bit byte, and the eighth bit will be the low-order bit in the first 8-bit byte, and so on.
*/
```

Good:
```java
// keep it clean
```

# Formatting
   
### Vertical Formatting
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### The Newspaper Metaphor
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Vertical Openness Between Concepts
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Vertical Distance
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Dependent Functions
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Horizontal Formatting
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Indentation
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Team Rules
  
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

# Error Handeling
### Use Exceptions Rather Than Return Codes
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Write Your Try-Catch-Finally Statement First
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Provide Context with Exceptions
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Don’t Return Null
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Don’t Pass Null
  
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

# Boundaries
### Using Third-Party Code
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Exploring and Learning Boundaries
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Learning Tests Are Better Than Free
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Using Code That Does Not Yet Exist
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Clean Boundaries
  
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

# Unit Tests
   ### The Three Laws of TDD
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Clean Tests
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### One Assert per test
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### F.I.R.S.T
  
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

# Classes
   ### Encapsulation
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### Classes Should be Small
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

### The Single Responsibility Principle
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Cohesion
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Maintaining Cohesion Results in Many Small Classes
   
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```


### Organizing for change
  
Bad:
```java
int a;
```

Good:
```java
int daySinceModification;
```

