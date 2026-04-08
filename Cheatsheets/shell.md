
---

# 🐚 Shell Scripting Cheat Sheet (Bash)

---

## 🚀 1. Basic Script Structure

```bash
#!/bin/bash

# This is a comment
echo "Hello, World!"
```

* `#!/bin/bash` → Shebang (tells system to use Bash)
* Run script:

  ```bash
  chmod +x script.sh
  ./script.sh
  ```

---

## 📥 2. Variables

```bash
name="Talha"
echo $name
```

⚠️ No spaces around `=`

---

## 📌 3. User Input

```bash
echo "Enter your name:"
read name
echo "Hello $name"
```

---

## 🧮 4. Arithmetic Operations

```bash
a=10
b=5

sum=$((a + b))
echo $sum
```

---

## 🔀 5. Conditional Statements

### if

```bash
if [ $a -gt $b ]; then
    echo "A is greater"
fi
```

### if-else

```bash
if [ $a -eq $b ]; then
    echo "Equal"
else
    echo "Not equal"
fi
```

### if-elif-else

```bash
if [ $a -gt $b ]; then
    echo "A > B"
elif [ $a -lt $b ]; then
    echo "A < B"
else
    echo "Equal"
fi
```

---

## 🔁 6. Loops

### for loop

```bash
for i in 1 2 3 4 5
do
    echo $i
done
```

### while loop

```bash
i=1
while [ $i -le 5 ]
do
    echo $i
    ((i++))
done
```

### until loop

```bash
i=1
until [ $i -gt 5 ]
do
    echo $i
    ((i++))
done
```

---

## ⚙️ 7. Functions

```bash
function greet() {
    echo "Hello $1"
}

greet "Talha"
```

---

## 📦 8. Command Line Arguments

```bash
echo "Script name: $0"
echo "First arg: $1"
echo "Second arg: $2"
echo "Total args: $#"
```

Run:

```bash
./script.sh arg1 arg2
```

---

## 📂 9. File Handling

```bash
# Check file exists
if [ -f file.txt ]; then
    echo "File exists"
fi

# Check directory
if [ -d folder ]; then
    echo "Directory exists"
fi
```

---

## 🔐 10. File Permissions (in script)

```bash
chmod 755 file.sh
```

---

## 🔗 11. Links

```bash
ln file.txt hardlink.txt
ln -s file.txt symlink.txt
```

---

## 📊 12. Process Management

```bash
ps
top
kill 1234
```

---

## 🔄 13. Redirection & Pipes

```bash
ls > output.txt
cat file.txt | grep "hello"
```

---

## 🧪 14. Case Statement

```bash
read choice

case $choice in
    1) echo "One";;
    2) echo "Two";;
    *) echo "Invalid";;
esac
```

---

## 📏 15. String Operations

```bash
str="Hello"

echo ${#str}       # Length
echo ${str:0:2}    # Substring
```

---

## 🔍 16. Test Operators

### Numeric

| Operator | Meaning      |
| -------- | ------------ |
| `-eq`    | Equal        |
| `-ne`    | Not equal    |
| `-gt`    | Greater than |
| `-lt`    | Less than    |

### File

| Operator | Meaning          |
| -------- | ---------------- |
| `-f`     | File exists      |
| `-d`     | Directory exists |
| `-r`     | Readable         |
| `-w`     | Writable         |

---

## ⚡ 17. Exit Status

```bash
echo $?
```

* `0` → success
* Non-zero → error

---

## 🧠 18. Important Built-ins

| Command | Purpose      |
| ------- | ------------ |
| `echo`  | Print output |
| `read`  | Input        |
| `exit`  | Exit script  |
| `clear` | Clear screen |

---

## ⚠️ Common Mistakes

❌ Wrong:

```bash
a = 10
```

✅ Correct:

```bash
a=10
```

❌ Missing spaces:

```bash
if [$a -gt $b]
```

✅ Correct:

```bash
if [ $a -gt $b ]
```

---

## 🎯 Exam Tips

* Always start with `#!/bin/bash`
* Use `chmod +x` before running
* Remember spacing in `if [ ]`
* `read` for input, `echo` for output
* `case` is cleaner than multiple `if-else`
* `$1`, `$2` → arguments

---

## 🧩 Mini Example Script

```bash
#!/bin/bash

echo "Enter a number:"
read num

if [ $num -gt 0 ]; then
    echo "Positive"
else
    echo "Negative or Zero"
fi
```

---
