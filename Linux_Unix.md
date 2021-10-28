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