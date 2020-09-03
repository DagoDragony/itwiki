Java

"word".length()
java.util.Collections.sort(listOfCountryNames)

System.out.println()
System.out.printf("%-15s%03d%n", "cpp", 10);

Scanner sc=new Scanner(System.in);
val scanner = if(args.length == 1){
val fileName = args(0)
	// println(s"Filename $fileName")
	new Scanner(new File(fileName))
}else
	new Scanner(System.in)
scanner.nextInt()

Math.pow(2, 3)

Calendar calendar = Calendar.getInstance();
calendar.set(2001, 12, 32);
calendar.get(Calendar.DAY_OF_WEEK);

NumberFormat usFormat = NumberFormat.getCurrencyInstance(Locale.US);
usFormat.format(2.129) // $2.13

NumberFormat usFormat = NumberFormat.getInstance(Locale.ENGLISH);
usFormat.setRoundingMode(RoundingMode.HALF_UP);
usFormat.setMaximumFractionDigits(2);
usFormat.setMinimumFractionDigits(2);
String us = "$" + usFormat.format(0.999);
