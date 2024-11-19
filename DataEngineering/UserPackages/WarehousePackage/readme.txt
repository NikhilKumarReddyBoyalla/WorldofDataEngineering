This is one of the interview questions at FAANG/ MAANG companies that rejected me right after the very first round.
And the question goes like this:

Implement a package for a warehouse scenario. The output must return all the entities that weigh more than 50 kgs



-->Group of input lists were given which held either the container details or the container and box details or both 
--> Each container can have a box that weighs something or the container with multiple boxes can also be summed up to 50 + kgs 
--> For this I would first cover concepts of OOP in python.

Starting with OOPS concepts 
===========================

Key components of Object oriencted programming are 
1. Object
2. Class
3. Encapsulation
4. Polymorphism
5. Inheritence 



Class:
======

-> It is a blueprint for objects. It defines attributes and functions of any object that is about to be derives as that class type

eg: Class EntityBase:
        def __init__(self, entity_id:int, entity_name:String, entity_type:String, isWeigheted:Bool): #this is called constructor. This sets the value of derived objects to the necessary attributes of the class structure. mapping
            self.entity_id = entity_id
            self.entity_name = entity_name
            self.entity_type = entity_type
            self.isWeigheted = isWeigheted

        #Function that returns the id and name of the object if it is a weighted entity
        def is_weighted_entity(self):
            if self.isWeighted:
                return (entity_id, entity_name)
            return None #explicitly return None if the condition is not multiple

Object: 
=======

-> Is is a instance of a class. A possible existance of a thing that has features of Class blueprint

eg: entity1 = EntityBase(1, 'ContainerA', 'Container', True) # this means the container has all the attributes that it can map to the attribute list defined in class blueprint
    entity1.is_weighted_entity() #this object entity1 can define the attributes of type class and can call all the functions that are declared in that class



Encapsulation:
=============

-> Encapsulation restricts the direct access to the object data by using private/ protected attributes with methods (getter/setter)
-> It basically restricts the access of the attributes of the object directly when declared as private __/protected _
-> These private/ protected objects can only be accessed/ modifies using getter and setter methods of the class blueprint itself


class EntityBase:
        def __init__(self, entity_id:int, entity_name:str, entity_type:str, isWeighted:bool, Weight:int): #this is called constructor. This sets the value of derived objects to the necessary attributes of the class structure. mapping
            self.__entity_id = entity_id
            self.entity_name = entity_name
            self.entity_type = entity_type
            self.__isWeighted = isWeighted
            self.__Weight = Weight

        #Function that returns the id and name of the object if it is a weighted entity
        def is_weighted_entity(self):
            if self.__isWeighted:
                return (self.__entity_id, self.entity_name)
            return None #explicitly return None if the condition is not multiple

Object1 = EntityBase(1, 'A', 'Container', True, 175)
Object1.is_weighted_entity()


Abstraction : 
===========

-> Hiding the internal details or implementation of a class and exposing only the essential features or functionalities

eg:
#Implementing code with both abstraction and encapsulation 

from abc import ABC, abstractmethod

class EntityBase(ABC):

    @abstractmethod 
    def isContainer(self, entity_type):
        pass 

    @abstractmethod
    def is_weighted_entity(self, entity_type):
        pass


class container(EntityBase):

    def isContainer(self, entity_type):
        if (self.entity_type == 'Container'):
            return self.entity_type
        return None
    
    def is_weighted_entity(self):
        return 'Correct'



if __name__ == "__main__":
    def checkIsContainer(isContainer : EntityBase,  entity_type):
        isContainer.isContainer(entity_type)
    
    entity1 = container()
    entity1.entity_type = "Container"
    print (checkIsContainer(entity1, entity1.entity_type))
    print(entity1.is_weighted_entity())


Inheritence:
============

It is mainly there to ensure code reusability
One class can inherit the properties and behavior of another class
-single
-multiple
-multilevel
-hierarical
-Hybrid
-constructor