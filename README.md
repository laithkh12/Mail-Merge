# ✉️ Automated Letter Generation

This project automates the generation of personalized letters based on a template. It reads a list of names from a file, replaces a placeholder in the letter template with each name, and saves each personalized letter as a separate document.

## 📋 Table of Contents
- [🎯 Objective](#-objective)
- [📂 Code Overview](#-code-overview)
  - [Process Outline](#process-outline)
- [⚙️ Requirements](#️-requirements)
- [▶️ How to Run](#️-how-to-run)
- [📄 License](#-license)

## 🎯 Objective
1. Read a list of names from `invited_names.txt`.
2. Use `starting_letter.txt` as a template for each personalized letter.
3. Replace the `[name]` placeholder with the actual name.
4. Save each letter in the "ReadyToSend" folder.

## 📂 Code Overview

### Process Outline

1. **Define the Placeholder**: 
   The placeholder `[name]` in the template will be replaced with each name in the list.

2. **Read the Names**:
   The program reads names from `invited_names.txt` in the `Input/Names` folder.

3. **Load the Template**:
   Read the content of `starting_letter.txt`, which contains the template letter with a `[name]` placeholder.

4. **Personalize and Save Each Letter**:
   - For each name, remove any leading or trailing whitespace using the `strip()` method. 
   - Replace the `[name]` placeholder in the template with the actual name.
   - Save the new letter as a `.docx` file in the `ReadyToSend` folder with the name format `letter_for_[name].docx`.

### Full Code Example

Copy and paste the following code into your Python file to run the program.

```python
PLACEHOLDER = "[name]"

with open("./Input/Names/invited_names.txt") as namesFile:
    names = namesFile.readlines( )

with open("./Input/Letters/starting_letter.txt") as letterFile:
    letterContent = letterFile.read()
    for name in names:
        strippedName = name.strip()
        newLetter = letterContent.replace(PLACEHOLDER, strippedName)
        with open(f"./Output/ReadyToSend/letter_for_{strippedName}.docx", mode="w") as completed_letters:
            completed_letters.write(newLetter)
```

- Hint 1: The readlines() method reads each line in the file as an item in a list. Learn more.
- Hint 2: replace() is used here to substitute [name] with the actual name. Learn more.
- Hint 3: strip() removes leading and trailing whitespace, which is helpful for cleaning up names.

## ⚙️ Requirements
- Python 3.x

## ▶️ How to Run
1. Ensure you have the following folder structure:
```bash
├── Input
│   ├── Names
│   │   └── invited_names.txt
│   └── Letters
│       └── starting_letter.txt
├── Output
│   └── ReadyToSend
```
2. Place your names in invited_names.txt (one name per line).
3. Create a letter template in starting_letter.txt with the placeholder [name].
4. Run the code:
```bash
python your_script_name.py
```
5. Find the personalized letters in the Output/ReadyToSend folder.

## 📄 License
This project is open-source and available under the MIT License.

Happy Letter Generating! 📬
