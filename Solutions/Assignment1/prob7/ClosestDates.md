```java
package closestDates;

import java.io.File;
import java.io.FileNotFoundException;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
import java.util.Scanner;
import java.util.stream.Collectors;



public class closestDates {	
	
	static SimpleDateFormat formatDate = new SimpleDateFormat("yyyy-MM-dd");
	
	public static void main(String[] args) throws ParseException {
		
		if(args.length==0) 		//if no arguments are given
		{
			System.out.println("No arguments specified.\nTry again.");
			System.exit(0);
		}
		
		if(args.length>1)		//if too many arguments are given
		{
			System.out.println("Too many arguments.\nTry again.");
			System.exit(0);
		}
		
		List<Date> dateList = new ArrayList<>();
		
		try
		{
			File file = new File(args[0]);
			Scanner scan = new Scanner(file);
			if(!(file.exists())||!(file.isFile()))
			{
				System.out.println("Given file is invalid or does not exist.\nTry again.");
				System.exit(0);
			}
			while(scan.hasNextLine())
				dateList.add(formatDate.parse(scan.nextLine()));
			scan.close();
		}
		catch(FileNotFoundException e)
		{
			System.out.println("File not found.\nTry again.");
			System.exit(0);
		}
		
		dateList = dateList.stream().distinct().collect(Collectors.toList());			//delete the same/duplicate dates
		getDates(dateList);
		
	}

	private static void getDates(List<Date> dateList) {
		
		long minDiff = -1;
		Date date1 = null;
		Date date2 = null;
		for(int i=0;i<dateList.size();i++)
		{
			for(int j=0;j<dateList.size()&&j!=i;j++)
			{
				long diff = Math.abs(dateList.get(i).getTime()-dateList.get(j).getTime());
				if(minDiff==-1||diff<minDiff)
				{
					date1 = dateList.get(i);
					date2 = dateList.get(j);
					minDiff = diff;
				}
			}
		}
		System.out.print("Closest dates are: ");
		System.out.print(formatDate.format(date1)+" and "+formatDate.format(date2));
	}
```
