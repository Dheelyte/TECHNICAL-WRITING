---
title: "Write Better Code With Python Comprehensions"
seoTitle: "What is Python Comprehension: Lists, dictionaries and sets."
datePublished: Mon Aug 14 2023 16:39:23 GMT+0000 (Coordinated Universal Time)
cuid: cllb3o17e00020ala02yuhnqa
slug: python-comprehension-list-dicts-sets
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/zGuBURGGmdY/upload/130ede51a665e0e48ab3b372c0541f34.jpeg
tags: python, data-structures

---

In versions 2.7 and 3.0, Python, among other features, released the features: List Comprehension, Dictionary comprehension and the closely related Set comprehension. These features made it easier to generate lists, dictionaries and sets, in a cleaner, more concise and more efficient way.

In the subsequent paragraphs, I will show you how using comprehensions — instead of the traditional method of creating data structures — can help you write concise and more efficient codes.

### LIST COMPREHENSION

The following code is the traditional way of creating lists in Python:

```python
>>> list_object = []
... for i in range(10):
...     list_object.append(i)
>>> list_object
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

This code can be drastically improved by using Python List Comprehension:

```python
>>> [i for i in range(10)]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

> A list comprehension consists of brackets containing an expression followed by a `for` clause, then zero or more `for` or `if` clauses. The result will be a new list resulting from evaluating the expression in the context of the `for` and `if` clauses which follow it — python.org

Python List comprehension also supports `if` clauses. The following is an example of list comprehension that only includes even numbers:

```python
>>> [i for i in range(10) if i % 2 == 0]
[0, 2, 4, 6, 8]
```

#### Nested List Comprehension

List comprehension also supports multiple `for` clauses:

```python
>>> [[i, j] for i in range(1) for j in range(7) if i != j]
[[0, 1], [0, 2], [0, 3], [0, 4], [0, 5], [0, 6]]
```

### DICTIONARY COMPREHENSIONS

Also known as dict comprehension, dictionary comprehensions generate dictionaries from key, value expressions.

The following is a simple example of a dict comprehension:

```python
>>> {i: i*2 for i in range(5)}
{0: 0, 1: 2, 2: 4, 3: 6, 4: 8}
```

The example above creates a dictionary with each iteration of the range object as its key, and its multiplication by **2** as its value. In dictionary comprehension, the key-value pair is separated by a colon.

Just like list comprehensions, dict comprehensions can also contain multiple `for` and `if` clauses. Let’s look at an example:

```python
>>> {i: j for i in range(5) for j in range(5)}
{0: 4, 1: 4, 2: 4, 3: 4, 4: 4}

>>> {i: j for i in range(5) for j in range(5) if i != 2}
{0: 4, 1: 4, 3: 4, 4: 4}
```

Note that in this code, Python automatically eliminated duplicate keys while generating this dictionary.

### SET COMPREHENSIONS

Python also supports set comprehension.

Python sets are similar to Python lists except that sets use curly braces instead of brackets and sets don’t contain duplicate elements.

The following are ways of creating a set:

```python
>>> set_object = set(['a', 'b', 'c', 'b'])
{'a', 'b', 'c'}

>>> set_object = {'a', 'b', 'c', 'a'}
{'a', 'b', 'c'}
```

Note that in the above example, duplicate elements have been removed because a set cannot contain duplicate elements.

The following is an example of generating a set using set comprehension:

```python
>>> {elem for elem in 'abcda'}
{'a', 'b', 'c', 'd'}
```

Similar to list and dict comprehension, set comprehension also supports **if** clauses:

```python
>>> {elem for elem in 'abcda' if elem != 'c'}
{'a', 'b', 'd'}
```

### CONCLUSION

In this article, we looked at what list, dictionary and set comprehensions are and how they can help us write better, cleaner and more concise code. Using it in your projects also lets your code readers know that you are up-to-date with the current trends in Python programming.

Thanks for reading. Till next time, keep building. 🚀

Reach me on [GitHub](https://github.com/Dheelyte), [Twitter](https://twitter.com/DelightGbolahan), [Linkedin](https://www.linkedin.com/in/delight-olagbuji)

I’m open to Software Engineering roles, contracts and project collaborations.