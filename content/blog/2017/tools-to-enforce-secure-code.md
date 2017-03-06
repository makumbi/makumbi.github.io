title=Tools for Enforcing Secure Code 
date=2017-02-19
type=post
tags=blog
status=published
~~~~~~

A simple Google search for an open source static code analysis tool displays a variety of tools for secure code analysis. Analyzing the various tools in the results menu, you quickly realize two things; one, that there are many open source code analysis tools, and two, the range at which code analysis tools differ from one another. Generally speaking, tools encountered during the survey some were multi-language (ex: VisualCodeGrepper, Zed Attack Proxy, PMD, and YASCA) others were language specific, for instance, only focusing on JAVA (ex: OWASP LAPSE+, FindBugs), PHP (ex: RIPS, and DevBug), or C++ (ex: Flawfinder, and CPPCheck). Another quick distinction between tools is the capabilities they had to conduct analysis. Analysis tools could either do both static and dynamic code analysis, others could only perform either static or dynamic code analysis. Furthermore, within language specific code analysis tools, tools differed further in the types of vulnerabilities they detected.

Recognizing the distinction and differences between open source secure code analysis tools is important and should not be overlook. A series of discussions among programmers and security team needs to take place in deciding a particular code analysis tool(s). Questions to be asked are; Does the tool support language(s) on the project? What type of vulnerability and code issues to they need to look for in code? What’s the rate of false positives associated with the tool(s)? among other targeted questions.

#### Selected open source tool

FindBugs code analysis tool will be used to demonstrate my understanding and purpose of open source code analysis tools. FindBugs is an open source code analyzer that focuses on detecting possible bugs in Java programs. Since the tool is written in Java, it is a stand-alone GUI application so it can be used on many platforms. Finally, FindBugs records potential errors in four ranks; scariest, scary, troubling and of concern (Markus, 2012).

#### Summary tool strengths and weaknesses

**Strengths**

Personally I prefer open source code analysis tools that focus only on a particular language because it allows the tool designer(s) to not only worry about detecting low hanging fruits, but get deeper into higher level coding vulnerabilities. Findbugs has a very low number of false positives. So the tool is generally reliable and finds valid bugs. The option of turning off scanning for certain types of bugs to be a useful feature which would increase the convenience of using FindBugs in different situations.

**Weakness**

FindBugs is not very customizable. For instance, Findbugs has its own defined coding style (naming conventions of methods etc.). There should be a way to customize the coding style so that it can analyze the code against a custom coding style specified by the user. It will not always be the case that the user will be coding in the style defined in FindBugs (Sandcastle, 2009).

### Source code for analysis

```
   private static void createConnection()
    {
        try
        {
            Class.forName("org.apache.derby.jdbc.ClientDriver").newInstance();
            //Get a connection
            conn = DriverManager.getConnection(dbURL); 
            
        }
        catch (ClassNotFoundException | InstantiationException | IllegalAccessException | SQLException except)
        {
            except.printStackTrace();
        }
        
    }
    
    private static void insertUserInfor(String userName, String userPass)
    {
        try
        {
            createConnection();
            stmt = conn.createStatement();
            stmt.execute("insert into " + tableName + " values ('" +
                    userName + "', '" + userPass + "')");
            
            stmt.close();
        }
        catch (SQLException sqlExcept)
        {
            sqlExcept.printStackTrace();
        }
    }
```

#### Results after applying FindBugs to the code

Netbeans makes it easy to apply Findbugs on Java code. The tool is deployed as follows; simply navigate to the navigation bar and click on sources, then click on inspect and select Findbugs. On the Java code that was inspected, Findbugs quickly detected troubling bugs within the code and displayed them on the results console. In random order, the tool grouped bugs in two categories; security and bad practice. On the left hand side of the results console, Netbeans has a feature that allows a user to rank bugs, so in my case, after clicking on the feature security category is placed at the top and bad practice category is placed below.

Under security category, Findbugs detected that the Java code is vulnerable to SQL injection. The tool was able to trace through the folder tree locating the precise method the vulnerability was occurring in the code. Findbugs gives a recommendation to mitigate the bug: “Consider using a prepared statement instead. It is more efficient and less vulnerable to SQL injection attacks”.

Under bad practice category, Findbugs detected one vulnerability at two locations in the code. The vulnerability detected was improper closing of a database resource. Findbugs’ recommendation to mitigate the bug: “Failure to close database resources on all paths out of a method may result in poor performance, and could cause the application to have problems communicating with the database”.

**Sources**

CyberSecology. “The OWASP Zed Attack Proxy (ZAP) Scanner” CyberSecology-Web Scanner Reviews. Retrieved from http://cybersecology.com/the-owasp-zed-attack-proxy-zap-scanner/ (On 17 February 2017).

InfoSec Institute. (2013). “Which Weapon Should I Choose for Web Penetration Testing? 3.0” Retrieved from http://resources.infosecinstitute.com/which-weapon-should-i-choose-for-web-penetration-testing-3-0/#gref (On 17 February 2017).

Markus, Sprunck. (2012)."Findbugs – Static Code Analysis of Java" Methods and Tools. Retrieved from http://www.methodsandtools.com/tools/findbugs.php (On 18 February 2017).

Sandcastle. (2009). “An Evaluation of FindBugs” Analysis of Software Artifacts. Retrieved from http://www.cs.cmu.edu/~aldrich/courses/654/tools/Sandcastle-FindBugs-2009.pdf (On 18 February 2017).

