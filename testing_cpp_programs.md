
# Program Testing Script

This file contains instructions on how to efficiently test a C++ graph program using a bash script that automates the testing process.

## 1. Organize the Test Cases

Place your input test cases and expected output in separate files.

Example directory structure:
```
/project
  - Solution.cpp
  - input1.txt
  - output1.txt
  - input2.txt
  - output2.txt
  - test_script.sh
```

- Input files: `input1.txt`, `input2.txt`, ...
- Expected output files: `output1.txt`, `output2.txt`, ...

## 2. Compile the Program

First, compile your program. This can be done manually or inside the script:
```bash
g++ -o Solution Solution.cpp
```

## 3. Bash Script for Automated Testing

Create a script `test_script.sh` to automate testing. This script will:
- Run the program on each input file.
- Compare the generated output with the expected output.

### Example Bash Script
```bash
#!/bin/bash

# Array of input and expected output file names
inputs=("input1.txt" "input2.txt" "input3.txt")
outputs=("output1.txt" "output2.txt" "output3.txt")

# Compile the C++ program
g++ -o Solution Solution.cpp

# Run tests
for i in ${!inputs[@]}; do
    # Run the solution on the input file and store the output in temp_output.txt
    ./Solution < ${inputs[$i]} > temp_output.txt

    # Compare the program's output with the expected output
    if diff -q temp_output.txt ${outputs[$i]} > /dev/null; then
        echo "Test Case $((i+1)): Passed"
    else
        echo "Test Case $((i+1)): Failed"
        echo "Expected:"
        cat ${outputs[$i]}
        echo "Got:"
        cat temp_output.txt
    fi
done

# Clean up temporary output file
rm temp_output.txt
```

## 4. Running the Script

To make the script executable, run:
```bash
chmod +x test_script.sh
```

Then execute the script:
```bash
./test_script.sh
```

## 5. Optional Enhancements

### Timeout Handling

To limit the execution time for each test case, use:
```bash
timeout 2s ./Solution < ${inputs[$i]} > temp_output.txt
```

### Memory Leak Detection

To detect memory issues, run the program through `valgrind`:
```bash
valgrind ./Solution < ${inputs[$i]} > temp_output.txt
```

## Conclusion

This method will help automate and verify multiple test cases for your C++ program efficiently.
