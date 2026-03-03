# Regular Expressions (Regex) in NLP

## 📌 Overview

Regular Expressions (Regex) are powerful text pattern-matching tools used to search, extract, clean, and manipulate text data.

In Natural Language Processing (NLP), Regex plays a critical role in text preprocessing and data cleaning.

---

## 🎯 Why Regex is Important in NLP?

Regex is commonly used for:

* Extracting emails
* Extracting phone numbers
* Removing punctuation
* Cleaning special characters
* Extracting hashtags or mentions
* Validating structured text patterns
* Token filtering

It is usually applied before tokenization or as part of the preprocessing pipeline.

---

## 🧠 Basic Regex Syntax

| Pattern | Meaning                           |    |
| ------- | --------------------------------- | -- |
| `.`     | Any character                     |    |
| `\d`    | Digit (0-9)                       |    |
| `\w`    | Word character (a-z, A-Z, 0-9, _) |    |
| `\s`    | Whitespace                        |    |
| `^`     | Start of string                   |    |
| `$`     | End of string                     |    |
| `*`     | 0 or more repetitions             |    |
| `+`     | 1 or more repetitions             |    |
| `?`     | Optional                          |    |
| `{n}`   | Exactly n times                   |    |
| `[]`    | Character set                     |    |
| `       | `                                 | OR |

---

## 🛠 Example in Python

```python
import re

text = "Contact me at example@gmail.com"

pattern = r"\w+@\w+\.\w+"
emails = re.findall(pattern, text)

print(emails)
```

### Output:

```
['example@gmail.com']
```

---

## 🧹 Cleaning Text Using Regex

### Remove Punctuation

```python
import re

text = "Hello!!! How are you??"
clean_text = re.sub(r"[^\w\s]", "", text)

print(clean_text)
```

### Output:

```
Hello How are you
```

---

## 📦 Common NLP Use Cases

### 1️⃣ Extract Numbers

```python
re.findall(r"\d+", text)
```

### 2️⃣ Extract Hashtags

```python
re.findall(r"#\w+", text)
```

### 3️⃣ Remove Extra Spaces

```python
re.sub(r"\s+", " ", text)
```

---

## 🔁 Regex in NLP Pipeline

Typical usage order:

1. Lowercasing
2. Regex cleaning
3. Tokenization
4. Stopword removal
5. Stemming / Lemmatization

---

## ⚠️ Limitations of Regex

* Not context-aware
* Not suitable for deep semantic understanding
* Can become complex and hard to maintain
* Not ideal for complex language structures

For advanced tasks, Machine Learning or Deep Learning models are preferred.

---

## 🚀 Conclusion

Regular Expressions are an essential foundational skill in NLP.
They provide efficient and fast pattern matching for structured text cleaning and extraction.

Before moving to Machine Learning or Transformers, mastering Regex is highly recommended.

---

**Author:** NLP-to-LLM Roadmap
**Level:** Beginner → Intermediate
**Category:** Text Preprocessing
