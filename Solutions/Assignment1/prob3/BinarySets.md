```java
import java.text.ParseException;
import java.util.ArrayList;
import java.util.List;

public class BinarySets {

	public static void main(String[] args) throws ParseException {

		if (args.length == 0)			 // when arguments aren't given
		{
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}

		if (args.length > 1) 			//when too many arguments are given	
		{
			System.out.println("Too many arguments.\nTry again.");
			System.exit(0);
		}

		int N = Integer.parseInt(args[0]);		//throws ParseException if given argument is invalid
		if (N <= 0)				//N should be a positive integer
		{
			System.out.println("N should be a postive integer.");
			System.exit(0);
		}

		int[] bits = { 0, 1 };			
		List<String> temp = new ArrayList<>();
		
		List<String> binaryNums = generateBits(bits, N, N, temp, "");			//generate binary numbers
		generateSets(binaryNums, N);					//generate the required sets
	}

	private static void generateSets(List<String> binaryNums, int n) {
		
		for (int i = 0; i < n; i++) 			//for loop for n sets
		{
			//print set numbers, parentheses and considered position of lower significant bit
			System.out.print("Set " + (i + 1) + ": (");  
			for (int j = 1; j <= n; j++) {
				if (j == (i + 1))
					System.out.print("0");
				else
					System.out.print("x");
			}
			System.out.print(") = ");
			
			//append all the numbers of the set
			String result = "";
			for (int j = 0; j < binaryNums.size(); j++) {
				if (binaryNums.get(j).charAt(i) == '0')
					result += Integer.toString(j + 1) + ", ";
			}
			result = result.substring(0, result.length() - 2);			//delete the last comma and whitespace
			System.out.print(result);
			System.out.println();
		}

	}

	private static List<String> generateBits(int[] bits, int n, int k, List<String> temp, String sequence) {

		if (k == 0)
		{
			if (sequence.length() == n) 
				temp.add(sequence);
			return temp;
		}

		for (int i = 0; i < bits.length; i++) {
			String out = sequence + Integer.toString(bits[i]);
			generateBits(bits, n, k - 1, temp, out);			//recursive call to generate binary numbers
		}
		return temp;
	}

}

```
