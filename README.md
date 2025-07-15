# INTEGRITY-FILE-CHECKER

*COMPANY*: CODETECH IT SOLUTIONS

*NAME*: ANISHA PRAVIN

*INTERN ID*: CITSOD165

*DOMAIN*: CYBERSECURITY 

*DURATION*: 4 WEEKS

*MENTOR*: NEELA SANTHOSH


#DESCRIPTION OF MY TASK 
Step 1: Library Imports
In below code, the required libraries are imported. The argparse library is used for parsing command-line arguments, hashlib for cryptographic hash functions, and sys for system-specific parameters and functions.

Python3
# Import the necessary libraries required.
import argparse
import hashlib
import sys
# Import the functions init and Fore from the colorama library.
from colorama import init, Fore

Step 2: Hash Calculation Function

Below, code defines a function calculate_hash that takes a file path as an argument and calculates the SHA-256 hash of the file using a hash object. It reads the file in 64KB chunks for efficiency and updates the hash object accordingly.

Python3
# Define a function to calculate the SHA-256 hash of a file.
def calculate_hash(file_path):
    # Create a SHA-256 hash object.
    sha256_hash = hashlib.sha256()
    # Open the file in binary mode for reading (rb).
    with open(file_path, "rb") as file:
        # Read the file in 64KB chunks to efficiently handle large files.
        while True:
data = file.read(65536)  # Read the file in 64KB chunks.
            if not data:
                break
            # Update the hash object with the data read from the file.
            sha256_hash.update(data)
    return sha256_hash.hexdigest()

    Step 3: Hash Verification Function
    
 A function verify_hash is defined, which takes a downloaded file path and an expected hash value as arguments. It calculates the hash of the downloaded file using the calculate_hash function and compares it with the expected hash value, returning a boolean result.

Python3
def verify_hash(downloaded_file, expected_hash):
    calculated_hash = calculate_hash(downloaded_file)
    return calculated_hash == expected_hash

    Step 4: Command-Line Argument
    
In this code, a command-line argument parser is created using argparse. Two arguments are defined: -f or --file for the downloaded file path and --hash for the expected hash value. Both are marked as required.

Python3
parser = argparse.ArgumentParser(
    description="Verify the hash of a file that is downloaded.")
parser.add_argument("-f", "--file", dest="downloaded_file",
                    required=True, help="path for the file downloaded")
parser.add_argument("--hash", dest="expected_hash",
                    required=True, help="Expected hash value is")
args = parser.parse_args()

Step 5: Argument Validation and Hash Verification

Finally, this subpart checks if the required command-line arguments are provided. If not, it prints an error message in red and exits. If the arguments are present, it proceeds to verify the hash using the verify_hash function. Depending on the result, it prints a success or failure message in green or red, respectively.

Python3
if not args.downloaded_file or not args.expected_hash:
    print(
        f"{Fore.RED}[-] Please Specify the file in order to validate and its Hash.")
    sys.exit()
if verify_hash(args.downloaded_file, args.expected_hash):
    print(
        f"{Fore.GREEN}[+] Hash verification occurred successfully. The software is original.")
else:
    print(
        f"{Fore.RED}[-] Hash verification has failed, which means the software may have been tampered or is not original.")
        
        Step 6: Run the Command in Terminal
        
After you have successfully written the code I have mentioned above, you can simply open the command prompt and go to the directory to where you have saved the python program and begin execution, for the execution you will need to run the following command:

python verify.py -f [file path here] [file name with extension] --hash [input your hash here.]


Conclusion
In conclusion, we learnt some concepts regarding the data integrity and how it can affect the data or file of any company or organization. we also learn about some of the drawbacks that we may have if we implement a system to deal and verify the data integrity, apart from all that we learnt the most important concept which was learning how we can verify the integrity of the files using digest or hash methods such as MD5, SHA-256 etc. along which example code to verify the integrity of a file.

OUTPUT

<img width="1070" height="266" alt="Image" src="https://github.com/user-attachments/assets/b8a6f382-f835-4614-9b48-9d14d2ff019a" />




    
