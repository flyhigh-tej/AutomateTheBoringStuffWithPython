# Chapter-11


A1. assert spam < 10

A2. assert eggs.lower() == bacon.lower()

A3. assert True

A4. import logging
    logging.basicConfig(level=logging.DEBUG, format=' %(asctime)s - %(levelname)s - %(message)s')

A5. import logging
    logging.basicConfig(filename = 'programLog.txt', level=logging.DEBUG, format = ' %(asctime)s - %(levelname)s - %(message)s')

A6. 1. logging.debug()
    2. logging.info()
    3. logging.warning()
    4. logging.error()
    5. logging.critical()

A7. logging.disable(logging.CRITICAL)    

A8. 1. While deleting print() of log messages there is a 
       possibilty to delete print() from the main program also.
    2. A single line of code logging.disable(logging.CRITICAL) 
       can stop printing the log statements once the debugging is done rather than deleting each and every statement.
    3. Time conserving

A9. Step Over : If the next line of code is a function call() it 
                quickly executes all the line of code in the function and pause at the statement following return statement.

    Step In : If the next line is a function call it enters inside 
              the function and pauses at the first line of code.

    Step Out : It executes all the statements inside the current function and pauses execution at the line following the return statement                           

A10. The debugger will stop at the breakpoint (if made) or once 
     the program is done executing all the statements.

A11. Breakpoint is a user defined point to a line of code where 
     the execution must pause when the debugger reaches that line of code.  

A12. By clicking on the line number of the respective 
     line a red dot appears then the breakpoint is set.


Debugging Coin Toss : 
  import random,logging
  logging.basicConfig(level = logging.DEBUG, format = '%(asctime)s - %(levelname)s - %(message)s')
  #logging.disable(logging.INFO)
  print('Guess the coin toss! Enter heads or tails:')
  guess = input()
  check = ['tails','heads']
  while guess not in check:
    print('Guess the coin toss! Enter heads or tails:')
    guess = input()
 toss = random.randint(0, 1) # 0 is tails, 1 is heads
 if check[toss] == guess:
    logging.info('1st Output: %s' %(check[toss]))    
    print('You got it!')
 else:
    print('Nope! Guess again!')
    guess = input()
    logging.debug('2nd Output: %s \nUser Input: %s' %(check[toss],guess))
    if check[toss] == guess:        
        print('You got it!')
    else:
        print('Nope. You are really bad at this game.')   
                   