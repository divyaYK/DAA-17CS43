```java
package groceryDiscountAgain;

import java.io.File;
import java.io.FileNotFoundException;
import java.text.ParseException;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

public class groceryDiscountAgain {

	public static void main(String[] args) throws ParseException {
		
		//input
		
		//if no arguments are given
		if(args.length==0)
		{
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}
		
		//if too many arguments are given
		if(args.length>2)
		{
			System.out.println("Too many Arguments.\nTry again.");
			System.exit(0);
		}

		//checking if the text file exists and if it is a file at all
		File file = new File(args[0]);
		
		if(!file.exists()) {
			System.out.println("File does not exist.\nTry again.");
			System.exit(0);
		}

		if(!file.isFile()) {
			System.out.println("Given file is not a Regular file.\nTry again.");
			System.exit(0);
		}
		
		
		List<String> itemName = new ArrayList<String>();
		List<Integer> itemPrice = new ArrayList<Integer>(); 
		
		try
		{
			Scanner scan = new Scanner(file);
			
			while(scan.hasNextLine())
			{
				//reading Names and Prices of Items from PriceList
				String[] arItems = scan.nextLine().split("[ ]+");
				itemName.add(arItems[0]);
				itemPrice.add(Integer.parseInt(arItems[1]));
			}
		}
		catch(FileNotFoundException e)
		{
			//if file is not  readable
			System.out.println("Could not read given file.\nTry again.");
			System.exit(0);
		}
		
		
		int N = Integer.parseInt(args[1]); //special Offer Price N
		List<List<Integer>> combinations = new ArrayList<List<Integer>>(); //2D arraylist to store different combinations
		List<Integer> temp = new ArrayList<Integer>(); //temporary arraylist 
		//indices of ItemName list correspond to ItemPrice indices which is why sorting to making any changes to ItemPrice list is not possible
		List<Integer> sortedItemPrice = new ArrayList<Integer>(itemPrice); //therefore ItemPrice list has been cloned
		Collections.sort(sortedItemPrice); //sorting the cloned list
		
		//compute
		getCombinations(sortedItemPrice,0, N, 0, temp, combinations);
		printCombinations(combinations,itemPrice,itemName);
		

	}

	public static void printCombinations(List<List<Integer>> combinations, List<Integer> itemPrice,
			List<String> itemName) {
		
		int index;
		int noOfItems=1;
		int k= 1; //for printing combination serial number 
		for(int i=0;i<combinations.size();i++)
		{
			
			System.out.print("Combination "+k+": ");
			k++;
			for(int j=0;j<combinations.get(i).size();j++)
			{
				index = itemPrice.indexOf(combinations.get(i).get(j)); //to find the index of the prices in the combinations list
				if(j!=combinations.get(i).size()-1&&combinations.get(i).get(j+1)==combinations.get(i).get(j)) //if price in the list is same as the next price in that list, 
					//then increment the quantity of the same item instead of printing the same item again
				{
					noOfItems++;
				}
				else
				{
					System.out.print(noOfItems+" "+itemName.get(index)+" "); //printing the item along with its quantity
					noOfItems=1;
				}
			}
			System.out.println();
		}
		
	}
	
	/*
	 * Main operation: Recursion + Backtracking
	 */
	public static void getCombinations(List<Integer> itemPrice, int start, int n, int sum, List<Integer> temp,
			List<List<Integer>> combinations) {
		
		if(sum>n)		//if sum>n, this list of combinations is rejected
			return;
		
		if(sum==n)		//if sum == n, this list of combinations is accepted and added to combinations list
		{
			combinations.add(new ArrayList<>(temp)); //temp list stores the list of combinations
			return;
		}
		
		for(int i = start;i<itemPrice.size();i++)		
		{
			temp.add(itemPrice.get(i));		//from start, add the next item to the temp list
			getCombinations(itemPrice,i,n,sum+itemPrice.get(i),temp,combinations); //recursively add items and keep checking the base conditions
			temp.remove(temp.size()-1);		//backtrack or remove the last item and continue 
		}
		
	}



}

```
