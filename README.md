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

Encapsulation

    There are 4 'pillars' of OOP. Essentially the core topics of OOP. The first of the four is Encapsulation which is essentially the binding of 
    data and the functions that manipulate said data. In other words, it is the idea of attributes and actions of a particular thing being
    collected into a single place that we call a class.

For more information on encapsulation:
https://pynative.com/python-encapsulation/

Abstraction

    Abstraction, another pillar of OOP, is the hiding of information/only giving access to neccessary information. Abstraction is important because 
    it helps keep data private and also prevents frustrating albeit accidental errors from happening. For example, you may accidentally alter the 
    value of a variable that should not have been altered. Abstraction would prevent that from occuring, using keywords such as private. 
    
For more information on abstraction:
https://www.faceprep.in/python/abstraction-in-python/#:~:text=Abstraction%20in%20Python%20is%20the,bought%20a%20new%20electronic%20gadget.

Private vs Public Variables

    With the PlayerCharacter class we created earlier, there are certain things that should not be altered. For example, the __init__ function, the
    run function, etc. These are all examples of things that should retain their value within the class and should not be altered outside of it.
    
    In Python, there technically are no true private variables, however, there is a way to get around this. We can use an underscore to denote
    a "private" variable, ex:
    
        class PlayerCharacter:
        def __init__(self, name, age):
            self._name = name
            self._age = age
            
    While it does not actually make the variable inaccessible outside of its scope, it does tell other developers that the variable should be 
    treated as if it were a real private variable.
    
For a discussion on Python's lack of true private variables:
https://stackoverflow.com/questions/1641219/does-python-have-private-variables-in-classes

Inheritance

    Inheritance, another pillar of OOP, allows new objects to take on the properties of existing properties, so you can inherit classes.
    
    Let's expand on the idea of us working for a gaming company developing a game about wizards. Imagine the boss wants us to include additional player
    types, such as archers, ogres, etc. We want to enforce that a user must be signed in to play, well, all of these player types will need that to be
    enforced as well... inheritance is useful as it enables us to quickly give our new objects the properties of our user object, ex:
        
        class User():
        def sign_in(self):
            print("logged in")
        
        class Wizard(User):
            pass
        
        class Archer(User):
            pass
        
        class Ogre(User):
            pass
            
     As you can see, we've passed the User class to each of our new objects via their parameters. This allows our new objects to inherit the sign
     in function.
     
     This is powerful because we can then expand on our new objects, while they are inheriting the function from our User class. ex:
     
        class Wizard(User):
            def __init__(self, name, power):
                self.name = name
                self.power = power
                
            def attack(self):
                print(f"attacking with power of {self.power}")
                
     As you can see, we have given Wizard some of its own functions... ok, but why does it matter, can't we do that regardless? Sure, but now we're 
     abstracting and keeping everything neat. We don't need to have the code for the "sign in" function within our Wizard class, because the wizard
     class is its own object, therefore having it inherit the function from User, and containing its own attributes/properties is much more organized
     and cleaner.
     
     If we instantiate a new instance of Wizard, we could use both the methods within our Wizard class and the methods within our User class:
     wizard1 = Wizard("Merlin", 50)
     wizard1.attack() -> outputs: attacking with the power of 50
     wizard.sign_in() -> outputs: logged in
     
For more information on inheritance:
https://www.w3schools.com/python/python_inheritance.asp
     
Polymporphism
    
    The last pillar of OOP is polymorphism. Polymorphism means "many forms". In Python, polymorphism relates to the way in which object classes
    can share the same method name but they can behave differently depending on what object calls them.
    
    Take the following code for example:
    
        class Wizard(User):
            def __init__(self, name, power):
            def attack(self):
                print(f"attacking with power of {self.power}")
                
        class Archer(User):
            def __init__(self, name, num_arrows):
            def attack(self):
                print(f"attack with arrows: arrows left - {self.num_arrows)")

    While the methods share the same name, "attack", they clearly yield different results when called by the different methods.
    
    An example of the power of polymorphism:
    
        wizard1 = Wizard("Merlin", 60)
        archer1 = Archer("Robin", 30)
        
        def player_attack(char):
            char.attack()
        
        player_attack(wizard1) -> outputs: attacking with power of 60
        player_attack(archer1) -> outputs: attacking with arrows: arrows left - 30
        
    As you can see, we instantiated new instances of our Wizard and Archer objects and also defined a new function. This function will invoke the
    attack method of our objects when passed in. Notice that the function returns wizard1.attack() or archer1.attack(), invoking the object's own
    attack method with their own output.
 
For more information on polymorphism:
https://www.programiz.com/python-programming/polymorphism

super()
    
    super() allows for us to share attributes from our parent class to its descendants (child classes). You could explicitly write these same attributes
    to your new objects, but if you ever have to alter it, you will have to make modifications in several objects rather than just the parent class.
    
    ex:
    
    Let's say your User class needs an email field as every user should have an email registered.
    
    class User(object):
        def __init__(self, email):
            self.email = email
            
        def sign_in(self):
            print("logged in")
            
    class Wizard(User):
        def __init__(self, name, power):
            super().__init__(email)
            self.name = name
            self.power = power
            
   The super() keyword essentially points up the class above the one invoking it. In this case, it is pointing at User. This is useful to us as it 
   allows us to enjoy the privileges of using the User class's email property without also having the responsibility of setting it within the Wizard
   class. This helps keep our code DRY (Don't Repeat Yourself)
   
For more information on super():
https://www.programiz.com/python-programming/methods/built-in/super

Introspection

    Since everything in Python is an object, this makes it easy for the compiler to recognize information about the objects.
    
    For example, calling print(dir(wizard1)) will display all information about an object, i.e; its properties, methods, etc.
    
Dunder Methods

    Dunder methods/magic methods, allows us to use Python specific functions on objects, created through our class. 
    
    class Toy():
        def __init__(self, color, age):
            self.color = color
            self.age = age
            self.my_dict = {
                "name": "Yoyo",
                "has_pets": False
            }
            
    action_figure = Toy("red", 0)
    print(action_figure.__str__()) -> is the same thing as print(str(action_figure))
    
    You can customize dunder methods (although it is not really recommended but there are special use cases), ex:
    
    def __str__(self):
        return f"{self.color}"
        
    def __len__(self):
        return 5
     
    def __getitem__(self, i):
        return self.my_dict[i]
        
    print(action_figure["name"]) -> prints Yoyo, thanks to the __getitem__ dunder method
    
For more information on dunder methods:
https://www.pythonmorsels.com/what-are-dunder-methods/

Multiple Inheritance
    
    Python allows objects to inherit properties, methods, and the link from multiple objects. For example:
        
        class User(object):
            def signed_in(self):
              print("logged in")

        class Wizard(User):
            def __init__(self, name, power):
               self.name = name
               self.power = power

            def attack(self):
                print(f"attacking with power of {self.power}")


        class Archer(User):
          def __init__(self, name, arrows):
            self.name = name
            self.arrows = arrows

          def arrow_attack(self):
            print(f"attacking with arrows: arrows left - {self.arrows}")

          def run(self):
            print("ran really fast")

        class HybridBorg(Wizard, Archer):
          def __init__(self, name, power, arrows):
            Archer.__init__(self, name, arrows)
            Wizard.__init__(self, name, power)
            
      As you can see, our new class "HybridBorg" inherits from both Wizard and Archer. We first initalize HybridBorg with the properties it needs,
      name, power, and arrows. Then we provide it the initialization for Archer and Wizard so that it may know how to inherit properties from each.
      
      We can use the new class and its inherited properties as such:
      
      character1 = HybridBorg("Hog", 60, 30)
      
      character1.signed_in()
      character1.attack()
      character1.arrow_attack()
      character1.run()
      
Link to Repl.it demonstrating multiple inheritance:
https://replit.com/@AutomationApe/MultipleInheritance#main.py

MRO - Method Resolution Order

    MRO is the flow of inheritance in objects. 
    
    Imagine you have classes A, B, C, D, and E:
    
    class A():
      def PrintNum():
        print(5)
        
    class B():
        pass
        
    class C(B, A):
        pass
        
    class D(C, B):
        pass
  
    class E(D, C):
        pass


    new_instance = D

    new_instance.PrintNum() -> outputs 5
        
    Class D for example, would follow this MRO:
    class D > class C > class B > class A > base object
    
    The reason for this is the order of the inheritance in the parameters. The MRO checks if there is anything in class D, since it passes, it then
    checks C, C passes, so it checks B, B also passes, so it checks A and inherits A's behavior.
 
Link to Repl.it demonstrating MRO:
https://replit.com/@AutomationApe/MRO

For more information on MRO:
https://www.educative.io/answers/what-is-mro-in-python
