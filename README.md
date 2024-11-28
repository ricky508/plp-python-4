# plp-python-4

Here’s a Python program that addresses both the **File Read & Write Challenge** and **Error Handling Lab**. This program reads the content of a file, modifies the content (e.g., converting all text to uppercase), and writes the modified content to a new file. It also handles errors gracefully, such as when the file doesn't exist or can't be read.

### Full Code:

```python
def read_and_modify_file(input_filename, output_filename):
    try:
        # Open the input file in read mode
        with open(input_filename, 'r') as infile:
            content = infile.read()  # Read the content of the file

        # Modify the content (e.g., convert to uppercase)
        modified_content = content.upper()

        # Write the modified content to the output file
        with open(output_filename, 'w') as outfile:
            outfile.write(modified_content)

        print(f"Content has been successfully modified and saved to {output_filename}.")

    except FileNotFoundError:
        print(f"Error: The file {input_filename} does not exist.")
    except IOError:
        print(f"Error: There was an issue reading or writing the file.")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")


# Ask the user for the input and output filenames
input_filename = input("Enter the name of the file to read: ")
output_filename = input("Enter the name of the file to write the modified content to: ")

# Call the function to read and modify the file
read_and_modify_file(input_filename, output_filename)
```

### Explanation:
1. **read_and_modify_file function**:
   - It tries to open the specified file (`input_filename`) in read mode. If the file is not found, a `FileNotFoundError` will be raised.
   - It reads the content of the file and performs some modification (in this case, converting all text to uppercase).
   - The modified content is then written to a new file (`output_filename`).
   - If there’s an issue reading or writing the file, an `IOError` is caught.
   - Any other unexpected errors are caught by the general `Exception` block, and the error message is printed.

2. **Error Handling**:
   - **FileNotFoundError**: Raised if the specified input file doesn't exist.
   - **IOError**: Catches issues that may arise during file reading/writing (like permission issues).
   - **Generic Exception**: Catches any unexpected errors.

3. **User Input**:
   - The user is prompted to enter the names of the input and output files.

### Example Usage:
Assume you have a file named `sample.txt` with the following content:
```
Hello, world!
This is a file handling example.
```

If you run the program and enter:
```
Enter the name of the file to read: sample.txt
Enter the name of the file to write the modified content to: modified_sample.txt
```

The `modified_sample.txt` will contain:
```
HELLO, WORLD!
THIS IS A FILE HANDLING EXAMPLE.
```

### Error Handling Example:
If the user provides a non-existent file name (e.g., `nonexistent_file.txt`), the program will handle the error:
```
Enter the name of the file to read: nonexistent_file.txt
Enter the name of the file to write the modified content to: modified_sample.txt
Error: The file nonexistent_file.txt does not exist.
```
