Cross-Platform RAM Dump Collection Tool
This tool facilitates the collection of RAM dumps on both Windows and Linux (ParrotOS, Kali). The collected RAM dump can be analyzed using tools like Volatility to extract process IDs and other forensic data.

Features
Windows Support: Simplified execution using Python.
Linux Support: Easily adaptable for ParrotOS and Kali Linux using the lime.ko module.
Output in .raw format for compatibility with forensic analysis tools.
Prerequisites
Common Requirements
Python 3.6 or later.
Necessary permissions:
Windows: Administrator privileges.
Linux: Root or sudo access.
Additional Requirements for Linux
lime.ko (Downloadable from the official Lime repository or through package managers).
Usage Instructions
For Windows
Navigate to the RAM Dumper folder in the tool's directory.
Open the terminal as Administrator in the same folder.
Execute the following command:
bash
Copy code
python ram_dump.py
A .raw file containing the RAM dump will be generated in the same folder.
For Linux
Before Running the Tool
Download the Lime kernel module (lime.ko):

Use the following command to clone the Lime repository:
bash
Copy code
sudo apt-get install -y linux-headers-$(uname -r) dkms git
git clone https://github.com/504ensicsLabs/LiME
cd LiME/src
make
The lime.ko file will be generated in the src directory.
Update the ram_dump.py file:

Replace the placeholder path in the following code:
python
Copy code
load_command = [
    "sudo",
    "insmod",
    "/lib/modules/6.10.11-amd64/updates/dkms/lime.ko",
    f"path={current_directory}/{MD5}/{MD5}.mem",
    "format=raw"
]
With the actual path to your downloaded lime.ko file. For example:
python
Copy code
"/path/to/your/lime.ko"
Running the Tool
Navigate to the tool's directory where ram_dump.py is located.
Open a terminal and execute the following command:
bash
Copy code
sudo python3 ram_dump.py
A .raw file containing the RAM dump will be created in the current directory.
Output Details
The tool generates a .raw file containing:

Complete RAM dump of the system.
Process IDs and other critical forensic information.
The .raw file can be analyzed using forensic tools like Volatility for further investigation.

Notes
Ensure the required permissions are granted before execution.
The tool is optimized for Windows and Linux (ParrotOS, Kali) but can be extended for other platforms with minor modifications.
For questions or issues, feel free to contact the project contributors.
Thank you for using the Cross-Platform RAM Dump Collection Tool!

Let me know if you need further refinements!
