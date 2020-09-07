Java

"word".length()
"word".charAt()
java.util.Collections.sort(listOfCountryNames)

StringBuilder A=new StringBuilder("afsdfasd");
new StringBuilder("word").reverse().toString()
A.setCharAt(0, Character.toUpperCase(A.charAt(0)));

"someString.substring(0, 1).toUpperCase()
"someString".substring(1)

int[] arr = new int[23];
int[] arr = new int[]{ 1, 2, 3, 4 };

Character.toLowerCase('A')
Arrays.sort(new Char[]{ 'b', 'c', 'a' });

Stack<String> stack = new Stack<>();
stack.push("word");
while(!stack.isEmpty())
	stack.pop();

LinkedList<String> queue = new LinkedList<>();
queue.add("word");
while(!queue.isEmpty())
	queue.remove();


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

String[] arr = new String[] { "one", "two"};
for(String m: arr)
  System.out.println(m);

Map<String, Integer> words = new HashMap<>();
words.put("hello", 3);
words.computeIfPresent("hello", (k, v) -> v + 1);
competitorsHashMap.put(word, competitorsHashMap.get(word) + 1); // updates existing value too
System.out.println(words.get("hello"));

LinkedList<String> list = new LinkedList<>();
list.add("one");
list.get(i); // very ineffective

for (Map.Entry<String, String> entry : map.entrySet()) {
	System.out.println(entry.getKey() + " = " + entry.getValue());
}
