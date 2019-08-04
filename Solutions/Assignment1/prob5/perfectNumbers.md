```java
package perfectNumbers;

import java.util.*;



/* Algorithm for finding perfect numbers:
 * 
 * Algo perfectNumbers(int n, int m){
 * 		//range: m to n
 * 		for i = n to m
 * 			for j = 1 to i
 * 				if j divides i, add j to the list of factors
 * 			//sum= sum of all factors of i
 * 			if sum==i 
 * 				i is a perfect Number
 * }
 * 
 */



public class perfectNumbers {

	public static void main(String[] args) {
		
		//input
		int lowNum=0, highNum=0;
		int item1=0, item2=0;
		ArrayList<Integer> listOfFactors = new ArrayList<Integer>();
		//if No input is given
		if(args.length==0)
		{
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}
		
		//if 2 input parameters aren't passed
		if(args.length==1)
		{
			System.out.println("One argument is missing.\nTry again.");
			System.exit(0);
		}
		
		//if too many input parameters are given
		if(args.length>2)
		{
			System.out.println("Too many arguments.\nTry again.");
			System.exit(0);
		}
		
		//scanning the parameters
		try {
			item1 = Integer.parseInt(args[0]);
			item2 = Integer.parseInt(args[1]);			
		}
		//if input parameters are invalid
		catch(NumberFormatException e)
		{
			System.out.println("Given Arguments are not Numbers.\nTry again.");
			System.exit(0);
		}
		
		//checking scanned parameters
		
		if(item1<0||item2<0)
		{
			System.out.println("Non-Negative Integers are not allowed.\nTry again.");
			System.exit(0);
		}
		
		if(item1<item2)
		{
			lowNum=item1;
			highNum=item2;
		}
		else if(item1>item2)
		{
			lowNum=item2;
			highNum=item1;
		}
		
		else //if both parameters are equal then the range is invalid
		{
			System.out.println("Invalid Range.\nTry again.");
			System.exit(0);
		}
		
		//compute
		int sum=0;
		boolean perfectNumberExistsFlag=false;
		
		for(int i=lowNum;i<=highNum;i++)
		{
			//find all factors of i
			for(int j=1;j<i;j++)
			{
				if(j!=i&&i%j==0)
					listOfFactors.add(j);
			}
			
			//add all factors of i
			for(int k=0;k<listOfFactors.size();k++)
				sum+=listOfFactors.get(k);
			
			//if sum = i then i is a perfect number
			if(sum==i) {
				System.out.println(i+ " is a Perfect Number");
				perfectNumberExistsFlag = true;
			}
			
			//clear the required variables
			sum=0;
			listOfFactors.clear();
		}
		
		//if No perfect Numbers are found
		if(perfectNumberExistsFlag==false)
			System.out.println("No Perfect Numbers Exist within the given range.");

	}

}
```
