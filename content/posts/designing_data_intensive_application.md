---
title: "Designing data intensive applications (reading)"
date: 2020-10-26T18:01:10+02:00
draft: false
description: I've just finished a book about designing data intensive applications.
---

I've just finished a book about designing data intensive applications.

TLDR;
It's good to know the concepts behind the tools you use everyday. This is what this book is about regarding databases.
I must also confess that I was a bit disappointed because the focus is not about data science but more about dealing with large volumes of data in more common applications.
The book is very good in my opinion. I recommend it.


## Author
Martin Kleppmann is a senior lecturer at the University of Cambridge.
This is why you will find the point of view of a researcher through the book.

## Summary
This books is about problems and solution to achieve reliable, scalable and maintenable applications.

The book is wide. I would focus only on concurrency control, when two programs or more want to access the same piece of data. You can face different problems of race conditions. A race condition happens when several programs want to access a shared variable.
Write skew is an example of problem of race conditions. It happens when a user reads a piece of data, makes a decision according to this, and writes this decision. But meanwhile, the piece of data has been changed by the action of another user.

To prevent these kinds of problems, there are different solutions : from the weakest to the strongest.

- Snapshot isolation (repeatable reads)
This is the idea that each transaction reads from a consistent snapshot of the database.

- Serializability
This is the strongest isolation. It's not always efficient. The idea is to execute actions as if they have been executed one at a time. To achieve that there are different ways :
 1. Executing actions serially
 2. Two phase locking: lock reads and writes
 3. Serializable snapshot isolation
 
 The last one is an optimistic approach. It allows actions to proceed without blocking. But when there's the final commit, the program checks that everything is okay. If the execution is not serializable, the action is aborted.

## What I liked in this book?
- The point of view of a researcher
- Discovering concepts behind the tools I've used
- Concepts are well explained. Some are tricky, but there's a real effort to explain them well.
- 

## What I didn't like?
I was expected a book more about data in data science. Finally, the problem comes from me, not from the book.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
