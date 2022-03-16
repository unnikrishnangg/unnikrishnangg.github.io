---
id: 70
title: 'Access denied when using GRANT ALL ON *.* in AWS RDS Mysql'
date: '2019-01-22T17:31:42+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=70'
permalink: /access-denied-when-using-grant-all-on-in-aws-rds-mysql/
description: "access denied when using GRANT *.* in AWS RDS mysql. This is useful to grant all privleges to an additional admin user."
categories:
    - AWS
    - RDS
redirect_from:
    - /tag/error-1045-28000-access-denied-for-user-admin-using-password-yes/
tags:
    - 'access denied for user admin rds'
    - 'Access denied when using GRANT ALL ON *.* in AWS RDS Mysql'
    - 'aws rds acces denied issue'
    - 'aws rds access denied'
    - 'cant grant all on *.* in rds'
    - 'ERROR 1045 (28000): Access denied for user ''admin''@''%'' (using password: YES)'
    - 'rds mysql grant all issue'
    - 'Using "GRANT ALL" With Amazon''s MySQL RDS'
    - AWS
    - RDS
---

I was totally unaware about the fact that even a master account doesn’t have all the privileges in an RDS database(MySQL) until I got stuck with this issue. Today, I was asked to create a secondary admin user in one of our production DB with all privileges. The MySQL DB instance was running in AWS RDS. I tried the following command

```
mysql> GRANT ALL ON *.* TO 'admin_sync'@'%';
ERROR 1045 (28000): Access denied for user 'admin'@'%' (using password: YES)
```

I got the above error while trying to grant all privileges. I was sure about the command because the same command was working fine for non-RDS mysql instances. Few minutes of googling has given me the fix.

```
 mysql> GRANT ALL ON `%`.* TO admin_sync@`%`;<p> Query OK, 0 rows affected (0.00 sec)
```


In order to protect the instance itself, RDS doesn’t allow even the master account to access to the mysql database. The mysql.\* tables are considered off-limits here since I don’t have access to the mysql.\* tables which are restricted by Amazon. I can’t grant permissions on \*.\* since that would match MySQL, and `%`.\* appears to not match those system tables.

So, the quick fix is to use `%`.\* instead of \*.\*.

The \_ and % wildcards are permitted when specifying DB names in GRANT statements that grant privileges at the global or database levels.

References

<https://dev.mysql.com/doc/refman/8.0/en/grant.html>

<http://www.fidian.com/problems-only-tyler-has/using-grant-all-with-amazons-mysql-rds>