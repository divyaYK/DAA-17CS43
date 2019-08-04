```java
package nSquare;

import java.util.*;

/*
 * Algorithm for computing n^2 using addition and subtraction of time complexity O(logN):
 * 
 * Algo squareOfN(int n)
 * {
 * 		if n==0 return 0
 * 		int k = squareOfN(divideBy2(n))
 * 		if n is odd
 * 			return n+k+k
 * 		return k+k 			
 * }
 * 
 * Algo divideBy2(int n)
 * {
 * 		int quotient =0
 * 		while(n>=2)
 * 		{
 * 			n=n-2
 * 			quotient++
 * 		}
 * }
 */
public class nSquare {
	
	public static void main(String[] args) {
		
		//input
		int n=0, result=0;
		if(args.length==0)
		{
			System.out.println("No arguments given.\nTry again.");
			System.exit(0);
		}
		
		try {
			n = Integer.parseInt(args[0]);
		}
		catch(NumberFormatException e)
		{
			System.out.println("Given argument is not a number.\nTry again.");
			System.exit(0);
		}
		
		//compute
		if(n==0)
			result=0;
		else if(n==1)
			result=1;
		else if(n<0)
			result = squareOfN(-n,-n);
		else
			result = squareOfN(n,n);
		
		//output
		System.out.println("Square of "+n+": "+result);
		

	}

	public static int squareOfN(int n, int temp) {
		if(n==0) return 0;
		int k=0;
		if(temp == 2)
			return n+n;
		if(temp==1)
			return n;
		k = squareOfN(n,divideBy2(temp));
		int remainder = remainderDivBy2(temp);
		if(remainder==1)
			return n+k+k;
		
		return k+k;
	}

	private static int remainderDivBy2(int n) {
		
		while(n>=2)
			n=n-2;
		return n;
	}

	public static int divideBy2(int n) {
		int quotient = 0;
		while(n>=2)
		{
			n=n-2;
			quotient++;
		}
		return quotient;
	}

}
```
