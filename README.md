# ObjectOrientedProgramming

What is Object Oriented Programming?

    Object Oriented Programming (OOP) is a programming model (paradigm) that organizes software design around objects. Objects can be defined as a data 
    field with unique attributes and behaviors. 

    The power behind OOP is that it is well-suited for large, complex, and actively updated and maintained programs. It is also beneficial to collaborative
    development.

    Imagine you work for Amazon and you have been tasked with creating code for drones that will deliver packages more efficiently. Using OOP, you and your
    team may break down this problem into more manageable tasks. For example, one team may tackle the propellers, one team might tackle the camera,
    one team may tackle the claws that hold the package, etc. This follows object oriented programming.
  
Creating Objects
  
    Imagine you're working for a gaming company and they want to create a Wizard game.
    
    You would need a player object and you can define that as follows:
    
    class PlayerCharacter: 
        def __init__(self, name):
            self.name = name
        
        def run(self):
            print('run')
            
    player1 = PlayerCharacter("John")
    player2 = PlayerCharacter("Mike")
    
    
    Essentially, classes act as a blueprint. By defining a class, you are creating a new data type that has its own behaviors and attributes.
    It can have its own variables, functions, methods, etc. You can create as many new objects (player1, player2, so on) as needed from this
    "blueprint". 
    
    The 'def __init__(self, name)' line is us declaring a dunder method, also known as a magic method. It acts as a constructor, helping initialize
    the class. The 'self' parameter is reference to the object itself, the PlayerCharacter class. 
    
    The 'self.name = name' line is using the name parameter, owned by the PlayerCharacter class, hence 'self.name'. We are essentially telling the
    class that its name parameter, will receive whatever name is passed as an argument. Therefore, when we run player1 = PlayerCharacter("John"), 
    self.name is set to "John"
    
For more information about Classes/Objects:
https://www.w3schools.com/python/python_classes.asp


Attributes and Methods

    Classes can have their own methods and attributes (or properties). This allows for more functionality and mimic the real world. 
    
    OOP allows us to write code that is repeatable, well-organized, and memory efficient.
    
    Attributes are pieces of data that are dynamic. When they are instanciated they are unique to their object. 
    
    There is such thing as a Class Object Attribute, and these differ from normal attributes as they are not dynamic. They are true to all objects of 
    that class. 
    ex:
    
        class PlayerChracter:
            membership = True
            def __init__(self, name, age):
            * more code *
            
        membership = true, is an example of a class object attribute. In all instances of PlayerCharacter, it will result in true, unlike name and age
        which differ from instance to instance.
        
\__init__
    
    __init__ is a constructor function, which controls how a new instance of a class is initialized. For example, we can set limits, set default 
    parameters, etc.
    
    ex:
    
        * class definition up here *
            def __init__(self, name="anonymous", age=0):
                if age > 18:
                    self.name = name
                    self.age = age
                    
        As you can see, we have set a default value for age and name within the parameters of the __init__ function. We have also set a condition,
        that our players be 18 years or older in order to create a character. 
        
        Creating a new instance of PlayerCharacter would be as follows:
        player1 = PlayerCharacter("Tom", 19)
        
For more information on __init__ and dunder methods:
https://www.section.io/engineering-education/dunder-methods-python/#:~:text=Dunder%20methods%20are%20names%20that,in%20functions%20for%20custom%20classes.
        
@classmethod and @staticmethod

    Using @classmethod, we are able to created special methods within our classes. 
    ex:
    
        @classmethod
        def adding_things(cls, num1, num2):
            return num1 + num2
            
    If you attempt to run player1.adding_things(2,3), it would error out as Python considers the object as an argument for the method as well,
    meaning the function requires 3 parameters. That is where the 'cls' keyword comes in, which stands for class. Adding this to your in-class 
    method allows for 'player1.adding_things(2,3)' to work as expected.
    
    You don't even have to instatiate a new instance of a class to use this method as it is a class method. Meaning you could simply call
    PlayerCharacter.adding_things(2,3) and you'd get the same result.
    
    Since it is a class method, you could actually use it to instantiate a new instance of said class with a little alteration. For example:
        @classmethod
        def adding_things(cls, num1, num2):
            return cls("Teddy", num1 + num2)
            
    player3 = PlayerCharacter.adding_things(2,3)
    ^This creates a new player object with the name "Teddy" and the age of 5.
    
    @staticmethod works practically the same way, however, you do not have access to 'cls' with @staticmethods. ex:
    
    @staticmethod
    def adding_things(num1, num2):
        return num1 + num2
        
    So what's the difference? You would use @classmethods when you care about the state of the class, in other words, when you care about its 
    attributes and properties. You would use @staticmethods when you do not care and just need something to be returned.
    
    * These are not typically seen in programming but they do have their uses *
    
Link to Repl.it demonstrating in-class methods:
https://replit.com/@AutomationApe/FavoriteMusicGenreLister#main.py

To learn more about classes and their methods:
https://www.w3schools.com/python/python_classes.asp


   
