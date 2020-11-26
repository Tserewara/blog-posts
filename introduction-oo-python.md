# An Introduction to Object-oriented programming in Python

Programming can be a very pleasant activity. When we first start learning it, we feel like we can build anything. Some say that programming is the closest to having super powers. But, once we start building a more complex system, we can become very frustrated.

If you have ever tried to build a big system, you probably realized that its complexity can grow fast.
When this happens, it's hard to keep on building it, and if we manage to finish it, we hope we never have to touch it again. Adding a new feature becomes a nightmare. Since you are reading this article, you already discovered that object-oriented programming is a way to build better software and tackle its complexity.

## What exactly is Object-Oriented Programming?

"Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code: data in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods)", says Wikipedia. In other words, it is a way to build software by creating objects and making them interact with each other to accomplish some goal. But what are objects? To understand, let's take some examples of the real world.

Imagine you are in a restaurant. A restaurant has a lot of objects like tables, chairs, cooks, customers, food and so on. These objects interact with each other. First, a customer walks into the restaurant and asks for a table. Then, an employee shows him/her a table. After that, the customer orders a lasagna. The waiter takes the order and gives the cook. The cook starts cooking. After a while, the dish is finished and then it is taken to the customer, who finally eats it and after that pays the bill.

We can easily recognize the objects in the system above because it's something concrete, that we all are familiar with. We have some information like dish and bill value, as well as behaviors like taking the order, cooking and paying the bill. An object-oriented software works similarly. It is composed by objects, that have data and behaviors attached to them. Therefore, our goal when building an object-oriented software is to identify the objects that make up the system and the way these objects behavior and affect each other.

## Data and behaviors are closely related in OO

One of the most important features of OOP is that data and behavior are grouped together. What does that mean? Let's take canned food as an example. Imagine you just bought a can of beans for lunch. To open it, you use the can opener that your grandfather gave  you. The beans are like the information you want to access. But to do that, you need a can opener that doesn't come with the can. In this case, the behavior (open the can) is not attached to the information (the beans). Now, imagine the can you bought has a self-opening system. Now, you don't need an external tool to perform the behavior of opening a can. In this case, the information (the beans) are attached to the behavior (open the can). This is how the object-oriented paradigm works. How does this translate to code?

This is how we would implement it without OO.

```py
# without oo

can_of_beans = "a lot of delicious beans"""

def can_opener(can):
    return print(can)
```

Now, let's see how to do this with OO.

```py
# with oo

class CanOfBeans:
    def __init__(self, content):
        self.content = content

    def open(self):
        return print(self.content)
```

You may be thinking that this approach is longer and more complex. It's true. But the point is: we don't have to use OO in everything. We must understand when objects are needed and when they are not. As we considered earlier in this article, when we need to tackle the complexity of a system, OO may be a better choice over the typical prodecural approach.

## How do we identify objects and their relationships?

It is easy to point the objects in a restaurant because they are physical things. However, in programming objects are abstract ideas. They represent entities that may not exist in the real world. This makes the task of identifying the objects of a system a little harder. But there's no need for fear.

### Object-oriented analysis

Before we start building a house, we need to gather some requirements. How many rooms will there be in the house? How big must it be? Does it need a garage? The same happens (at least it should) before building software. We need to gather the requirements of the system. This way, we know exactly what we have to build. To do so, we need to speak to the person who asked us to build the system, or our client. Object-oriented analysis is the process of trying to figure out the objects and relatioship between them based on a set of requirements. After this stage, we should have a set of requirements of what the system should do. For example, our client may asks us to build an online system to manage orders of a restaurant. Users of the system need to be able to:

* Order food
* Reserve a table
* Pay the bill

**Food**, **table** and **bill** are some objects of our system, while *reserve table* and *pay the bill* are behaviors. It is not so hard to do this, as long as we ask our client (who needs the software) the right questions. Not always the clients know exactly what they need. It's our job to help. It is also very important to point that we often need to change decisions made in this stage as we understand better the needs of the client. So, we don't have to worry too much with coming up with all the requirements at once. They will always change and we must be prepared to deal with this.

### Object-oriented design

Once we have the requirements, it's time to start the design. Object-oriented design it the process of laying out the requirements in a way we can implement. It is like creating the blueprint of a house. In this stage, we name our objects and behaviors and represent them with some kind of visual language, usually UML.