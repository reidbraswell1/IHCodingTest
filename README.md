# IHCodingTest

## Problem 1
1) Write a function that take and integer and returns a boolean of false when the integer is a prime number and true if it is not.  A prime number is a number greater than 1 that has no positive divisors other than 1 and itself.

Example:\
isNotPrime(7) => false<br>
isNotPrime(12) => true<br>

\<insert code here>
  
```csharp
        static bool isPrime(int number)
        {

            if (number == 1) return false;
            if (number == 2) return true;

            for (int i = 2; i <= Math.Ceiling(Math.Sqrt(number)); ++i)
            {
                if (number % i == 0) return false;
            }

            return true;

        }
```
## Problem 2

2) Given a string, find the last unique (non-repeating) character in it and return it's index. If it doesn't exist, return -1. 
\
\
Example:
\
\
lastUnique(“timedtestsarestressful”) => 21<br>
lastUnique(“xabcabc”) => 0<br>
lastUnique(“omnomnom”) => -1<br>

\<insert code here>

```java
public static int getCharacter(String input){
       //remove all the spaces
       input = input.replaceAll(" ", "");
       Character nonRptChar = null;
       int indexNonRptChar = -1;
       //Will store each character and it's count
       HashMap<Character, Integer> map = new HashMap<>();
       for (int i = 0; i <input.length(); i++) {
           Character chr = input.charAt(i);
           if(map.containsKey(chr)){
               map.put(chr,map.get(chr)+1);
           }else{
               map.put(chr, 1);
           }
       }
       //Iterate the string from right to left and return the character for which the count is 1 in map
       for (int i = input.length()-1; i >=0; i--) {
           if(map.get(input.charAt(i))==1){
               nonRptChar = input.charAt(i);
               indexNonRptChar = i;
               break;
           }
       }
       return indexNonRptChar;
}

```

## Problem 3

3) Write a function that given a path, will read in a file and print the number of occurrences of all words in the file that start with a vowel (‘a’, ‘e’, ‘i’, ‘o’, ‘u’). 

Example:\
countVowelWords(“testfile.txt”) =>
\
\
30 a\
14 and\
17 in\
24 of\
5 end\
2 under\
\...<br>

\<insert code here>

``` csharp
        static void countVowelWords(string fileName)
        {
            string text = File.ReadAllText("/home/reid/repos/test/test.txt");

            var words = text.Split(' ');
            var queryResultsA =
                from n in words
                where n.StartsWith('a')
                orderby n ascending
                select n;

            var queryResultsE =
                from n in words
                where n.StartsWith('e')
                orderby n ascending
                select n;

            var queryResultsI =
                from n in words
                where n.StartsWith('i')
                orderby n ascending
                select n;

            var queryResultsO =
                from n in words
                where n.StartsWith('o')
                orderby n ascending
                select n;

            var queryResultsU =
                  from n in words
                  where n.StartsWith('u')
                  orderby n ascending
                  select n;

            var temp = "";
            var count = 0;

            if (queryResultsA.Count() > 0)
            {
                temp = queryResultsA.First();
                count = 0;
                foreach (var item in queryResultsA)
                {
                    if (item != temp)
                    {
                        Console.WriteLine($"{count} {temp}");
                        temp = item;
                        count = 0;
                    }
                    count++;
                }
                Console.WriteLine($"{count} {temp}");
            }

            if (queryResultsE.Count() > 0)
            {
                temp = queryResultsE.First();
                count = 0;
                foreach (var item in queryResultsE)
                {
                    if (item != temp)
                    {
                        Console.WriteLine($"{count} {temp}");
                        temp = item;
                        count = 0;
                    }
                    count++;
                }
                Console.WriteLine($"{count} {temp}");
            }

            if (queryResultsI.Count() > 0)
            {
                temp = queryResultsI.First();
                count = 0;
                foreach (var item in queryResultsI)
                {
                    if (item != temp)
                    {
                        Console.WriteLine($"{count} {temp}");
                        temp = item;
                        count = 0;
                    }
                    count++;
                }
                Console.WriteLine($"{count} {temp}");
            }

            if (queryResultsO.Count() > 0)
            {
                temp = queryResultsO.First();
                count = 0;
                foreach (var item in queryResultsO)
                {
                    if (item != temp)
                    {
                        Console.WriteLine($"{count} {temp}");
                        temp = item;
                        count = 0;
                    }
                    count++;
                }
                Console.WriteLine($"{count} {temp}");
            }

            if (queryResultsU.Count() > 0)
            {
                temp = queryResultsU.First();
                count = 0;
                foreach (var item in queryResultsU)
                {
                    if (item != temp)
                    {
                        Console.WriteLine($"{count} {temp}");
                        temp = item;
                        count = 0;
                    }
                    count++;
                }
                Console.WriteLine($"{count} {temp}");
            }
        
```

## Problem 5

Given three tables (Patients, Hospitals, and Visits), write a SQL query that returns the total number of patients over 65 who visited each hospital in 2017.

### Patients

| patient_id | name  | date_of_birth |
| ------------ | ------- | --------------- |
| 1            | Alice   | 1965-04-02      |
| 2            | Bob     | 1990-08-01      |
| 3            | Charlie | 1982-07-05      |

### Hospitals

| hospital_id | name    | city   |
| ------------- | --------- | -------- |
| 1             | Emory     | Decatur  |
| 2             | Grady     | Atlanta  |
| 3             | Northside | Dunwoody |

### Visits

| visit_id | patient_id | hospital_id | visit_date |
| ---------- | ------------ | ------------- | ------------ |
| 1          | 2            | 2             | 2016-05-30   |
| 2          | 1            | 3             | 2016-08-04   |
| 3          | 3            | 3             | 2016-11-22   |
| 4          | 2            | 1             | 2017-01-15   |
| 5          | 1            | 2             | 2017-04-01   |

The result would look something like:

### Results

| Hospital Name | Patients Over 65 |
| ------------- | ---------------- |
| Emory         | 125403           |
| Grady         | 84537            |
| Northside     | 163522           |


\<insert SQL here>

```sql
SELECT Hospitals.name AS 'Hospital Name',
       COUNT(Patients.patient_id) AS 'Patients Over 65'
FROM Patients
JOIN Visits ON Visits.patient_id = Patients.patient_id
JOIN Hospitals ON Hospitals.hospital_id = Visits.hospital_id
WHERE (YEAR(CURRENT_TIMESTAMP) - YEAR(Patients.date_of_birth)) > 65;

```

DUMP

```sql
-- MySQL dump 10.13  Distrib 5.7.22, for Linux (x86_64)
--
-- Host: localhost    Database: IHTest
-- ------------------------------------------------------
-- Server version	5.7.22-0ubuntu0.16.04.1

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Current Database: `IHTest`
--

CREATE DATABASE /*!32312 IF NOT EXISTS*/ `IHTest` /*!40100 DEFAULT CHARACTER SET big5 */;

USE `IHTest`;

--
-- Table structure for table `Hospitals`
--

DROP TABLE IF EXISTS `Hospitals`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `Hospitals` (
  `hospital_id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `city` varchar(255) NOT NULL,
  PRIMARY KEY (`hospital_id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=big5;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `Hospitals`
--

LOCK TABLES `Hospitals` WRITE;
/*!40000 ALTER TABLE `Hospitals` DISABLE KEYS */;
INSERT INTO `Hospitals` VALUES (1,'Emory','Decater'),(2,'Grady','Atlanta'),(3,'Northside','Dunwoody');
/*!40000 ALTER TABLE `Hospitals` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `Patients`
--

DROP TABLE IF EXISTS `Patients`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `Patients` (
  `patient_id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `date_of_birth` date NOT NULL,
  PRIMARY KEY (`patient_id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=big5;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `Patients`
--

LOCK TABLES `Patients` WRITE;
/*!40000 ALTER TABLE `Patients` DISABLE KEYS */;
INSERT INTO `Patients` VALUES (1,'Alice','1945-04-02'),(2,'Bob','1990-08-01'),(3,'Charlie','1982-07-05');
/*!40000 ALTER TABLE `Patients` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `Visits`
--

DROP TABLE IF EXISTS `Visits`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `Visits` (
  `visit_id` int(11) NOT NULL AUTO_INCREMENT,
  `patient_id` int(11) NOT NULL,
  `hospital_id` int(11) NOT NULL,
  `visit_date` date NOT NULL,
  PRIMARY KEY (`visit_id`)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=big5;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `Visits`
--

LOCK TABLES `Visits` WRITE;
/*!40000 ALTER TABLE `Visits` DISABLE KEYS */;
INSERT INTO `Visits` VALUES (1,2,2,'2016-05-30'),(2,1,3,'2016-08-04'),(3,3,3,'2016-11-22'),(4,2,1,'2017-01-15'),(5,1,2,'2017-04-01');
/*!40000 ALTER TABLE `Visits` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2018-05-10 18:47:48
```
