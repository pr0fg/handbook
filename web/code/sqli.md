# SQL Injection (SQLi)

SQL injection is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access. In many cases, an attacker can modify or delete this data, causing persistent changes to the application's content or behavior.

## Types of SQLi

|    SQL Injection Type        | Description                     
|----------------|-------------------------------|
|In-band SQLi (Classic SQLi)|In-band SQL Injection is the most common and easy-to-exploit of SQL Injection attacks. In-band SQL Injection occurs when an attacker is able to use the same communication channel to both launch the attack and gather results. The two most common types of in-band SQL Injection are Error-based SQLi and Union-based SQLi. |    
|Error-based SQLi          |Error-based SQLi is an in-band SQL Injection technique that relies on error messages thrown by the database server to obtain information about the structure of the database. In some cases, error-based SQL injection alone is enough for an attacker to enumerate an entire database.| 
|Union-based SQLi         |Union-based SQLi is an in-band SQL injection technique that leverages the UNION SQL operator to combine the results of two or more SELECT statements into a single result which is then returned as part of the HTTP response.|
|Inferential SQLi (Blind SQLi)|Inferential SQL Injection, unlike in-band SQLi, may take longer for an attacker to exploit, however, it is just as dangerous as any other form of SQL Injection. In an inferential SQLi attack, no data is actually transferred via the web application and the attacker would not be able to see the result of an attack in-band (which is why such attacks are commonly referred to as “blind SQL Injection attacks”). Instead, an attacker is able to reconstruct the database structure by sending payloads, observing the web application’s response and the resulting behavior of the database server. The two types of inferential SQL Injection are Blind-boolean-based SQLi and Blind-time-based SQLi.|
|Boolean-based (content-based) Blind SQLi |Boolean-based SQL Injection is an inferential SQL Injection technique that relies on sending an SQL query to the database which forces the application to return a different result depending on whether the query returns a TRUE or FALSE result. Depending on the result, the content within the HTTP response will change, or remain the same. This allows an attacker to infer if the payload used returned true or false, even though no data from the database is returned.|
|Time-based Blind SQLi |Time-based SQL Injection is an inferential SQL Injection technique that relies on sending an SQL query to the database which forces the database to wait for a specified amount of time (in seconds) before responding. The response time will indicate to the attacker whether the result of the query is TRUE or FALSE. epending on the result, an HTTP response will be returned with a delay, or returned immediately. This allows an attacker to infer if the payload used returned true or false, even though no data from the database is returned.|
|Out-of-band SQLi|Out-of-band SQL Injection is not very common, mostly because it depends on features being enabled on the database server being used by the web application. Out-of-band SQL Injection occurs when an attacker is unable to use the same channel to launch the attack and gather results. Out-of-band techniques, offer an attacker an alternative to inferential time-based techniques, especially if the server responses are not very stable (making an inferential time-based attack unreliable).|
| Voice Based Sql Injection | It is a sql injection attack method that can be applied in applications that provide access to databases with voice command. An attacker could pull information from the database by sending sql queries with sound. |


## SQL Comment Termination
- Hash comment: `#`
- C-style comment: `/*`
- SQL comment: `--`
- Backtick comment: \`
- Null byte: `;%00`


## Full List of SQLi Vectors
[Generic Injections Gist](https://gist.github.com/pr0fg/d6aa66f8a8c109875001f3d89ed0aef0)

[Error Based Injections Gist](https://gist.github.com/pr0fg/618c92cd3a5b27aceb9eb5ccf5add620)

[Time Based Injections Gist](https://gist.github.com/pr0fg/235339f9231f627f3d074f5b49d79b65)

[Union Select Injections Gist](https://gist.github.com/pr0fg/a0d44def0bfcf965a143311c48386687)

[Auth Bypass Gist](https://gist.github.com/pr0fg/3df347128adf45f6d0ca644d76152664)


## WAF Bypass
[Read more here.](https://owasp.org/www-community/attacks/SQL_Injection_Bypassing_WAF)