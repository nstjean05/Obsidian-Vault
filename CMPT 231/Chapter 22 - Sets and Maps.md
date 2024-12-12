## What is a Set?
- A *set* is a collection of elements with no duplicates.
- These are often used to determine whether a particular element is a member.
- Other collections (such as lists) can also test for containment, but if containment is highly important, consider using a set.
## What is a Map?
- A map is a collection that establishes a relationship between keys and values.
- The goal is to have an efficient way of obtaining a value, given its key.
- Keys of a map must be unique, however multiple keys may map to the same object.
	- Ex.  An ID string may be used as a key to retrieve information about a member object.
## Set utilization.

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;
import java.util.TreeSet;
/**
* A URL domain blocker.
*/
public class DomainBlocker
{
	private TreeSet<String> blockedSet;
	/**
	* Sets up the domain blocker by reading in the blocked domain names from
	* a file and storing them in a TreeSet.
	* @throws FileNotFoundException
	*/
	public DomainBlocker() throws FileNotFoundException
		{
			blockedSet = new TreeSet<String>();
			File inputFile = new File("blockedDomains.txt");
			Scanner scan = new Scanner(inputFile);
			while (scan.hasNextLine())
				{
				blockedSet.add(scan.nextLine());
			}
		}

		/**
		* Checks to see if the specified domain has been blocked.
		*
		* @param domain the domain to be checked
		* @return true if the domain is blocked and false otherwise
		*/
		public boolean domainIsBlocked(String domain)
		{
		return blockedSet.contains(domain);
	}
}
```