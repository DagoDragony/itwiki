Bash

```
variable=value
arrayVar=(1 2 5 7 4)
arrayVar+=("someVal")
arrayVar+=(${anotherAray[@]})

echo $variable
echo ${arrayVar[@]} # print all variable 

for server in "${servers[@]}"
do
	echo "$server"
done
```

