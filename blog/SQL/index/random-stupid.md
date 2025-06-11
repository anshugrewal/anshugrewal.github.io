1. What is the default value of NVARCHAR?
Ans: It's 1.
Yes, just 1.

So please, for the love of clean databases, don’t forget to mention the size.

Because size isn’t just a number — it’s the difference between a working app and a mysterious String or binary data would be truncated error.

2. CPU time and Elapsed time
Ans:

CPU time
This is the total time the SQL Server's CPU spent actively processing your query.
It only measures computation time by the processor.

Elapsed time
This is the total wall-clock time from the moment SQL Server started to when it finished executing your query.
It includes:
Waiting on I/O (e.g. reading from disk or memory)
Any blocking/delays
Network transfer (very small in local testing)

SET STATISTICS TIME ON;
SELECT TOP 1000 * FROM FGPartMasterSheet$
ORDER BY NEWID();
(SQL Server Execution Times:
   CPU time = 0 ms,  elapsed time = 18 ms.)

SET STATISTICS TIME OFF;

SET STATISTICS TIME ON;
SELECT TOP 1000 * FROM FGPartMasterSheet$
ORDER BY SAPPartNumber;
(SQL Server Execution Times:
   CPU time = 0 ms,  elapsed time = 17 ms.)

SET STATISTICS TIME OFF;

SET STATISTICS TIME ON;
SELECT TOP 1000 * FROM FGPartMasterSheet$
ORDER BY SAPPartNumber;
SET STATISTICS TIME OFF;

(SQL Server Execution Times:
   CPU time = 0 ms,  elapsed time = 22 ms.)
