The zip file in this repository contains the opcodes extracted from the malware samples collected in Submission 2. Each file has the extension .opcode and is named after the malware sample it was extracted from. Within the Script folder inside the zip file are the Python scripts used to generate the opcode files.

##

### Setup

- **Operating System:** The scripts were designed to be used in a 64-bit Linux environment
- **Python 3:** Python 3 must be installed on the system and accessible to the current user
- **PyGhidra:** The PyGhidra python library must be installed either on the system or in the current virtual environment. It can be installed with pip using the command: pip install pyghidra 
- **Java Runtime:** An installation of the Java 21 runtime must be present on the system for Ghidra to work
- **Ghidra:** [Ghidra](https://github.com/NationalSecurityAgency/ghidra/releases) should be installed in an accessible directory on the machine. Once installed, Ghidra should be run once manually so that it can be pointed to the Java install directory

##

### Usage

python3 script.py \<GHIDRA_PATH\> \<EXECUTABLES_PATH\> \[Optional Arguments\]

|ARGUMENT|DESCRIPTION|
|---|---|
|GHIDRA_PATH			    |Required. Path to your Ghidra install directory|
|EXECUTABLES_PATH		    |Required. Path to the executables you wish to process.| Can be a file or directory
|--help, -h			    |Prints this help information|
|--verbose, -v			    |Enables verbose output|
|--recursive, -r		    |Will recursively search the directory at EXECUTABLES_PATH|
|--output_path, -o \<PATH\>	    |Sets the output path for the .opcode files (Default out/)|
|--output_type, -t \<TYPE\>	    |Sets the output type for the .opcode files. Either hex, hexaddr, or bin (Default hex)|
|--ignore, -i \<FILE1\[,FILE2\]\>   |A comma seperated list of file names to ignore in the executables directory (Only file names, not paths)|
|--project_name, -n \<NAME\>	    |Sets the Ghidra project name (Default tmpGhidraProject)|
|--project_path, -p \<PATH\>	    |Sets the Ghidra project path (Default is working directory)|
|--post_script, -s \<PATH\>	    |Sets the post script to use for analysis (Default ./post.py)|
|--log_path, -l \<PATH\>	    |Sets the path for the logfile directory (Default log/)|
|--no_out_recursive		    |Disables recursive directories on file output|
|--no_delete			    |Disables Ghidra project deletion at the end of the script|
