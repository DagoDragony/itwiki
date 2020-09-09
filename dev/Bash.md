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

echo "(23*5)/5" | bc 
echo "scale = 4; 5+50*3/20 + (19*2)/7" | bc -l | xargs printf "%.3f\n"
```

