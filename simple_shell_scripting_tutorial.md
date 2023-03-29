# Shell Scripting Basics

Shell scripting is a way to automate tasks in Unix-like operating systems by writing scripts that contain a sequence of commands. The most common shell used for scripting is Bash (Bourne Again Shell).

## Shebang

The shebang specifies the interpreter to be used for the script. For Bash, the shebang line is:

```
#!/bin/bash
```

## Comments

Comments start with the '#' character and are not executed.

```
# This is a comment
```

## Variables

Variables store values for later use. Use the equal sign (=) without spaces to assign values, and the '$' character to access values.

```
name="John Doe"
echo "My name is $name"
```

## Command Substitution

Use the output of one command as an argument for another command by enclosing the command in $() or ``.

```
date_today=$(date)
echo "Today is $date_today"
```

## Conditional Statements

Use 'if', 'elif', and 'else' to execute different code blocks based on certain conditions.

```
if [ "$age" -gt 18 ]; then
  echo "You are an adult."
elif [ "$age" -eq 18 ]; then
  echo "You just turned 18."
else
  echo "You are not an adult."
fi
```

## Loops

Use 'for' or 'while' loops to execute a block of code multiple times.

# For loop
```
for i in {1..5}; do
  echo "Iteration $i"
done
```

# While loop
```
counter=1
while [ $counter -le 5 ]; do
  echo "Iteration $counter"
  counter=$((counter + 1))
done
```

## Functions

Functions are reusable pieces of code that can be called with arguments.

```
greet() {
  echo "Hello, $1!"
}

greet "John"
```

## Example Script

Here's a simple script that calculates the factorial of a given number:

```
#!/bin/bash

factorial() {
  if [ $1 -le 1 ]; then
    echo 1
  else
    previous_factorial=$(factorial $(( $1 - 1 )))
    echo $(( $1 * previous_factorial ))
  fi
}

echo "Enter a positive integer:"
read number

result=$(factorial $number)
echo "The factorial of $number is $result"
```

Save this script as "factorial.sh", make it executable using `chmod +x factorial.sh`, and run it with `./factorial.sh`.

---

# Windows Shell Scripting Basics

This tutorial covers scripting using batch files and PowerShell in the Windows operating system.

## Batch Scripting

Batch files (with a `.bat` or `.cmd` extension) contain a series of commands executed by the Windows command prompt (cmd.exe).

### Echo

Used to display text on the screen. By default, batch files display each command as it is executed. To disable this behavior, use `@echo off`.

```
@echo off
echo Hello, World!
```

### Variables

Variables store values for later use. Use the `set` command to assign a value to a variable, and `%variable%` to access the value.

```
set name=John Doe
echo My name is %name%
```

### Conditional statements

Use `if` to execute different code blocks based on certain conditions.

```
set age=20
if %age% GTR 18 (
  echo You are an adult.
) else (
  echo You are not an adult.
)
```

### Loops

Use `for` or `:label` with `goto` to create loops.

```
REM For loop
for /L %%i in (1,1,5) do (
  echo Iteration %%i
)

REM While loop
set counter=1
:loop
if %counter% LEQ 5 (
  echo Iteration %counter%
  set /A counter+=1
  goto loop
)
```

### Functions

Batch files don't have true functions like other scripting languages. However, you can use labels and `call` to mimic function behavior.

```
:Greet
echo Hello, %1!
goto :EOF

call :Greet John
```

## PowerShell Scripting

PowerShell scripts (with a `.ps1` extension) offer more advanced features and functionality compared to batch files.

### Output

Use `Write-Host` or `Write-Output` to display text on the screen.

```
Write-Host "Hello, World!"
```

### Variables

Variables store values for later use. Use the `$` character to declare and access variables.

```
$name = "John Doe"
Write-Host "My name is $name"
```

### Conditional statements

Use `if`, `elseif`, and `else` to execute different code blocks based on certain conditions.

```
$age = 20
if ($age -gt 18) {
  Write-Host "You are an adult."
} elseif ($age -eq 18) {
  Write-Host "You just turned 18."
} else {
  Write-Host "You are not an adult."
}
```

### Loops

Use `for`, `foreach`, or `while` to create loops.

```
# For loop
for ($i = 1; $i -le 5; $i++) {
  Write-Host "Iteration $i"
}

# While loop
$counter = 1
while ($counter -le 5) {
  Write-Host "Iteration $counter"
  $counter++
}
```

### Functions

Functions are reusable pieces of code that can be called with arguments.

```
function Greet($name) {
  Write-Host "Hello, $name!"
}

Greet "John"
```

Both batch and PowerShell scripts can be executed by double-clicking the script file or running the file from a command prompt or PowerShell window, respectively.

---

Tutorial written by ChatGPT, an AI language model developed by OpenAI.
