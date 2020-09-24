Bash

```
cat </dev/stdin
arr=($(cat))
variable=value
arrayVar=(1 2 5 7 4)
arrayVar+=("someVal")
arrayVar+=(${anotherAray[@]})
echo ${someString:2:1} # from 3rd char get 1
echo ${arr[*]:3:5}
echo ${arr[@]/*[aA]*/} # array substitution remove words with a|A
echo ${ary[@]/[A-Z]/.} # cap to "."
${#ArrayName[@]} # array length
${!ArrayName[@]} # array indexes
finalArr=(${arr[@]} ${arr[@]} ${arr[@]})
printf '%s\n' "${arr[@]}" | sort | uniq -u # print array into separate lines for other commands

echo $someString| cut -c3,4
echo $someString| cut -c1-7
IFS="" && echo $sentence | cut -f1-3

head -n20 </dev/stdin
tail -c20 </dev/stdin

tr "()" "[]"
tr "a-z" "A-Z"
tr -s " " # replace multiple aquirances with one

sort -r # reverse sort
sort -t$'\t' -k2 -rn # sort numeric reverse by field 2

uniq -u # only unique lines(if line has duplicate, it is skipped at all)

paste -s
paste - - - # join in groups of 3
paste -sd '\t\t\n' # as above
 

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

grep -iwE 'th(e|at|en|ose)'
sed -e 's/\<the\>/this/' # change word the to this
sed 's/\(thy\)/{\1}/gI' # case insensitive global thy wrap

awk '{ print $1,$2 }' test.txt
awk '/test/ { print $1 }' test.txt # return only lines containing test
awk '/^[a-z]/ { print } test.txt
awk '{ if($1 ~ /123/) print } test.txt
awk '{ if($1 ~ /[0-9]/) print } test.txt
awk '{ if($2 == "" || $3 == "" || $4 == "" ) print "Not all scores are available for "$1 }'
awk '{ if($2 < 50 || $3 < 50 || $4 < 50) print $1" : Fail"; else print $1" : Pass" }'
awk '{ if(NR%2 == 0) printf $0"\n" }'
```

