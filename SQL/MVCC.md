## What is [MVCC](https://www.youtube.com/watch?v=iM71d2krbS4)? (multiversion concurrency control)

Multiversion concurrency control (MVCC) is a database optimization technique. MVCC creates duplicate copies of records so that data can be safely read and updated at the same time.

With MVCC, database reads and writes don’t block each other, and that greatly enhances the user experience.

### What are the benefits of MVCC?

When implemented properly by a DBMS, multiversion concurrency control provides the following benefits:

- Improved read access performance;
- Diminished need for database locks;
- Fewer database access contention issues;
- Continued record isolation for write operations; and
- Reduced number of database deadlocks.
### How does an MVCC database work?

While DBMS vendors are free to implement MVCC in their own ways, multiversion concurrency control usually works like this:

1. Every database record has a version number.
2. Concurrent reads happen against the record with the highest version number.
3. Write operations operate on copy of the record, not the record itself.
4. Users continue to read the older version while the copy is updated.
5. After the write operation is successful, the version id is incremented.
6. Subsequent concurrent reads use the updated version.
7. When a new update occurs, a new version is again created, continuing the cycle.

## What is the difference between MVCC vs locking?

Unlike traditional a DMBS, multiversion concurrency control does not lock a record when a write operation is about to occur. Instead, a new version of the record, with an incremented version number, is created.

Users can continue to read the old version of the record while the new record is transitionally edited and updated. This eliminates the need for locks, as well as contention and deadlock issues.

When the new version of the record is committed to the database, all future read operations work on the updated version. New write operations again create a new version, and the cycle continues.

### What are the drawbacks to multiversion concurrency control (MVCC)?

While MVCC offers many benefits, there are two key drawbacks to multiversion concurrency control:

1. Concurrent update control methods are difficult to implement.
2. The database grows in size and becomes bloated by multiple versions of DBMS records.

For the user, or even the developer, the complexity involved to implement MVCC concurrency control methods is completely hidden, as the functionality is provided by the database vendor.

The developer can write SQL, and the end user can consume applications as they normally would. The fact that the DBMS uses multiversion concurrency control behind the scenes is completely transparent to them.

#### PostgreSQL MVCC multiversion concurrency control

Every vendor has its own strategy to minimize the main drawback of MVCC: the ever-expanding size of the database, given the potential number of record versions created.

To deal with version bloat, a PostgreSQL MVCC database uses a cleverly named process, VACCUM, to identify and delete duplicate and unneeded records created by the multiversion concurrency control process.

### Addressing the MVCC database space exceeded problem

The PostgreSQL MVCC VACCUM process solves the version bloat problem, but it can be resource-intensive when it runs and cause locks of its own as it inspects the state of each [record](https://www.theserverside.com/video/How-Java-17-records-work) in the database.

Despite the fact that it may consume extra resources, RDBMS admins should not turn PostgreSQL MVCC VACCUM process off. Otherwise, the system will eventually generate an MVCC database space exceeded error, and admins will need to take the database offline to resolve it.