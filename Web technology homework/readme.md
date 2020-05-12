## Unit 14 Homework: Web Development

#### HTTP Requests and Responses

Answer the following questions about the HTTP request and response process.

1. What type of architecture does the HTTP request and response process occur in?
##### Client Server architecture

2. What parts make up an `HTTP request`?
##### The request line, header and the body

3. What is the optional part of an HTTP request?
#####  The body is the optional part of HTTP request

4. What three parts make up an HTTP response?
##### The status line, header and Body

5. Which number class of status codes represent errors?
##### The status codes in the 400 series are the error codes
6. What are the two most common request methods that a security professional will come across?
##### The 2 most common request methods are GET method and POST method
##### GET method: It is used to request information from the source
##### POST method is used to update the information to the source
7. Which type of HTTP request method is used for sending data?
##### POST method is used for sending the data
8. Which part of an `HTTP request` contains the data being sent to the server?
##### The body part of the HTTP request  contains the data being sent to server
#####In the below example, Content length and home parameter contains the data and its length being transmitted to server:
```POST /path/script.cgi HTTP/1.0
From: frog@jmarshall.com
User-Agent: HTTPTool/1.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 32

home=Cosby&favorite+flavor=flies
```

9. In which part of an HTTP response would the browser receive the web code to generate and style a web page?
##### The body part of the HTTP request  contains the data being sent to server

#### Using cURL

Answer the following questions about `curl`:

10. What are the advantages of using curl over the browser?
##### Curl is a command line tool as compare to a GUI based web - --browser. It has the following advantages:
```-Test web server security configurations.
-Ensure web servers don't leak sensitive data through their HTTP responses.
-Verify that servers only respond to certain request types.
-Look for vulnerabilities on a web server.
```
11. Which curl option is used to change the request method?
##### we must use -X option to change the request method
12. Which curl option is used to set request headers?
##### we must use -H to set the request header
13. Which curl option is used to view the response header?
##### --head option
14. Which request method might an attacker use to scope out usable HTTP requests that an HTTP server will accept?
##### POST method

#### Sessions and Cookies

Recall that HTTP servers need ways to recognize clients from one another. These are implemented through sessions and cookies.

Answer the following questions about sessions and cookies.

15. Which response header sends a cookie to the client?

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```
##### Set-Cookie: cart=Bob will send a cookie to the client
16. Which request header sets a cookie in the client?

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```
##### Cookie: cart=Bob will set cookie in the client

#### Example HTTP Requests and Responses

Look through the following example HTTP request and response and answer the following questions.

#### HTTP Request Example

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What was the request method?
##### POST request method
18. Was the request encrypted or unencrypted?
##### unencrypted
19. Does the request have a user session associated to it?
##### no user session associated
20. What kind of data is being sent from this request body.
##### username & password is being sent.
#### HTTP Response Example

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```

21. What was the response status code?
##### 200 OK

22. Was the response encrypted or unencrypted?
##### encrypted
23. Does this response have a user session associated to it?
##### Yes `Set-Cookie: SessionID=5`
24. What kind of content is likely to be in the [page content] response body?
##### `Content-Type: text/html; charset=UTF-8`
25. If your class covered security headers, what security request headers have been included?
`Strict-Transport-Security: max-age=31536000; includeSubDomains`

#### Monoliths and Microservices

Answer the following questions about monoliths and microservices:

26. What are the individual components of microservices called?
##### A front end server, backend server and database
27. What is a service that writes to a database and communicates to other services?
##### API service writes to a database and communicates with other services
28. What type of underlying technology allows for `microservices` to become scalable and have redundancy?
##### container technology allows microservices to become scalable and have redundancy.

#### Container Vulnerability Filtering

Answer the following questions about vulnerability filtering `Trivy` scans with `jq`:

29. Do `microservices` share the same kind of vulnerabilities as regular operating systems?
##### A microservice shares similar kind of vulnerabilities as a regular OS. e.g Man in the middle attack, buffer overflow, Denial of service and Privilege escalation.

30. Would an organization be more concerned with `Low` severity vulnerabilities as much as `Critical`?
##### The organisation will not be concerned with Low as the damages will be limited.

31. Would the bash tool `jq` be useful in finding certain kinds of vulnerabilities within a vulnerability report?
##### yes jq can be used to find certain kind of vulnerabilities
`jq '.[0].Vulnerabilities | keys' results.json`

##### Deploying and Testing a Container Set

Answer the following questions about multi-container deployment:

32. What is a tool that can be used to deploy multiple containers at once?
##### docker-compose

33. What kind of file format was required for us to deploy a container set?
##### YAML file

##### Container Runtime Intrusion Detection Systems

34. What is a tool used to actively detects intrusion behavior within containers?
##### Container Intrusion Detection Systems (CIDS)

35. What high-value system file might an intruder view that would trigger a `sensitive file opening` alert?
`/etc/shadow`

36. What kind of intruder action might trigger an alert from a container IDS that says `shell configuration file has been modified`?
##### Unknown shell starting in the container
