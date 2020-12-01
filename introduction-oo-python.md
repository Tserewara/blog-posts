# A beginner-friendly introduction to object-oriented programming using Python

Programming can be a very pleasant activity. When we first start learning it, we feel like we can build anything. Some say that programming is the closest to having super powers. But, once we start building a more complex system, we can become very frustrated.

If you have ever tried to build a big system, you probably realized that its complexity can grow fast. When this happens, it's hard to keep on building it, and if we manage to finish it, we hope we never have to touch it again. Adding a new feature becomes a nightmare. Since you are reading this article, you already discovered that object-oriented programming is a way to build better software and tackle its complexity.

## What exactly is Object-Oriented Programming?

"Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code: data in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods)", says Wikipedia. In other words, it is a way to build software by creating objects and making them interact with each other to accomplish some goal. But what are objects? To understand, let's take some examples of the real world.

Imagine you are in a restaurant. A restaurant has a lot of objects like tables, chairs, cooks, customers, food and so on. These objects interact with each other. First, a customer walks into the restaurant and asks for a table. Then, an employee shows him/her a table. After that, the customer orders a lasagna. The waiter takes the order and gives the cook. The cook starts cooking. After a while, the dish is finished and then it is taken to the customer, who finally eats it and after that pays the bill.

We can easily recognize the objects in the system above because it's something concrete, that we all are familiar with. We have some information like dish and bill value, as well as behaviors like taking the order, cooking and paying the bill. An object-oriented software works similarly. It is composed by objects, that have data and behaviors attached to them. Therefore, our goal when building an object-oriented software is to identify the objects that make up the system and the way these objects behavior and affect each other.

## Data and behaviors are closely related in OO

One of the most important features of OOP is that data and behavior are grouped together. What does that mean? Let's take canned food as an example. Imagine you just bought a can of beans for lunch. To open it, you use the can opener that your grandfather gave  you. The beans are like the information you want to access. But to do that, you need a can opener that doesn't come with the can. In this case, the behavior (open the can) is not attached to the information (the beans). Now, imagine the can you bought has a self-opening system. Now, you don't need an external tool to perform the behavior of opening a can. In this case, the information (the beans) are attached to the behavior (open the can). This is how the object-oriented paradigm works. How does this translate to code?

This is a way we could implement it without OO.

```python
# without oo

can = "a lot of delicious beans"

def can_opener(can):
    return print(can)

can_opener(can)

# output
# a lot of delicious beans
```

Now, let's see how to do this with OO.

```python
# with oo

class CanOfBeans:
    def __init__(self, content):
        self.content = content

    def open(self):
        return print(self.content)
can_of_beans = CanOfBeans("a lot of delicious beans")

can_of_beans.open()

# output
# a lot of delicious beans
```

You may be thinking that this approach is longer and more complex. It's true. But the point is: we don't have to use OO in everything. We must understand when objects are needed and when they are not. As we considered earlier in this article, when we need to tackle the complexity of a system, OO may be a better choice over the typical procedural approach.

## OO is not only about programming

It is easy to point the objects in a restaurant because they are physical things. However, in programming objects are abstract ideas. They represent entities that may not exist in the real world. This makes the task of identifying the objects of a system a little harder. But there's no need for fear. We have some techniques to help us.

### Object-oriented analysis

Before we start building a house, we need to gather some requirements. How many rooms will there be in the house? How big must it be? Does it need a garage? The same happens (at least it should) before building software. We need to gather the requirements of the system. This way, we know exactly what we have to build. To do so, we need to speak to the person who asked us to build the system, or our client. Object-oriented analysis is the process of trying to figure out the objects and relationships between them based on a set of requirements. After this stage, we should have a set of requirements of what the system should do. For example, our client may asks us to build an on-line system to manage orders of a restaurant. Users of the system need to:

```markdown
- Order food
- Reserve a table
- Pay the bill
```

`Food`, `table` and `bill` are some objects of our system, while `reserve table `and `pay the bill` are behaviors. It is not so hard to do this, as long as we ask our client (who needs the software) the right questions. Not always the clients know exactly what they need. It's our job to help. It is also very important to point that we often need to change decisions made in this stage as we understand better the needs of the client. So, we don't have to worry too much about coming up with all the requirements at once. They will always change and we must be prepared to deal with this.

### Object-oriented design

Once we have the requirements, it's time to start the design. Object-oriented design is the process of laying out the requirements in a way we can implement them. It is like creating the blueprint of a house. In this stage, we name our objects and behaviors and represent them with some kind of visual language, usually UML.

### Object-oriented programming

Finally, after designing our system, we can implement it using whatever language we want. The result is a software that solves a problem of one or many users. Often times, unexperienced programmers jump ahead the stage of implementation without paying attention to the early stages of analysis and design. This can lead to a hard-to-maintain software or even prevent us from finishing it. Of course, not all projects need an exhaustive analysis or a detailed design. However, if you are working on a large project, meant to be used by thousands of users, you'll probably need to spend time in those stages. 

## Relationship between objects

As we said earlier, the OO paradigm relies on using objects to represent entities and making them interact with each other. How do we know the way the objects should interact? To address this, we must understand the kinds of relationships that exist between objects. Some analogies can help.

### Association

Imagine we are  still designing a system for a restaurant. Now, we have to add a feature to relate a cook and the cutlery he uses. Each cook can use one cutlery at a time. We have two objects so far: `Cook` and `Cutlery`. In this case, we have an `association` between the two objects, because a `Cook` **uses** a `Cutlery`, but they don't depend on each other to exist. Let's write some code.

```python
class Cook:
    def __init__(self, name):
        self.name = name
        self.cutlery = None


class Cutlery:
    def use(self):
        print('Cutlery is being used')

if __name__ == '__main__':
    simple_cutlery = Cutlery()
    
    cook = Cook('Pierre')
    cook.cutlery = simple_cutlery
    cook.cutlery.use()

# output
# Cutlery is being used
```

Note that even though `cook` uses `simple_cutlery`, they exist indepently. For example, if we delete `cook`, we are still able to use `simple_cutlery`.

```python
class Cook:
    def __init__(self, name):
        self.name = name
        self.cutlery = None


class Cutlery:
    def use(self):
        print('Cutlery is being used')

if __name__ == '__main__':
    simple_cutlery = Cutlery()
    
    cook = Cook('Pierre')
    cook.cutlery = simple_cutlery
    cook.cutlery.use()
    
    del cook
    
    simple_cutlery.use()

	# output
	# Cutlery is being used
```

### Aggregation

Aggregation is a more specific kind of association, where an object is part of another.  To illustrate that, now let's design a simple ingredient list feature for the recipes of our restaurant. We will need two classes: `Recipe` and `Ingredient`.

```python
class Recipe:
    def __init__(self):
        self.ingredients = []
    
    def add_ingredient(self, ingredient):
        self.ingredients.append(ingredient)
    
    def prepare(self):
        for ingredient in self.ingredients:
            print(f'Mixing {ingredient.name} to recipe')
    
class Ingredient:
    def __init__(self, name, qty):
        self.name = name
        self.qty = qty

if __name__ == '__main__':
    
    pizza = Recipe() # not a tasty pizza
    
    flour = Ingredient('flour', '3 cups')
    water = Ingredient('water', '1 cup')
    dry_yeast = Ingredient('dry yeast', '2 teaspoons')
    salt = Ingredient('salt', '2 teaspoons')
    
    pizza.add_ingredient(flour)
    pizza.add_ingredient(water)
    pizza.add_ingredient(dry_yeast)
    pizza.add_ingredient(salt)
    
    pizza.prepare()

    # output
    # Mixing flour to recipe
    # Mixing water to recipe
    # Mixing dry yeast to recipe
    # Mixing salt to recipe
```

In our example, `Recipe` aggregates objects of the class `Ingredient`. The `pizza` object can be created, but it cannot perform any task because it needs objects of type `Ingredient`. So, these two different kinds of objects can exist without each other, but the object of type `Recipe` only works properly when it aggregates ingredients. That's what we call aggregation: **objects exist independently**, but one type **depend on the other to exist**.

### Composition

Composition is also a kind of association. But in this case, an object owns another. This way, if owner object ceases to exist, the objects that compose it also do. Let's use our restaurant example again. Imagine that we need to keep track of the orders our customers make. An order is made up by the name of the customer and the dishes the client orders. Since it doesn't make sense to have an order without a dish, we will create the dish object inside the order. Let's do it.

```python
class Dish:
    def __init__(self, name, value):
        self.name = name
        self.value = value


class Order:
    def __init__(self, customer_name):
        self.customer_name = customer_name
        self.dishes = []
    
    def add_dish(self, dish_name, dish_value):
        dish = Dish(dish_name, dish_value) # the dish will only exist inside Order
        self.dishes.append(dish)


if __name__ == '__main__':
    
    order1 = Order('John Doe')
    
    order1.add_dish('Lasagna', '$20')
    order1.add_dish('Pizza', '$25')
    order1.add_dish('Risotto', '$30')
    
    
    del order1 # deleting order1 will also delete all the dishes 
```

When we create `order1` and call `add_dish`, objects of the type `Dish` are created and put somewhere in memory. After we delete `order1` , Python will automatically delete the dishes (its garbage collector does the dirty job). How can we see that happening?  Let's change our `Dish` class a little bit and add a method  that will allow us to see when it is deleted.:

```python
class Dish:
    def __init__(self, name, value):
        self.name = name
        self.value = value

    def __del__(self): # this special method is run when we call del
        print(f'The object {self.name} was deleted')

class Order:
    def __init__(self, customer_name):
        self.customer_name = customer_name
        self.dishes = []
    
    def add_dish(self, dish_name, dish_value):
        dish = Dish(dish_name, dish_value) # the dish will only exist inside Order
        self.dishes.append(dish)


if __name__ == '__main__':
    
    order1 = Order('John Doe')
    
    order1.add_dish('Lasagna', '$20')
    order1.add_dish('Pizza', '$25')
    order1.add_dish('Risotto', '$30')
    
    print("Before deleting order")
    print()

    print("After deleting order")
    print()
    
    del order1 # deleting order1 will also delete all the dishes
```

The output will be:

```markdown
Before deleting order

After deleting order

The object Risotto was deleted
The object Pizza was deleted
The object Lasagna was deleted
```

As we saw, in composition, the relationship between objects is stronger since the inner objects depend on the owner to exist.

### Inheritance

Inheritance is the most famous and overused relationship in OO. In this relationship, one class inherits data and behaviors from another. The class that provides them is called parent and the one that inherits is called child. This relationship is also referred to as an *is-a* relationship, because one class is of the type of the other. Let's use our restaurant one more time to illustrate inheritance. Imagine we have to design a delivery system for our restaurant. We can delivery a lot of dishes as well as other items as sodas, wines etc. We have to represent all the kinds of products the restaurant sells with a class. Let's call it `Product`. Also, imagine we have to add a method in the product to show how much of it there still is in stock.

```python
class Product:
    def __init__(self, name, price, stock)
    	self.id = id
        self.name = name
        self.price = price
        self.stock = stock
    
    def stock_qty(self):
        self.stock.show_qty(self.id)        
```

In our restaurant, there is a lot of products. So, we can inherit from `Product` to create them.

```python
class Product:
    def __init__(self, name, price, stock)
    	self.id = id
        self.name = name
        self.price = price
        self.stock = stock
    
    def stock_qty(self):
        self.stock.show_qty(self.id)

class Pizza(Product):
    pass

class Wine(Product):
    pass

class Lasagna(Product):
    pass
```

Note we only need to pass `Product` to the new class to inherit from it. We don't need to implement anything. We already have all the data and behavior of `Product` in `Pizza`, `Wine` and `Lasagna`. Inheritance is a very powerful technique. Even though, many people tend to overuse it since it allows to share functionalities between classes. That's not the best reason to use inheritance. More about it in a future article (if you are really curious, you can read about **polymorphism** and see what it has to do with inheritance).

## Summary

- Association - a class uses another, but it doesn't needs it to exist

- Aggregation - a class needs another to work but not to exist

- Composition - a class is part of another and when the container class is deleted, its composing classes also are

- Inheritance - a class is another, since it inherits from a parent class

  

It takes time and effort to get the hang of OO. So, don't feel discouraged if you still don't understand it well. Keep learning and trying to apply it in your projects and things will become more and more clear. 