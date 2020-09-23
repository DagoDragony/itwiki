Bash

```
variable=value
arrayVar=(1 2 5 7 4)
arrayVar+=("someVal")
arrayVar+=(${anotherAray[@]})
echo ${someString:2:1} # from 3rd char get 1
echo $someString| cut -c3,4
echo $someString| cut -c1-7
IFS="" && echo $sentence | cut -f1-3

head -20 </dev/stdin

echo $variable
echo ${arrayVar[@]} # print all variable 
[[ ${myArray[*]} =~ $column ]] && printf "1" || printf "0" # check if array contains value

for server in "${servers[@]}"
do
	echo "$server"
done

for i in $(seq 1 $count)
do
    read number
    sum=$(( $sum+$number ))
done

(( $column % 50 == 0 )) && printf "one"

if [[ $a == $b && $a == $c ]]; then
    echo "EQUILATERAL"
elif [[ $a == $b || $b == $c || $c == $a ]]; then
    echo "ISOSCELES"
else
    echo "SCALENE"
fi

# expressions
echo "5+50*3/20 + (19*2)/7" | bc -l | xargs printf "%.3f\n"
```

