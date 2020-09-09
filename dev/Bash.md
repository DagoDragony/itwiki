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

if [[ $a == $b && $a == $c ]]; then
    echo "EQUILATERAL"
elif [[ $a == $b || $b == $c || $c == $a ]]; then
    echo "ISOSCELES"
else
    echo "SCALENE"
fi
```

