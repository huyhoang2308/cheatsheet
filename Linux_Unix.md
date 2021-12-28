# Linux/Unix

## String and format

- Printing to terminal
```bash 
$ echo "Welcome to Bash"
Welcome to Bash

$ printf "Welcome to Bash"
Welcome to Bash
```

- Escape character prefixed
```bash
$ echo "Hello world \!" #Escape character \.
Hello world !
```

- Format
```bash
$ printf "%-5s %-10s %-4s\n" No Name Mark
$ printf "%-5s %-10s %-4.2f\n" 1 Sarath 80.3456
$ printf "%-5s %-10s %-4.2f\n" 2 James 90.9989
$ printf "%-5s %-10s %-4.2f\n" 3 Jeff 77.564v

No    Name       Mark
1     Sarath     80.35
2     James      91.00
3     Jeff       77.56
```

- Print file content
```bash
hello.txt
hello world!

$ cat hello.txt 
hello world! 
```

- Finding the length of a string
```bash
$ var=12345678901234567890$
$ echo ${#var}
20
```

## System
- datetime and format 
```bash
$ date
Sun Oct 31 20:47:17 +07 2021

$ date +"%m-%d-%y"
10-30-21

$ date +"%Y-%m-%d"
2021-12-28

# Get last day of preioius month 
$ date -d "$(date +%Y-%m-01) -1 day" +%d-%b-%Y
30-Nov-2021
```


- Checking for super user
```bash
If [ $UID -ne 0 ]; then
	echo Non root user. Please run as root.
else
	echo Root user
fi
```

- Write to file
```bash
$ echo 'hello' > hello.txt
$ cat hello.txt
hello

$ cat hello.txt | tee new_hello.txt
$ cat new_hello.txt
hello
```

- Searching content file
```bash
$ file1.txt
hello world! My name is Dale!

$ file2.txt
hello world! My name is Chip!

$ grep Dale file1.txt
My name is Dale!

$ grep Dale file2.txt

$ grep Chip file2.txt
My name is Chip!

$ grep Chip file2.txt
My name is Chip!
```
- Read from input
```bash
$ cat test.sh 

#!/bin/bash
# This script will test if you have given a leap year or not.

echo "Type the year that you want to check (4 digits), followed by [ENTER]:"

read year

if (( ("$year" % 400) == "0" )) || (( ("$year" % 4 == "0") && ("$year" % 100 !=
"0") )); then
  echo "$year is a leap year."
else
  echo "This is not a leap year."
fi

$ test.sh 
Type the year that you want to check (4 digits), followed by [ENTER]:
2000
2000 is a leap year.
```

- File description: List all files/folders in current directory	
```bash
$ pwd
/mnt/c/Users/user
$ ls -l
drwxrwxrwx 1 dale dale      512 Aug  9 07:57  OneDrive
```