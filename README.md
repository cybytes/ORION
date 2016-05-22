# ORION
ORION is a database system with both advanced features and very fast performance. It is still in early stages, but included features and goals are:
- Open source
- Platform independent
- Storage independent
- Distributed:
  - Clustering
  - Full and partial synchronization
  - Segmented data at different locations
- Queries on older data versions
- SQL and No-SQL
- Document database support
- Relational database support
- Object(-tree) database support
- Automatic index management
- Full version compatibility (backwards and forwards)

[OPEN SOURCE]
The system will be fully open source, including commercial use. We do require a reference visible to users somewhere in your application that mention ORION, Cybytes and me (Niels Bos) for credits.

[PLATFORM INDEPENDENT]
The core is written in portable .NET code, which allows it to run under many operating systems, including mobile platforms.

[STORAGE INDEPENDENT]
Storage works through API based modules that allow developers to program any type of storage. Standard IO modules include file system and memory. Storage may vary now and in the future, particularly in Cloud environments. The IO-API ensures the database can adapt to any of these.

[DISTRIBUTED]
ORION is capable of running a single database on several locations. One form is the cluster where multiple servers are scalable with higher reliability. 
The system also supports synchronization, where databases at different locations still work whilst not in-sync. The added "partial sync" feature allows one location to contain a subset of the data. This may be set by table, column, row or even cell. This function is very helpful for mobile and client applications, where the client systems don't need all data. An example is a central database with records for different users and each user only syncs his/her own records. 
Finally, the database supports segmented data where each location stores its own data for fast access whilst still have access to data from other locations at slower speeds. This is done by linking databases and queries know which data to get from which server. Data can be cached locally with synchronization in the background for faster queries.

[QUERIES ON OLDER DATA VERSIONS]
Each change to the database increases the data version number. The system allows queries on the current or any older version number. We are investigating the option to make changes to propagate from these to the head version. This allows applications to work with a snapshot without risk of changes in subsequent queries.

[SQL and No-SQL]
The initial setup will be No-SQL but we will implement SQL queries in the future, as this is a technology that many programmers are familiar with. In the background, all queries are C# scripts that are compiled on-the-fly. This should make queries very fast and, if stored as procedures, functions and views, run as fast as ORION runs itself with only a single compilation required for all invokations.

[DOCUMENT DATABASE SUPPORT]
Like other document databases, the system supports JSON/BSON documents for storage. The problem with these databases is that the data is often relational but that is slower. This makes the design a trade off in many cases between duplicate data with higher speed or relational data at slower speeds but without the risks and waste of duplicate data. ORION solves this with direct data pointers to related records which is as fast as non-relational whilst still be relational. The output is like a document in JSON/BSON with child records nested (if desired) as deep in a tree as you desire.

[RELATIONAL DATABASE SUPPORT]
The entire database is relational but works with direct data pointers in the storage, making it very fast on low access-time media like SSD and memory. ORION is designed with these low-latency type media in mind as we think they are the future (e.g. 3D XPoint).

[OBJECT(-TREE) DATABASE SUPPORT]
.NET code will be available in the first version to allow direct migration from classes to the database and back, with many additional features to manage this interaction with minimal code. Since the base of the system is JSON/BSON, any programming language should be possible in the future, including Java, C++ and any other.

[AUTOMATIC INDEX MANAGEMENT]
We will include a system that automatically creates, changes and deletes indexes on data, based on query loads. This feature is helpful for rapid application development, or if a developer wants fast data access without the fuss of programming this. Of course it can be set manually as well or to a combination of both. In addition, the system can use this system to advise the developer which indexes it thinks may improve performance and which aren't used (often) to help with profiling.

[FULL VERSION COMPATIBILITY]
With distributed databases, it may be hard to keep them all at the same version or ORION. Mobile devices may not have updated yet for example. For this reason, ORION has a versioned communication that allows older clients to work with newer databases, even if changes are substantial. We are investigating the option to support newer version as well through an automatic download in your application through the ORION libraries to include support of newer version.
This also includes versioning of data files, so any older (or possibly newer) version of the data files can be used in a version of ORION.

NOTE! Not all these features have been (fully) researched, so things may change. Please stay tuned for updates. For questions, suggestions and ideas, please contact me at info@cybytes.com.

Happy coding!
Niels
