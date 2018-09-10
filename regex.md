# Regular Expressions

#### Wildcards
- Use '.' as wildcard for any character:
```python
regex = "b.t"
```

#### Beginnings and Endings of Strings
- Use '^a' to match strings that starts with 'a'.
- Use 'a$' to match strings that ends with 'a'.

#### Search Function
- re.search(pattern, string) returns a match object if pattern is found, None otherwise.
```python
import re
if re.search("needle", "haystack") is not None:
    print("Found!")
else:
    print("No match found!")
```

#### Matching Multiple Characters
- To match multiple characters, specify the characters between "[]":
```python
"[bcr]at"  # will match bat/cat/rat
"[0-9]"  # will match all numbers
"[a-zA-Z]"  # will match all alphabets
```

#### Escape Special Characters
- To escape a character with special meaning e.g. '[]', precede them with "\":
```python
for row in posts:
    if re.search("\[Serious\]", row[0]) is not None:
        # This will match "[Serious]", [] in this
        # case are no longer special characters
        serious_count += 1
```

#### Combine Regex Characters
- Check if code has either "[Serious]" or "[serious]":
```python
serious_count = 0
for row in posts:
    if re.search("\[[Ss]erious\]", row[0]) is not None:
        serious_count += 1
```

- Use "|" to match either one character or another
```python
if re.search("^[\[\(][Ss]erious[\]\)]", row[0]) is not None:
    serious_start_count += 1
if re.search("[\[\(][Ss]erious[\]\)]$", row[0]) is not None:
    serious_end_count += 1
# Combine both if statements using |
if re.search("^[\[\(][Ss]erious[\]\)]|[\[\(][Ss]erious[\]\)]$", row[0]) is not None:
    serious_count_final += 1  # [Serious], [serious], (Serious), (serious), [Serious) etc
```


#### Additional Regex
- Use "\*" to match 0 or more occurences
- Use "+" to match 1 or more occurences
- To match years, use:
```python
"[1-2][0-9][0-9][0-9]"
```
- Use "{n}" to repeat characters n times:
```python
"[0-9]{4}"  # repeat numbers 4 times
```
- Use "()" to create subgroups, omit characters:
```python
# log[0] is "[30/Jan/2010:00:03:18 +0200]"
re.search(r"(\[)(.*)(\])", log[0]).group(1)  # returns "["
re.search(r"(\[)(.*)(\])", log[0]).group(2)  # returns 30/Jan/2010:00:03:18 +0200
re.search(r"(\[)(.*)(\])", log[0]).group(3)  # returns "]"
```
- Use sub() to substitute strings:
```python
# sub(pattern, replacement, original_string)
re.sub("yo", "hello", "yo world")
```
- Use re.findall(pattern, string) will return all matches in a list:
```python
re.findall("[a-z]", "abc123")  # returns ["a", "b", "c"]
```
