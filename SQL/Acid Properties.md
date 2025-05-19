When you’re building and maintaining an application, **the last thing you want to worry about is data integrity**; Charging a customer the wrong amount or losing their data can be catastrophic. Thankfully, the databases you’re using — like MySQL and Postgres — take special measures to make sure that doesn’t happen. But what’s going on behind the hood? Most modern SQL DBs use transactional standards like ACID to ensure data integrity and keep your users from seeing wrong or stale data, and this post explores how they work.

## [All the things that can go wrong with your transactions](https://retool.com/blog/whats-an-acid-compliant-database#all-the-things-that-can-go-wrong-with-your-transactions)

Data Scientists worry about long analytical queries and warehousing, but for developers, databases are all about transactions. A database transaction is a series of logically grouped database operations: insert a row here, update a record there, and more stuff like that. Your application code is constantly making transactions every time you sign up a new user or that user updates their account information.

The thing about transactions, though, is that they can go very wrong. Any number of things can happen when you’re trying to write to your database: you can lose connection to a remote instance, you can encounter value errors, or anything else under the sun. You’ve seen it, you’ve dealt with it, and it can mean disaster for your underlying data. Let’s take a look at a quick example that a company like Amazon might run into:

```plaintext
1- User updates order quantity and clicks “order now” →
2- Update order quantity in the pending orders table
3- Add row to orders table
4- Apply the purchase to user’s balance / charge credit card
5
```

Copy Code

If something goes wrong in the middle of this group of operations but the system continues executing them, the user will get charged the wrong amount. And if the charge doesn’t work, they’ll get their order for free. It turns out that [these kinds of data errors have names](https://vladmihalcea.com/a-beginners-guide-to-acid-and-database-transactions/?ref=retool-blog), and there are a bunch of them. A few examples:

## [Dirty Reads](https://retool.com/blog/whats-an-acid-compliant-database#dirty-reads)

If a transaction is in the middle of updating some data and hasn’t committed yet, and another transaction is allowed to read that uncommitted data, that’s dirty, and could lead to your app showing incorrect data that got rolled back.

An example of a dirty read could be a transaction that invalidates login tokens when a user changes their password. If as the first transaction loads the token, a second one reads that token before the first invalidates it, you’d have yourself a dirty read.

In terms of actual [SQL](https://retool.com/blog/what-is-sql-structured-query-language), here's what a dirty read might look like:

```sql
1### Transaction 1 ###
2
3SELECT user_login_token_id
4FROM tokens
5
6UPDATE tokens
7SET token_status = "INVALID"
8WHERE token_id = user_login_token_id
9
10### Transaction 2 ###
11
12SELECT user_login_token_id
13FROM tokens
14
```

Copy Code

SQL

## [Non-Repeatable Reads](https://retool.com/blog/whats-an-acid-compliant-database#non-repeatable-reads)

If you’ve got two consecutive reads in one transaction with a concurrent update in between, those reads are going to show different results even though they’re part of the same transaction.

An example might be two writers working on a blog. Our first user starts a transaction that reads a post’s title, writes to the post, and then reads that post’s title again. If a second user changes that post’s title in the middle of the first user’s transaction, the first user is going to see different values for the title across the two reads; or in other words, a non-repeatable read.

Here's what a non-repeatable read might look like in SQL:

```sql
1### Transaction 1 ###
2
3SELECT post_title
4FROM posts
5
6SELECT
7    post_title,
8    post_content
9FROM posts
10
11### Transaction 2 ###
12
13UPDATE posts
14SET post_title = "something_new"
15WHERE post_title = post_title
16
```

Copy Code

SQL

## [Phantom Reads](https://retool.com/blog/whats-an-acid-compliant-database#phantom-reads)

If a transaction reads data and then a concurrent transaction inserts data that would have been read in the original transaction, that’s a phantom read.

Let’s use the same example as a non-repeatable read: if our second user adds content in between our first user’s two reads, the first read will be missing data that appears in the second read (this is actually really similar to a non-repeatable read, which is why the same example works).

In SQL, a phantom read might look like this:

```sql
1### Transaction 1 ###
2
3SELECT post_title
4FROM posts
5
6SELECT
7    post_title,
8    post_content
9FROM posts
10
11### Transaction 2 ###
12
13INSERT INTO posts
14VALUES "something_new", ...
15
```

Copy Code

SQL

These are the 3 transactional errors [as defined by the SQL standard](https://en.wikipedia.org/wiki/Isolation_(database_systems)?ref=retool-blog#Read_phenomena) — the big three, you might say. A lot of these errors sound like one another and tend to overlap in practice, so don’t sweat the details. For more detailed information, check out [Vlad Mihalcea’s blog series on the topic](https://vladmihalcea.com/a-beginners-guide-to-acid-and-database-transactions/?ref=retool-blog).

Now, the important question: how do we avoid these?

## [ACID, but the good kind](https://retool.com/blog/whats-an-acid-compliant-database#acid-but-the-good-kind)

Popular relational databases like MySQL avoid these kinds of data integrity issues by following a few core principles that govern how transactions work. They conform to a transactional standard called ACID. ACID is an acronym for four different words, but it really breaks down into two core principles: completeness and concurrency. First, here’s what ACID stands for:

- **Atomicity**: the “all or nothing” rule — the transaction either happens completely or doesn’t happen at all
- **Consistency**: data is consistent before and after a transaction without any missing steps
- **Isolation**: multiple transactions can happen concurrently without reading the wrong data
- **Durability**: transactional success is robust to system failure

These overlap a lot, so just remember: the point of any ACID compliant DB is to make sure that

- Transactions can fail without hurting data integrity
- Multiple transactions can occur concurrently without reading and writing the wrong data

ACID is a set of properties, but it’s not a process: how do the SQL databases we use actually achieve ACID compliance? They use a system called locking to keep the database on hold while transactions happen. Locking works like you’d imagine it would: when a transaction begins, the database engine locks the data that it’s working with until the transaction is completed (and sometimes, beyond that). That way, concurrent transactions can’t work with the data that’s being changed by the first transaction.

Once a transaction begins and acquires a lock, it can either finish successfully and commit, or run into an error and abort. It’s sort of like writing in an Excel spreadsheet before saving your work — things are changed, but only softly, until you save them (commit) or revert them (abort). Back to our Amazon example: if our database runs into an error right after updating a user’s order quantity, the transaction will abort, and it’s as if that update never happened. And if the error happened during the update, the credit card will never get charged. Either everything happens or nothing happens, and that’s ACID.

The intricacies of commiting and locks are pretty hairy, but a good start is [Methods and Tools’ excellent paper](https://www.methodsandtools.com/archive/archive.php?id=83&ref=retool-blog) on the topic.

## [ACID concepts in NoSQL and distributed systems](https://retool.com/blog/whats-an-acid-compliant-database#acid-concepts-in-no-sql-and-distributed-systems)

ACID was a building block of the reliable relational DBs we’re familiar with today, but NoSQL has changed the game: many NoSQL DBs are built as distributed systems, and they can’t always ensure complete transactional consistency. There’s actually a theory that governs this — called [CAP theorem](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e?ref=retool-blog) — that in distributed systems, you can’t never have full consistency and full availability; you need to choose one. So what does ACID look like for something like MongoDB or Cassandra?

A new quasi-standard has emerged for NoSQL databases called BASE (a rare overlap between SQL and chemistry jokes), and it’s a weak or soft consistency model that [relaxes some of the assumptions of ACID](https://neo4j.com/blog/acid-vs-base-consistency-models-explained/?ref=retool-blog) in order to achieve scalability:

- **Basic Availability**: the database basically works most of the time, even though it’s not perfect
- **Soft-State**: nodes of the database aren’t necessarily consistent with each other all the time
- **Eventual Consistency**: data will be consistent across nodes eventually, like by read time

In a lot of ways, this is the exact opposite of ACID, and prioritizes availability over perfect consistency; but that’s kind of the point of NoSQL in the first place. As NoSQL becomes a more established part of app development ([more than 25% of developers](https://insights.stackoverflow.com/survey/2019?ref=retool-blog) are using MongoDB already), expect more advancements on this front.

Today, we’re dealing with more data than we ever have, and we’re building database systems that can scale and handle that load. ACID might not be the exact transactional standard for the future, but its building blocks will certainly make their way in there. And if you’re building with a database and want a quick and easy way to add functionality on top, check out Retool.