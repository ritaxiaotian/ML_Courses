=====================================================================
Assignment: Project 2: Yelp Maps
OK, version v1.13.11
=====================================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Unlocking tests

At each "? ", type what you would expect the output to be.
Type exit() to quit

---------------------------------------------------------------------
Problem 0 > Suite 1 > Case 1
(cases remaining: 5)

-- Already unlocked --

---------------------------------------------------------------------
Problem 0 > Suite 1 > Case 2
(cases remaining: 4)

-- Already unlocked --

---------------------------------------------------------------------
Problem 0 > Suite 1 > Case 3
(cases remaining: 3)

-- Already unlocked --

---------------------------------------------------------------------
Problem 0 > Suite 1 > Case 4
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 0 > Suite 2 > Case 1
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 0 unlocked.

---------------------------------------------------------------------
Problem 1 > Suite 1 > Case 1
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 1 unlocked.

---------------------------------------------------------------------
Problem 2 > Suite 1 > Case 1
(cases remaining: 2)

>>> from abstractions import *
>>> import abstractions
>>> soda_reviews = [make_review('Soda', 4.5),
...                 make_review('Soda', 4)]
>>> soda = make_restaurant('Soda', [127.0, 0.1],
...                        ['Restaurants', 'Breakfast & Brunch'],
...                        1, soda_reviews)
>>> restaurant_name(soda)
? 'Soda'
-- OK! --

>>> restaurant_location(soda)
?  [127.0, 0.1]
-- OK! --

>>> restaurant_categories(soda)
?  ['Restaurants', 'Breakfast & Brunch']
-- OK! --

>>> restaurant_price(soda)
? 1
-- OK! --

>>> restaurant_ratings(soda)
? [4.5,4]
-- OK! --

---------------------------------------------------------------------
Problem 2 > Suite 2 > Case 1
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 2 unlocked.

---------------------------------------------------------------------
Problem 3 > Suite 1 > Case 1
(cases remaining: 7)

Q: Which of the following types of values can be passed as
an argument to distance?
Choose the number of the correct choice:
0) number; e.g. 1
1) string of a pair; e.g. '[1, 1]'
2) restaurant; e.g. make_restaurant('A', [1, 1], ['Food'], 1, [])
3) pair; e.g. [1, 1]
? 3
-- OK! --

---------------------------------------------------------------------
Problem 3 > Suite 1 > Case 2
(cases remaining: 6)

Q: Consider the list l = [[4, 1], [-3, 2], [5, 0]]. Which of
the choices below for fn would make min(l, key=fn) evaluate
to [4, 1]?
Choose the number of the correct choice:
0) sum
1) lambda x, y: abs(x - y)
2) lambda x, y: pow(-x, y)
3) lambda x: abs(x[0] - x[1])
? 3
-- OK! --

---------------------------------------------------------------------
Problem 3 > Suite 2 > Case 1
(cases remaining: 5)

>>> import tests.test_functions as test
>>> from recommend import *
>>> distance([0, 0], [3, 4]) # should be a decimal
? 5.0
-- OK! --

>>> distance([6, 1], [6, 1]) # should be a decimal
? 0.0
-- OK! --

>>> distance([-2, 7], [-3.5, 9]) # should be a decimal
? 2.5
-- OK! --

---------------------------------------------------------------------
Problem 3 > Suite 2 > Case 2
(cases remaining: 4)

>>> import tests.test_functions as test
>>> from recommend import *
>>> find_closest([6, 1],
...              [[1, 5], [3, 3]])
? [3,3]
-- OK! --

>>> find_closest([1, 6],
...              [[1, 5], [3, 3]])
? [1,5]
-- OK! --

---------------------------------------------------------------------
Problem 3 > Suite 2 > Case 3
(cases remaining: 3)

>>> import tests.test_functions as test
>>> from recommend import *
>>> find_closest([0, 0],
...              [[-2, 0], [2, 0]])
? [-2,0]
-- OK! --

>>> find_closest([0, 0],
...              [[1000, 1000]])
? [1000,1000]
-- OK! --

---------------------------------------------------------------------
Problem 3 > Suite 2 > Case 4
(cases remaining: 2)

>>> import tests.test_functions as test
>>> from recommend import *
>>> # Be sure to use the distance function!
>>> find_closest([0, 0],
...              [[2, 2], [0, 3]])
? [2,2]
-- OK! --

>>> find_closest([0, 0],
...              [[5, 5], [2, 7]])
? [5,5]
-- OK! --

---------------------------------------------------------------------
Problem 3 > Suite 2 > Case 5
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 3 unlocked.

---------------------------------------------------------------------
Problem 4 > Suite 1 > Case 1
(cases remaining: 12)

Q: If centroids is [[-1, 1], [5, -1], [1, 10], [-1, -10]],
to which centroid will [6, 0] be associated?
Choose the number of the correct choice:
0) [5, -1]
1) [-1, 1]
2) [-1, -10]
3) [1, 10]
? 0
-- OK! --

---------------------------------------------------------------------
Problem 4 > Suite 1 > Case 2
(cases remaining: 11)

Q: If centroids is [[1, 1], [1, -1], [-1, 1], [-1, -1]],
to which centroid will [0, 0] be associated?
Choose the number of the correct choice:
0) [-1, 1]
1) [1, 1]
2) [1, -1]
3) [-1, -1]
? 1
-- OK! --

---------------------------------------------------------------------
Problem 4 > Suite 2 > Case 1
(cases remaining: 10)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 2 > Case 2
(cases remaining: 9)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 2 > Case 3
(cases remaining: 8)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 2 > Case 4
(cases remaining: 7)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 2 > Case 5
(cases remaining: 6)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 3 > Case 1
(cases remaining: 5)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 3 > Case 2
(cases remaining: 4)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 3 > Case 3
(cases remaining: 3)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 3 > Case 4
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 4 > Suite 3 > Case 5
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 4 unlocked.

---------------------------------------------------------------------
Problem 5 > Suite 1 > Case 1
(cases remaining: 4)

>>> from recommend import *
>>> cluster1 = [
...     make_restaurant('A', [-3, -4], [], 3, [make_review('A', 2)]),
...     make_restaurant('B', [1, -1],  [], 1, [make_review('B', 1)]),
...     make_restaurant('C', [2, -4],  [], 1, [make_review('C', 5)]),
... ]
>>> find_centroid(cluster1) # should be a pair of decimals
? [0,-3]
-- Not quite. Try again! --

? [0.0,-3.0]
-- OK! --

---------------------------------------------------------------------
Problem 5 > Suite 1 > Case 2
(cases remaining: 3)

-- Already unlocked --

---------------------------------------------------------------------
Problem 5 > Suite 2 > Case 1
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 5 > Suite 2 > Case 2
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 5 unlocked.

---------------------------------------------------------------------
Problem 6 > Suite 1 > Case 1
(cases remaining: 8)

Q: What are we using the k-means algorithm to achieve?
Choose the number of the correct choice:
0) Predicting the ratings for k restaurants.
1) Finding the mean rating of restaurants for k categories.
2) Grouping the restaurants into k clusters by location.
? 2
-- OK! --

---------------------------------------------------------------------
Problem 6 > Suite 1 > Case 2
(cases remaining: 7)

Q: What is the first step of the k-means algorithm?
Choose the number of the correct choice:
0) Randomly initialize k centroids.
1) Find the centroid (average position) of each cluster.
2) Create a cluster for each centroid consisting of all elements closest to
   that centroid.
? 0
-- OK! --

---------------------------------------------------------------------
Problem 6 > Suite 1 > Case 3
(cases remaining: 6)

Q: After we randomly initialize k centroids, what is the first step
of the iterative portion of the k-means algorithm?
Choose the number of the correct choice:
0) Randomly reassign centroids.
1) Find the centroid (average position) of each cluster.
2) Group restaurants by latitude.
3) Create a cluster for each centroid consisting of all elements closest to
   that centroid.
? 
