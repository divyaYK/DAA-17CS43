```java
package box;

import java.text.ParseException;

public class box {

	public static void main(String[] args) throws ParseException {
		
		//input
		
		if(args.length==0)//no arguments
		{
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}
		
		if(args.length>1)//too many arguments
		{
			System.out.println("Too many arguments.\nTry again.");
			System.exit(0);
		}
		
		int N = Integer.parseInt(args[0]);
		int x=1,y=1;
		
		if(N%2==0)
		{
			x = N/2;
			y = x+1;
		}
		else
			x = N/2+1;
		
		for(int i=1;i<=N;i++)
		{
			for(int j=1;j<=N;j++)
			{
				
				if(i==1||i==N||j==1||j==N||i==j||j==(N-i+1)||i==x||j==x||i==y||j==y)
					System.out.print("*");
				else
					System.out.print(" ");
			}
			System.out.println();
		}

	}

}

```
