
# FOSS LAB EXAM

Three problems were asked to be solved 

  - Amicable Number
  - Remove blank lines from a given file
  - Online BMI calculator

# Amicable Numbers

  - a pair of numbers, each of which is the sum of the factors of the other.
  - eg 220 and 284
  
```sh
##CODE##
#!/bin/sh
i=1
var=0
while [ $i -le 10000 ]
do
        k=`expr $i - 1`
        sum=0
        for j in `seq 1 $k`
        do
                a=`expr $i % $j`
                if [ $a -eq 0 ]
                then
                        sum=`expr $sum + $j`
                fi
        done
        #echo $sum 
        sum1=0
        k=`expr $sum - 1`
        for j in `seq 1 $k`
        do
                a=`expr $sum % $j`
                if [ $a -eq 0 ]
                then
                        sum1=`expr $sum1 + $j`
                fi
        done
        #echo $sum1
        if [ $sum -ne $sum1 ]
        then
                if [ $i -eq $sum1 ]
                then 
                        echo "$i"
                        var=`expr $var + $i`
                fi
        fi
        i=`expr $i + 1`
done
echo "Sum=$var"






```
What the program does is that it inputs value from 1 - 10000 using a while loop and it checks if it is amicable that is sum of the factors of the other are equal if so it is outputed and sum is incremented with the amicable value and the finally the sum is outputed when the loop runs out.











### Blank Lines

```sh
##CODE##
#!/bin/sh
if [ $# -ne 2 ]
then
	echo "Invalid number of parameters"
	exit
fi
file=$1
if test -s "$file"
then
	echo file exist
else
	echo file doesnot exist
fi
grep -v -w  -i "" $1 > $2





```

What the above code does is that it inputs two files as parameters and checks for number of parameters if not true points out an error using grep we can check for the empty lines and using invert (-v) we can copy all the mismatches to a new file and that is the output we require.

# BMI CALCULATOR USING PHP

- BMI = WEIGHT/(HEIGHT*HEIGHT)
- Input fields weight and height in a html file
- Pass the  value to the php file using POST method
- DO the processing and display the output
