```java
package primeNumbers;

import java.util.*;


/*
 * Algorithm to find all the consecutive prime numbers in the given range:
 * 
 * algo primeNum{
 * 		//given a range n to m
 * 		//find all the prime numbers from 2 to n and put them in a list
 * 		for i = 2 to n
 * 			for j = 2 to n
 * 				if i!=j && i%j == 0
 * 					i is not a prime number
 * 				else
 * 					i is a prime number
 * 		//using the list, find prime numbers between n and m and print them if they are consecutive
 * 		for i = n+1 to m
 * 			for j = 0 to k= list size
 * 				if i%list(j)!=0
 * 					add the prime number to list
 * 		for i = k to list size
 * 			if list.get(i+1)-list.get(i)==2
 * 				print list.get(i) and list.get(i+1)
 * }
 */


public class primeNumbers {

	public static void main(String[] args) {
		
		//input
		int lowNum=0, highNum=0;
		int item1=0, item2=0;
		ArrayList<Integer> listOfPrimeNumbers = new ArrayList<Integer>();
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
		//adding the first two prime numbers to the list
		
		listOfPrimeNumbers.add(2);
		listOfPrimeNumbers.add(3);
		boolean isPrimeFlag = false;
		int z=0;
		//finding the prime numbers below lowNum and adding them to the list
		
		int k = listOfPrimeNumbers.size();
		z=k;
		int lowNum1=0;
		
		//If the range starts from 0 or 1 then the prime numbers are computed from 2
		if(lowNum==0||lowNum==1)
		{
			lowNum1=2;
			
		}
		
		
		else {
			lowNum1=lowNum;
			
			//Find all the prime numbers below the lowNum
			for(int i=5;i<lowNum1;i++)
			{
				for(int j=2;j<=Math.sqrt(i);j++)
				{
					if(i!=j&&i%j==0)
					{
						isPrimeFlag=false;
						break;
					}
					isPrimeFlag=true;
				}
				if(isPrimeFlag==true)
					listOfPrimeNumbers.add(i);
				isPrimeFlag=false;
			}
			z=listOfPrimeNumbers.size();
		}
		
		
		//adding the prime numbers in the given range using the prime numbers that has already been added to the list if lowNum != 0 or 1
		//if lowNum == 0 or 1 then start from 2
		for(int i=lowNum1;i<=highNum;i++)
		{
			k = listOfPrimeNumbers.size();
			for(int j=0;j<k&&listOfPrimeNumbers.get(j)<=Math.sqrt(i);j++)
			{	
				if(i%listOfPrimeNumbers.get(j)==0)
				{
					isPrimeFlag=false;
					break;
				}
				isPrimeFlag=true;
			}
			if(isPrimeFlag==true)
				listOfPrimeNumbers.add(i);
			isPrimeFlag=false;
		}
		
		
		
		//if no prime numbers are added then no prime numbers exist within the given range
		if(listOfPrimeNumbers.size()==z)
		{
			System.out.println("No Prime Numbers exist between "+lowNum+" and "+highNum);
			return;
		}
		
		//if prime numbers are added, check if there are any consecutive prime numbers
		if(lowNum==1||lowNum==0)
			z=0;
		for(int i=z;i<listOfPrimeNumbers.size()-1;i++)
		{
			if(listOfPrimeNumbers.get(i+1)-listOfPrimeNumbers.get(i)==2) {
				System.out.println(listOfPrimeNumbers.get(i)+","+listOfPrimeNumbers.get(i+1));
				isPrimeFlag=true;
			}
		}
		
		//if no consecutive prime numbers are found
		if(isPrimeFlag==false)
			System.out.println("There are no consecutive Prime Numbers between "+lowNum+" and "+highNum);

	}

}

```
