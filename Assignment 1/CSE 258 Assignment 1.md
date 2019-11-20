## CSE 258 Assignment 1

######  A53280596 Yawen Zhao

#### Task 1

In this part, we are aiming at this target: given a pair of one user and one book, we can predict whether the user read this book. Here we use Logistic Regression to solve this problem. Detail will be discusses as below

##### 1.1 Feature design

Given the pair (user, book), here we design 6 features of it as following:

(1) Computer the maximum jaccard similarity, cosine similarity and pearson similarity of the book with all the books this user has read before. Denote them as $$bookJacSim,bookCosSim,bookPearSim$$.

(2) Computer the maximum jaccard similarity, cosine similarity and pearson similarity of the user with all the users who have read this book. Denote them as $$userJacSim,userCosSim,userPearSim$$.

Here we can computer the specific similarity of two users or to book as following:

$$Jaccard \ Similarity: $$

$$Jaccard \ Similarity: $$

$$Jaccard \ Similarity: $$

Then our feature to be train can be denote as:

​           $$x = [1, bookJacSim, userJacSim, bookCosSim, userCosSim, bookPearSim, userPearSim]$$

Here corresponding $$y$$ is just whether this user has read this book, 1 as read, 0 as not read.

##### 1.2 Data Seperation

Given 200000 (user, book)pairs concerning all the books all the users has res, we seperate the data as 2 parts:

(1) 190000 (user, pair, rating) used to generate the feature of each book and each user to computer their similarity.

(2) 20000 (user, pair) used to train the logistic regression classifier. 

Regarding the 20000 data used to train the logistic regression classifier, as we only have 10000 (user, book) pairs that indicate the user has read this book as possitive data, we need to generate 10000 (user, book) pairs that indicate the user has not read this book as negative data. Here we simply generate these 10000 pairs based on the 200000 pairs concerning about all the books each user has read. 