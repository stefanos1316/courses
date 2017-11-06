<img src="media/AUEB_logo.jpg" width="425" /> <img src="media/BA_Lab.png" width="425" />
# Προγραμματισμός ΙΙ
## Εξαιρέσεις και Ισχυρισμοί

* [Στέφανος Γεωργίου](https://www.balab.aueb.gr/stefanos-georgiou.html)
* [Θεόδωρος Στασινόπουλος](https://www.balab.aueb.gr/theodore-stassinopoulos.html)


## Τι έιναι εξαιρέσεις?

* Μία εξάιρεση είναι ένα γεγονός που παρακάμπτει την κανονική εκτέλεση ενός προγράμματος.


## Χηρισμός εξαιρέσεων 

* Μπορέι να γίνει χρησιμοποιώντας τον **try-catch** κατασκευαστή.

```java
try {
    some code here
} catch and finally blocks …
```


## throws

* Μπορούμε να ορίσουμε την πιθανότητα να προκήψη μία εξαίρεση στην υπογραφή μίας μεθόδου. 

```java
public void writeList() throws IOException, IndexOutOfBoundsException {...}
```


## throw new

* Μπορούμε να ορίσουμε την πιθανότητα δημιουργίας μίας εξαίρεσης  μέσο της **throw new** λέξης.
* Επίσης, θα πρέπει αν ορίσουμε στην υπογραφή της μεθόδου την λέξη **throws** με το όνομα της εξαίρεσης.

```java

public void checkAmout(int amount) throws NegativeAmoutException {
	if (ammount < 0) {
   		throw new NegativeAmmountException();
	}
}
```


## Τύποι εξαιρέσεων

![](media/exceptions.png)


## Παραδείγμα Checked Exception

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;

public  class testClass {

	public static void main(String args[])  {		
	      File file = new File("E://file.txt");
	      try {
			FileReader fr = new FileReader(file);
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} 
	   }
}
```


## Παράδειγμα Unchecked Exception

```java
	import java.io.*;
	
	public calss ExcepTest {
		public static void main(String[] args) {
			try {
				int a[] = new int[2];
				System.out.println("Access elements three:" + a[3]);
			} catch(ArrayIndexOutOfBoundsException e) {
				System.out.println("Exception thrown :" +e);
			}
			System.out.println("Out of the block");
		}
	}
```


## Χρήση της finally

```java
public class ExcepTest {

   public static void main(String args[]) {
      int a[] = new int[2];
      try {
         System.out.println("Access element three :" + a[3]);
      } catch(ArrayIndexOutOfBoundsException e) {
         System.out.println("Exception thrown  :" + e);
      } finally {
         a[0] = 6;
         System.out.println("First element value: " + a[0]);
         System.out.println("The finally statement is executed");
      }
   }
}
```


## Ίχνη Στοίβας

* Τα ίχνη στοίβας περιέχουν αποτελέσματα σφαλμάτων μίας εφαρμογής 
όπου προσφέρουν στοιχεία για τα αίτια του σφάλματος. 
* Η χρήση της μεθόδου **printStackTrace()** δίνει το δέντρο της 
στοίβας αν κάποια μέθοδος έχει αποτύχη.


## Παράδειγμα για Ίχνη Στοίβας

```java
HighLevelException: MidLevelException: LowLevelException
         at Junk.a(Junk.java:13)
         at Junk.main(Junk.java:4)
 Caused by: MidLevelException: LowLevelException
         at Junk.c(Junk.java:23)
         at Junk.b(Junk.java:17)
         at Junk.a(Junk.java:11)
         ... 1 more
 Caused by: LowLevelException
         at Junk.e(Junk.java:30)
         at Junk.d(Junk.java:27)
         at Junk.c(Junk.java:21)
         ... 3 more
```


## Δημιουργεία εξαιρέσεων

* Μπορούμε να δημιουργήσουμε τις δικές μας εξαιρέσεις επεκτείνοντας τις κλάσεις π.χ. **Exception**, **RuntimeException** 


## Ισχυρισμοί (1)

* Χρησιμοποιείτε για έβρεση λαθών μέσα στον κώδικα.
* Χρησιμοποιεί μια έκφραση boolean, αν αυτή επιστρέψει λάθος τότε προσδιορίζει την ένδειξη σφάλματος στο κώδικα 
με την εκτύπωση κάποιου μηνύματος.
* Για χρήση του assertion πρέπει να εκτελέσετε ώς έχει: java -ea|-enableassertion executable
* Επιτρέπει την τεκμηρίωση του κώδικα και τον τρόπο λειτουργίας του.


## Ισχυρισμοί (2)

* Επιτρέπει την κατανοώηση του προγράμματος μας για άλλα άτομα.
* Βοηθούν στην εύκολη αποσφαλμάτωση του κώδικα.
* Οι ισχυρισμοί δεν έιναι για τους χρήστες ενός προγράμματος αλλά για του μηχανικούς λογισμικού.
* Οταν εντοπιστεί σφάλμα ισχυρισμού συνήθως πρέπει να σταματά η λειτουργία ενός πρόγάμματος.


## Διαφορές Ισχυρισμών με Εξαιρέσεις

* Με τους ισχυρισμούς ελέγχουμε περιπτώσεις που δεν πρέπει ποτέ να συμβούν ενώ με τις εξαιρέσεις 
κάτι που μπορεί αν συμβεί.
* Ο ισχυρισμός σταματά την εκτέλεση του προγράμματος ενώ η εξαίρεση επιτρέπει την συνέχεια αν μπορεί 
να διορθωθεί το συγκεκριμένο σφάλμα.


## Παράδειγμα (1)

```java
BankAccount acct = null;

// ...
// Get a BankAccount object
// ...

// Check to ensure we have one
              assert acct != null : "Object Null";
``` 


## Παράδειγμα (2)

```java
import java.io.*;

public class AssertionTest3 {

   public static void main(String argv[]) throws IOException {
      System.out.print("Enter your marital status: ");
      int c = System.in.read();
      switch ((char) c) {
         case 's':
         case 'S': System.out.println("Single"); break;
         case 'm':
         case 'M': System.out.println("Married"); break;
         case 'd':
         case 'D': System.out.println("Divorced"); break;
         default: assert !true : "Invalid Option"; break;
      }

   }
}
```


## Παράδειγμα (3)

```bash
	[sgeorgiou@aiolos]$ java -ea AssertionTest3 
	Enter your marital status: n
	Exception in thread "main" java.lang.AssertionError: Invalid Option
		at AssertionTest3.main(AssertionTest3.java:15)

```
