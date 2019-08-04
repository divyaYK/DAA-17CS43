```java
import java.text.ParseException;

public class GenerateHAndT {

	public static void main(String[] args) throws ParseException{
		
		//No arguments case
		if(args.length==0)
		{
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}
		
		//Case of too many arguments
		if(args.length>1)
		{
			System.out.println("Too many arguments.\nTry again.");
			System.exit(0);
		}
		
		int N = Integer.parseInt(args[0]); //throws ParseException if not Parsable
		
		if(N<=0)		//if N is not positive
		{
			System.out.println("N should be a positive integer.\nTry again.");
			System.exit(0);
		}
		char[] hAndT = {'H','T'};		//H for heads and T for Tails
		
		headsAndTails(hAndT,"",N,N);		//generating sequence
	}

	static void headsAndTails(char[] hAndT, String out, int temp, int n) {
		
		if(temp==0)		//base case
		{
			if(out==null)
				System.out.println("No sequence generated.");
			if(out.length()==n)		//print the string iff it is of length n
				System.out.println(out);
			return;
		}
		
		for(int i=0;i<hAndT.length;i++)
		{
			int outSize = out.length();
			String sequence = out;
			if(outSize==0||!(out.charAt(outSize-1)=='T'&&hAndT[i]=='T')) //append the output string iff the preceding character and succeeding character are both not 'T' 
				sequence += hAndT[i];
			headsAndTails(hAndT,sequence,temp-1,n); //recursive call to append the string
		}
		
	}

}

```
