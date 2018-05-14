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
? 3
-- OK! --

---------------------------------------------------------------------
Problem 6 > Suite 1 > Case 4
(cases remaining: 5)

Q: What is the second step of the iterative portion of the k-means
algorithm?
Choose the number of the correct choice:
0) Randomly reassign centroids.
1) Group restaurants by latitude.
2) Find the centroid (average position) of each cluster.
3) Create a cluster for each centroid consisting of all elements closest to
   that centroid.
? 2
-- OK! --

---------------------------------------------------------------------
Problem 6 > Suite 2 > Case 1
(cases remaining: 4)

-- Already unlocked --

---------------------------------------------------------------------
Problem 6 > Suite 2 > Case 2
(cases remaining: 3)

-- Already unlocked --

---------------------------------------------------------------------
Problem 6 > Suite 2 > Case 3
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 6 > Suite 2 > Case 4
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 6 unlocked.

---------------------------------------------------------------------
Problem 7 > Suite 1 > Case 1
(cases remaining: 6)

Q: What does a predictor function returned by
find_predictor do?
Choose the number of the correct choice:
0) returns the r_squared value
1) takes in a restaurant and returns the predicted location of
   that restaurant
2) takes in a restaurant and returns the predicted rating for that
   restaurant
? 2
-- OK! --

---------------------------------------------------------------------
Problem 7 > Suite 1 > Case 2
(cases remaining: 5)

Q: What does the list xs represent?
Choose the number of the correct choice:
0) the restaurants in restaurants
1) the restaurants reviewed by user
2) the names of restaurants in restaurants
3) the extracted feature value for each restaurant in restaurants
? 3
-- OK! --

---------------------------------------------------------------------
Problem 7 > Suite 1 > Case 3
(cases remaining: 4)

Q: What does the list ys represent?
Choose the number of the correct choice:
0) the names for the restaurants in restaurants
1) user's ratings for the restaurants in restaurants
2) the average rating for the restaurants in restaurants
3) the names for the restaurants reviewed by user
 1
-- OK! --

---------------------------------------------------------------------
Problem 7 > Suite 2 > Case 1
(cases remaining: 3)

-- Already unlocked --

---------------------------------------------------------------------
Problem 7 > Suite 2 > Case 2
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 7 > Suite 2 > Case 3
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 7 unlocked.

---------------------------------------------------------------------
Problem 8 > Suite 1 > Case 1
(cases remaining: 11)

Q: In best_predictor, what does the variable reviewed represent?
Choose the number of the correct choice:
0) a list of ratings for restaurants reviewed by the user
1) a list of restaurants reviewed by the user
2) a list of all possible restaurants
? 1
-- OK! --

---------------------------------------------------------------------
Problem 8 > Suite 1 > Case 2
(cases remaining: 10)

Q: Given a user, a list of restaurants, and a feature function, what
does find_predictor from Problem 7 return?
Choose the number of the correct choice:
0) a predictor function and its r_squared value
1) a predictor function
2) a restaurant
3) an r_squared value
? 0
-- OK! --

---------------------------------------------------------------------
Problem 8 > Suite 1 > Case 3
(cases remaining: 9)

Q: After computing a list of [predictor, r_squared] pairs,
which predictor should we select?
Choose the number of the correct choice:
0) the first predictor in the list
1) the predictor with the highest r_squared value
2) the predictor with the lowest r_squared value
3) an arbitrary predictor
? ? 1
-- OK! --

---------------------------------------------------------------------
Problem 8 > Suite 2 > Case 1
(cases remaining: 8)

-- Already unlocked --

---------------------------------------------------------------------
Problem 8 > Suite 2 > Case 2
(cases remaining: 7)

-- Already unlocked --

---------------------------------------------------------------------
Problem 8 > Suite 2 > Case 3
(cases remaining: 6)

-- Already unlocked --

---------------------------------------------------------------------
Problem 8 > Suite 2 > Case 4
(cases remaining: 5)

-- Already unlocked --

---------------------------------------------------------------------
Problem 8 > Suite 3 > Case 1
(cases remaining: 4)

-- Already unlocked --

---------------------------------------------------------------------
Problem 8 > Suite 3 > Case 2
(cases remaining: 3)

-- Already unlocked --

---------------------------------------------------------------------
Problem 8 > Suite 3 > Case 3
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 8 > Suite 3 > Case 4
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 8 unlocked.

---------------------------------------------------------------------
Problem 9 > Suite 1 > Case 1
(cases remaining: 5)

Q: rate_all returns a dictionary. What are the keys of this dictionary?
Choose the number of the correct choice:
0) restaurant ratings
1) restaurant names
2) restaurants
? 
? 1
-- OK! --

---------------------------------------------------------------------
Problem 9 > Suite 1 > Case 2
(cases remaining: 4)

Q: What are the values of the returned dictionary?
Choose the number of the correct choice:
0) numbers - mean restaurant ratings
1) lists - list of all restaurant ratings
2) numbers - a mix of user ratings and predicted ratings
3) numbers - user ratings only
4) numbers - predicted ratings only
? 2
-- OK! --

---------------------------------------------------------------------
Problem 9 > Suite 1 > Case 3
(cases remaining: 3)

Q: In rate_all, what does the variable reviewed represent?
Choose the number of the correct choice:
0) a list of restaurants reviewed by the user
1) a list of ratings for restaurants reviewed by the user
2) a list of all possible restaurants
? 0
-- OK! --

---------------------------------------------------------------------
Problem 9 > Suite 2 > Case 1
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 9 > Suite 3 > Case 1
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 9 unlocked.

---------------------------------------------------------------------
Problem 10 > Suite 1 > Case 1
(cases remaining: 5)

Q: Given a restaurant, what does restaurant_categories in
abstractions.py return?
Choose the number of the correct choice:
0) a list of numbers (ratings)
1) a single string (category)
2) a single number (rating)
3) a list of strings (categories)
? 3
-- OK! --

---------------------------------------------------------------------
Problem 10 > Suite 1 > Case 2
(cases remaining: 4)

Q: When does a restaurant match a search query?
Choose the number of the correct choice:
0) if the query string is mentioned in the restaurant's reviews
1) if the query string is equal to the restaurant's categories
2) if the query string is a substring of the restaurant's name
3) if the query string is one of the restaurant's categories
? 3
-- OK! --

---------------------------------------------------------------------
Problem 10 > Suite 1 > Case 3
(cases remaining: 3)

Q: What type of object does search return?
Choose the number of the correct choice:
0) a dictionary that maps restaurant names (strings) to restaurants
1) a list of restaurants
2) a dictionary that maps restaurant categories (strings) to restaurants
3) a list of restaurant names (strings)
? 1
-- OK! --

---------------------------------------------------------------------
Problem 10 > Suite 2 > Case 1
(cases remaining: 2)

-- Already unlocked --

---------------------------------------------------------------------
Problem 10 > Suite 3 > Case 1
(cases remaining: 1)

-- Already unlocked --

---------------------------------------------------------------------
OK! All cases for Problem 10 unlocked.
