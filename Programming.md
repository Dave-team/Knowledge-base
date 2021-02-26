# Programming 

## Principles
- DRY: Don’t Repeat Yourself. Specify things once and then use that – don’t duplicate things  
- YAGNI: You Ain’t Gonna Need It. Only implement things when you really need them. Mostly, you don’t need things after all, or what you actually need is quite different from what you foresaw you needed  
- KISS: Keep It Simple Stupid
- Don’t reinvent the wheel
- Analysis paralysis – do your analysis but sometimes, you just need to start doing things 
- Scope creep – create something that just about meets the requirements – keep the scope manageable 
- Break things down into small parts and make things modular 
- Deliver continuously – test continuously 
- Implement test driven development: write tests before you write the software 
- Choose names for variables, functions and arguments that are meaningful
- Use comments to clarify what you want before starting to write any code. Comments shouldn’t explain what the code is doing. Instead, comments should explain why the code is doing something. Think about the person that is taking over your role. How to make his/her life easy? 
- Use comments throughout coding to clarify what the code does
- Whenever you do something more often, make sure to wrap what you’re doing in a function. Make sure to not repeat yourself using for loops and list comprehensions. Future me: the goal of your Python writing should be to create modular code where functions can be used throughout other scripts. And then the next step is using abstraction by implementing classes. To test your code, use Pytest (usually we create unit tests with this)– you want to implement test driven development. Ultimately, you want to work within different virtual environments to reduce dependencies and to build packages. All of this ties into creating robust Python workflows which tightly links back to using Object Oriented Programming (OOP),You’ll want to implement Continuous Integration CI pipelines, such as Travis 
- Write docstrings for your code – these make up the final documentation. Docstrings should include: 
  - Description of what the function does
  - Description of arguments
  - Description of return values
  - Description of errors
  - Additional notes
- Version control your code, e.g. in GitHub
- Automate as much as possible 
- Get code reviews
- Make notes on any new things you learn in the process 

## Programming process
- Principle: The goal is to not just make the program work – the goal is to learn how to make the program work 
- Before writing code and or a program, make sure you really understand the problem. Break the problem down into its components and write a high level plan in pseudo code. 
- Start small; tackle that small bit first. Make it work, document and test, understand and only then move on to the next bit. Make sure that every small bit of code you make work, that it is optimized to the best of your ability. 
- Create a skeleton when working on a project. In this skeleton you specify all the individual tasks than need to be completed 
- Use incremental development: add and test a small piece of code at a time and make sure it returns the desired results before adding the next piece of code
- TEST! 
- If you can’t figure something out, ask for help (make sure you really thought things through and be able to clearly outline your problem with the things you have already tried to implement). 
- When looking at solutions online: would this work? Why? 
- Coding is about learning throughout the process. You cannot rush into a solution. A bug is an opportunity to learn. Step back from the bug and look at the problem from a higher level to properly understand what you’re working on.  

## Debugging 
- What are the potential reasons this might be different? Eliminate those differences 

**Rubber Duck Debugging**
- Beg, borrow, steal, buy, fabricate or otherwise obtain a rubber duck (bathtub variety).
- Place rubber duck on desk and inform it you are just going to go over some code with it, if that’s all right.
- Explain to the duck what your code is supposed to do, and then go into detail and explain your code line by line.
- At some point you will tell the duck what you are doing next and then realise that that is not in fact what you are actually doing. The duck will sit there serenely, happy in the knowledge that it has helped you on your way.

- Solve one problem at a time. Once the problem is solved, then make it more efficient and generally better.
- Write the comments first, then fill in the code.
- If you can’t debug, throw out and replace.

**Understanding and fixing the problem**
- What is your code sample supposed to do?
- What exactly is the problem you're seeing?
- What is the expected output or behavior of your program?
- What output or behavior do you get instead?
- If your code doesn't compile or crash, is there an error message of any kind? If so, what is it? If not, what happened?
- What inputs, if any, cause the problem?
- What have you already tried to debug your own problem? Where do you suspect the problem is? What uncertainties do you have?
- What precisely are you confused by?
- Have you tried googling for answers? If so, what search queries have you tried? What pages have you read? What do you find confusing about them?

**Testing and debugging**
1. What should the program be doing? 
2. If that doesn’t work, figure out what the program is actually doing – look at the error messages 
   1. When there is an error in the program, try commenting out the line of the error and run the program
   2. Try commenting out the entire remainder of the code and run it. Then check the error message
   3. Take the line where the error is most likely to be and over simplify it before running it again
   4. When there is a name error, search for the name in the code
3. Run test cases: 
   1. Try and except cases
   2. Use the IDLE debugger

**Tests**
- Unit tests: test one tiny bit of functionality in isolation and prove it is doing things right. Each unit test must be independent / able to run on its own 
- Integration testing: check if different modules work fine when combined together as a group
- Functional testing: testing functionality within the system (with dependencies) to confirm the code is doing the right things
- Acceptance testing: testing the entire application end to end 

## Learning how to program
True passion for programming is the driving force behind it:
1. Learning the syntax of some simple programming language, e.g. Python
2. Figure out the environment where you code and run your programs
3. Write a few programs, run them, feel happy and excited to see them running
4. Improve your program, add new features
5. Get stuck in some problems which seemed simple in the first place
6. Get help, find solutions online, read tutorials how others have coded similar problems
7. Realize you could improve your previous code, when write the same feature again, now you write it in a better way
8. Understand the deficiencies in your programs
9. Spend countless hours, days, nights to fix bugs
10.	Get help from more experienced programmers if possible, as it will save tons of time
11.	In a few months now that you understand the language and development environment better, you write something more challenging.
12.	The above cycle repeats. Programming requires constant practice

As a junior developer, you’ll spend a lot of time reading other people’s code – become good at it and learn to identify bugs

## Tools
- Docker: container tool, making sure the code runs on all environments 
- Kubernetes: container tool 
- Travis: Continious Integration
- Sphinx: documentation
- Git: version control software 

## Other
- Whenever you save code, make sure to not include your credentials. Instead, use an input field that requires the password
- Whenever you use pip, you are installing a package. You can create your own packages as well 
- Microservices are a software development technique—a variant of the service-oriented architecture architectural style that structures an application as a collection of loosely coupled services.
- CD / CI (Continuous Delivery and Continuous Integration) 
- AWS Lamdba - used to run code within the cloud 
- Web server - server that can run on the web 
