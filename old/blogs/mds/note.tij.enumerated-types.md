## Enumerated Types ##

### Basic enum features ###
When you create an `enum`, an associated class is produced for you by the compiler. This class is automatically inherited from `java.lang.Enum`. The methods in the class is:

* **ordinal()** 	get the order of each `enum` instance, start from `0`.
* **equals()** and **hashCode()** return true or false
* **compareTo()** 	(Comparable)  return >0 =0 <0
* **name()** 		equal to **toString()**
* **valueOf()** 	get the valueOf `enum` instance by name.
* **getDeclaringClass()**

In declaration of `enum Shrubbery { GROUND, CRAWLING, HANGING }`, the Shrubbery is the new class inherited from `java.lang.Enum`.
Static import of `import static packageName.Shrubbery.*` ,you can use the static instance of `enum` GROUND .etc directly without Shurbbery.GROUND in other java source file.

### Adding methods to an enum ###
Except for the fact that you can't inherit from it, an **enum** can be treated much like a regular class. You can add methods to an **enum**, including `main()`.

	import static net.mindview.util.Print.*;
	public enum OzWitch {
		WEST(" the West"), 						//instance of the new Class OzWitch
		NORTH("the North"),
		EAST("the East"),
		SOUTH("missing");

		private String description;  			// new data member 

		private OzWitch(String description) {	// add methods: OzWitch, getDescription, main.
			this.description = description;
		}
		public String getDescription() { return description; }
		public static void main(String[] args) {
			for(OzWitch witch : OzWitch.values())
			print(witch + ": " + witch.getDescription());
		}
	}

### Overriding enum methods ###
You can overriding the `toString()` method. 

### `enum`s in *switch* statement ###

### The mystery of *values()* method ###
