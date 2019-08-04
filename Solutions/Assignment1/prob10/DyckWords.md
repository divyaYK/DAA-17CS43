```java
package dyckWords;

import java.text.ParseException;
import java.util.ArrayList;
import java.util.List;

public class dyckWords {

	public static void main(String[] args) throws ParseException {

		// input

		if (args.length == 0)// no arguments
		{
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}

		if (args.length > 1)// too many arguments
		{
			System.out.println("Too many arguments.\nTry again.");
			System.exit(0);
		}
		
		int K = Integer.parseInt(args[0]);
		char[] parentheses = {'(',')'}; 		//parentheses set
		K = K*2;				//parentheses are supposed to be printed in pairs
		
		printDyckWords(parentheses,"",K,K);		//method to print dyck words

	}

	public static void printDyckWords(char[] parentheses,String out, int k, int temp) {
		
		if(temp==0)		//base case
		{
			
			if(out==null)		
				System.out.println("No sequence is generated.");
			if(out.length()==k)		//if out String is of length k
			{
				boolean flag = false;
				int leftPrnthCount = 0;
				int rightPrnthCount = 0;
				
				if(out.charAt(0)!='('||out.charAt(k-1)!=')')		//if first character isn't '(' or last character isn't ')', out is not a dyck word
					return;
				
				
				List<Character> outChar = new ArrayList<>();		//Adding out string's characters to a list
				for(int i=0;i<k;i++)
				{
					outChar.add(out.charAt(i));
					if(out.charAt(i)=='(')
						leftPrnthCount++;
					else
						rightPrnthCount++;
				}
				if(leftPrnthCount!=rightPrnthCount)			//if left and right parentheses are not in pairs, out is not a dyck word
					return;
				
				int i=1;
				while(i<k)
				{
					if(outChar.get(0)==')')
					{
						flag = false;
						break;
					}
					if(outChar.get(0)=='('&&outChar.get(i)==')') 		//if a pair of left and right parentheses is found
					{
						outChar.remove(i);			// remove the pair and set the flag to be true
						outChar.remove(0);
						flag= true;
						k=k-2;			//k decreases after removing the pair
						i=1;			//search of right parentheses begins from index 1
					}
					else
					{
						flag = false;		//if pair is not found
						i++;				//keep searching by incrementing i until i is less than k
					}
					
					
				}
				
				if(flag==true)
					System.out.println(out);
			}
			return;
		}
		
		for(int i=0;i<parentheses.length;i++)
		{
			String sequence = out+parentheses[i];
			printDyckWords(parentheses, sequence, k, temp-1);
		}
		
	}

}

```
