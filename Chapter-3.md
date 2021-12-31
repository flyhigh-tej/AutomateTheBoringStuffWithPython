# Chapter-3

A1. 1.Functions are the primary way to compartmentalize the code into 
      logical groups.
    2.Very useful at the time of debugging to spot the errors and to correct
      them.
    3.Functions are a great tool to help organize the code. 

A2. Functions are executed when called.

A3. def function_name():

A4. Function consists of a set of statements to perform a desired action.
    The statements are executed only when it is called from some part of 
    the program. 

A5. There exists only 1 global scope whereas any number of local scopes can 
    be present in a program depending upon the number of functions present. 

A6. The variables in the local scope gets destroyed once the function 
    containing the variables has encountered a return statement for that 
    respective function.

A7. Return values are the user set values to be given as output on reaching 
    the completion of the respective function. Yes
    
A8. The function will have a null value as the return value.

A9. By using the keyword global while defining the variable.

A10. NoneType

A11. It imports all functions from areallyourpetsnamederic module which can  
     be accessed by all members of the respective program.

A12. spam.bacon()

A13. By Exception Handling using try and except blocks.

A14. The try block is used for detecting the error while executing statements 
     in the program and the except clause contains the possible fix for the error detected in the try clause.

Practice Project:

ans=0    
#reduces number by checking whether odd or even
def collatz(number) :
 global ans
 if number%2 == 0 :    
   ans= n//2
   print(ans)
 else :
   ans = 3*number+1
   print(ans)
 return ans

while True :
  try :               #Input validation using Exception Handling
   print("Enter a number")
   n = int(input())
  except ValueError :
   print('Enter an integer only') 
  collatz(n)

  if ans == 1:  #Checks for the value 1
    break
  else :
    continue 

