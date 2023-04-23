# ASSGNMNT19

Number 1 -

Question -
Make a class called Thing with no contents and print it. Then, create an object called example from this class and also print it. Are the printed values the same or different?

Answer -
class Thing:
    pass
print(Thing)
<class '__main__.Thing'>
example = Thing()
print(example)
<__main__.Thing object at 0x000002B5D9C00D00>
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 2 -

Question -
Create a new class called Thing2 and add the value 'abc' to the letters class attribute. Letters should be printed.

Answer -
class Thing2:
    letters = 'abc'
print(Thing2.letters)
abc
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 3 -

Question -
Make yet another class called, of course, Thing3. This time, assign the value 'xyz' to an instance (object) attribute called letters. Print letters. Do you need to make an object from the class to do this?

Answer -
class Thing3:
    def __init__(self):
        self.letters = 'xyz'
The variable letters belongs to any objects made from Thing3, not the Thing3 class itself:

print(Thing3.letters)
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-7-6f5d5916809a> in <module>
----> 1 print(Thing3.letters)

AttributeError: type object 'Thing3' has no attribute 'letters'
something = Thing3()
print(something.letters)
xyz
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 4 -

Question -
Create an Element class with the instance attributes name, symbol, and number. Create a class object with the values 'Hydrogen,' 'H,' and 1.

Answer -
class Element:
    def __init__(self, name, symbol, number):
        self.name = name
        self.symbol = symbol
        self.number = number
hydrogen = Element('Hydrogen', 'H', 1)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 5 -

Question -
Make a dictionary with these keys and values: 'name': 'Hydrogen', 'symbol': 'H', 'number': 1. Then, create an object called hydrogen from class Element using this dictionary.

Answer -
#Starting with the dictionary:
el_dict = {'name': 'Hydrogen', 'symbol': 'H', 'number': 1}
#Creating object called hydrogen from class Element using el_dict
hydrogen = Element(el_dict['name'], el_dict['symbol'], el_dict['number'])
hydrogen.name
'Hydrogen'
We can also initialize the object directly from the dictionary, because its key names match the arguments to "init"

hydrogen = Element(**el_dict)
hydrogen.name
'Hydrogen'
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 6 -

Question -
For the Element class, define a method called dump() that prints the values of the object’s attributes (name, symbol, and number). Create the hydrogen object from this new definition and use dump() to print its attributes.

Answer -
class Element:
    def __init__(self, name, symbol, number):
        self.name = name
        self.symbol = symbol
        self.number = number
    def dump(self):
        print('name=%s, symbol=%s, number=%s' %(self.name, self.symbol, self.number))
hydrogen = Element(**el_dict)
hydrogen.dump()
name=Hydrogen, symbol=H, number=1
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 7 -

Question -
Call print(hydrogen). In the definition of Element, change the name of method dump to str, create a new hydrogen object, and call print(hydrogen) again.

Answer -
print(hydrogen)
<__main__.Element object at 0x000002B5DB25E760>
class Element:
    def __init__(self, name, symbol, number):
        self.name = name
        self.symbol = symbol
        self.number = number
    def __str__(self):
        return ('name=%s, symbol=%s, number=%s' %(self.name, self.symbol, self.number))

hydrogen = Element(**el_dict)
print(hydrogen)
name=Hydrogen, symbol=H, number=1
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 8 -

Question -
Modify Element to make the attributes name, symbol, and number private. Define a getter property for each to return its value.

Answer -
class Element:
    def __init__(self, name, symbol, number):
        self.__name = name
        self.__symbol = symbol
        self.__number = number
    @property    
    def name(self):
        return self.__name
    @property
    def symbol(self):
        return self.__symbol
    @property
    def number(self):
        return self.__number
hydrogen = Element('Hydrogen', 'H', 1)
hydrogen.name
'Hydrogen'
hydrogen.symbol
'H'
hydrogen.number
1
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 9 -

Question -
Define three classes: Bear, Rabbit, and Octothorpe. For each, define only one method: eats(). This should return 'berries' (Bear), 'clover' (Rabbit), or 'campers' (Octothorpe). Create one object from each and print what it eats.

Answer -
class Bear:
    def eats(self):
        return 'berries'
    
class Rabbit:
    def eats(self):
        return 'clover'

class Octothorpe:
    def eats(self):
        return 'campers'
    
b = Bear()
r = Rabbit()
o = Octothorpe()
print(b.eats())
berries
print(r.eats())
clover
print(o.eats())
campers
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Number 10 -

Question -
Define these classes: Laser, Claw, and SmartPhone. Each has only one method: does(). This returns 'disintegrate' (Laser), 'crush' (Claw), or 'ring' (SmartPhone). Then, define the class Robot that has one instance (object) of each of these. Define a does() method for the Robot that prints what its component objects do.

Answer -
class Laser:
    def does(self):
        return 'disintegrate'

class Claw:
    def does(self):
        return 'crush'
    
class SmartPhone:
    def does(self):
        return 'ring'
    
class Robot:
    def __init__(self):
        self.laser = Laser()
        self.claw = Claw()
        self.smartphone = SmartPhone()
        
    def does(self):
        return '''I have many attachments:
        My laser, to %s.
        My claw, to %s.
        My smartphone, to %s.''' % (self.laser.does(),self.claw.does(),self.smartphone.does() )
robbie = Robot()
print( robbie.does())
I have many attachments:
        My laser, to disintegrate.
        My claw, to crush.
        My smartphone, to ring.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
