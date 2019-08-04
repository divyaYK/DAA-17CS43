```java
package factorDigits;

public class factorDigits {

	public static void main(String[] args) {

		// input
		int lowNum = 0, highNum = 0;
		int item1 = 0, item2 = 0;

		// if No input is given
		if (args.length == 0) {
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}

		// if 2 input parameters aren't passed

		if (args.length == 1) {
			System.out.println("One argument is missing.\nTry again.");
			System.exit(0);
		}

		// if too many input parameters are given
		if (args.length > 2) {
			System.out.println("Too many arguments.\nTry again.");
			System.exit(0);
		}

		// scanning the parameters
		try {
			item1 = Integer.parseInt(args[0]);
			item2 = Integer.parseInt(args[1]);
		}
		// if input parameters are invalid
		catch (NumberFormatException e) {
			System.out.println("Given Arguments are not Numbers.\nTry again.");
			System.exit(0);
		}

		// checking scanned parameters

		if (item1 < 0 || item2 < 0) {
			System.out.println("Non-Negative Integers are not allowed.\nTry again.");
			System.exit(0);
		}

		if (item1 < item2) {
			lowNum = item1;
			highNum = item2;
		} else if (item1 > item2) {
			lowNum = item2;
			highNum = item1;
		}

		else // if both parameters are equal then the range is invalid
		{
			System.out.println("Invalid Range.\nTry again.");
			System.exit(0);
		}
		
		printResult(lowNum,highNum);

	}

	public static void printResult(int lowNum, int highNum) {

		boolean isDivisible = false;
		boolean atLeastOnePrinted = false;
		for(int i=lowNum;i<=highNum;i++)
		{
			String Number = String.valueOf(i); //taking the number as a string
			char[] digits = Number.toCharArray(); //storing all the characters of the string
			
			for(int j=0;j<digits.length;j++)
			{
				int k = Character.getNumericValue(digits[j]); //converting every character to numerical value
				if(k!=0)
					if(i%k!=0)
					{
						isDivisible = false;
						break;
					}
				isDivisible = true;
			}
			
			if(isDivisible==true)
			{
				atLeastOnePrinted = true;
				System.out.println("Number "+i+" is divisible by all it's digits.");
			}
			isDivisible = false;
		}
		
		if(atLeastOnePrinted == false)
			System.out.println("No numbers are divisible by their digits within the given range.");
		
	}

}

```
