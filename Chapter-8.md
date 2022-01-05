# Chapter-8


A1. PyInputPlus is not a part of the Python Standard Library hence it   
    must be installed seperately. 

A2. In order to shorten typing pyinputplus.function_name() to pyip.
    function_name() each time a function has to be called.

A3. inputInt() accepts only integer values from the user whereas the 
    inputFloat() accepts integer values as well as decimal values from the user.

A4. import pyinputplus as pyip
    response = pyip.inputInt(min = 0, lessThan= 100, prompt = 'Enter the number: ' )
    print(response)  

A5. Regular expressions are passed as raw string arguments to the 
    allowRegexes and blockRegexes 

A6. The function terminates with a pyip.RetryLimitException 

A7. hello is printed each time when a blank input is received as an input

Sandwich Maker : 

 import pyinputplus as pyip
 bread = pyip.inputMenu(['wheat', 'white', 'sourdough'], prompt = 'Breads avaiable--> wheat, white, sourdough\nEnter your choice: ')
 if bread == 'wheat' :
    b_p = 5
 elif bread == 'sourdough' :
    b_p = 7
 else : 
    b_p = 4
 cost = b_p  
 protein = pyip.inputMenu(['chicken', 'turkey', 'ham', 'tofu'], prompt = 'Protein type avaiable-->chicken, turkey, ham, or tofu\nEnter your choice: ')
 if protein == 'chicken' :
    p_p = 15
 elif protein == 'turkey' :
    p_p = 12
 elif protein == 'ham' :
    p_p = 10    
 else : 
    p_p = 8
 cost = cost + p_p           
 cheese = pyip.inputYesNo(prompt = 'Do you want cheese?\nEnter Yes or No: ')
 if cheese == 'yes' :
    cheese_ty = pyip.inputMenu(['cheddar', 'swiss', 'morazella'], prompt = 'Cheese type avaiable-->cheddar, swiss, morazella\nEnter your choice: ')
    if cheese_ty == 'cheddar' :
        ct_p = 5
    elif cheese_ty == 'swiss' :
        ct_p= 7
    else : 
        ct_p= 4
    cost = cost + ct_p
 addons= pyip.inputYesNo(prompt = 'mayo, mustard, lettuce, or tomato\nEnter Yes or No: ')
 if addons == 'yes' :
    cost += 4
 number = pyip.inputInt(prompt = 'Number of sandwiches: ', min = 1, default = 'The minimun number of allowed orders are 1')
 cost = cost * number
 print(f'${cost}')

Write Your Own Multiplication Quiz :

 import pyinputplus as pyip
 import time, random 
 noOfQues = 10
 correct_ans = 0
 for i in range(noOfQues) :
    no1 = random.randint(0,9)
    no2 = random.randint(0,9)
    ques = no1 * no2
    prompt = 'Question %s: %s * %s\n'%(i, no1, no2)
    try :
        pyip.inputStr(prompt, allowRegexes=['^%s$' % (no1 * no2)], blockRegexes=[('.*','Incorrect!')], timeout=8, limit=3)
    except pyip.TimeoutException:
       print('Out of time!')
       break
    except pyip.RetryLimitException:
       print('Out of tries!')
       break
    else :
        print('Correct')
        correct_ans += 1
        continue
    time.sleep(1)
 print('No. of Questions answered Correct: %s'%(correct_ans)) 
 print(f'Score: {correct_ans}/{noOfQues}')  
 

      

