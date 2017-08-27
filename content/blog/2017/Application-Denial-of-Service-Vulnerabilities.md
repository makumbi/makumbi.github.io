title=Application Denial of Service Vulnerability
date=2017-08-26
type=post
tags=blog
status=published
~~~~~~

The Denial-of-Service (DoS) attack is deployed by adversaries to render network resources or computer systems unavailable for those who are authorized to have access by sending heavy amounts of unusual traffic. Analyzing the impact of DoS attacks through the three pillars of security which are confidentiality, integrity, and availability the DoS attack mainly focuses on impacting availability, however, the attack can also lead to leaking of sensitive information or resources triggering the impact of confidentiality.

Attacker(s) use many techniques, methods, and tools at their disposal to carry out DoS or DDoS attacks. Some of these methods are what we have come accustomed to reading on security blogs and news sites, encompassing bandwidth consumption that consume all available network bandwidth of the victim or crafted packets that take advantage of existing vulnerabilities such as MAC Flooding on a Switch device. 

What we do not often hear on the news are application DoS attacks. These attacks focus on exhausting resources by using disproportionately large consumption of data that overwhelms available memory, disk space, or processor time. Attacks can include inserting many keys with the same code into hash table, triggering worst-case performance or using excessive disc space.

#### FIO04-J. Release resources when they are no longer needed.

Below is an example from [Rules for Oracle Coding Standard]( https://www.securecoding.cert.org/confluence/display/java/FIO04-J.+Release+resources+when+they+are+no+longer+needed "Rules for Oracle Coding Standard") for Java on how exhausting resources vulnerability found in java code can be mitigated.

The Java garbage collector ensures that unreferenced but unreleased memory is cleared to create space for used references. However, Java garbage collector cannot free non-memory resources such as open files and database connections. As a result, failing to release such resources can lead to resource exhausting attacks because remnants of used resources to be left in memory. To mitigate java garbage collector resource exhausting vulnerability output streams should be closed promptly after use. 

#### Noncompliant Code Example (File Handler)

```java
public int processFile(String fileName)
                       throws IOException, FileNotFoundException {
  FileInputStream stream = new FileInputStream(fileName);
  BufferedReader bufRead =
      new BufferedReader(new InputStreamReader(stream));
  String line;
  while ((line = bufRead.readLine()) != null) {
    sendLine(line);
  }
  return 1;
}
```

#### Compliant Solution Example

```java
try {
  final FileInputStream stream = new FileInputStream(fileName);
  try {
    final BufferedReader bufRead =
        new BufferedReader(new InputStreamReader(stream));
 
    String line;
    while ((line = bufRead.readLine()) != null) {
      sendLine(line);
    }
  } finally {
    if (stream != null) {
      try {
        stream.close();
      } catch (IOException e) {
        // Forward to handler
      }
    }
  }
} catch (IOException e) {
  // Forward to handler
}
```

Compliant code releases all resources regardless of any exception that might occur. In the case of the code snippet the File Input Stream is closed. If and when an output stream is used after each write, take steps to ensure that the output is reset after each write. The reset clears the output stream of internal object cache migrating memory and resource leaks during serialization.


