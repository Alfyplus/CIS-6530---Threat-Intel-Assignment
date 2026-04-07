The zip file in this repository contains the classification script used to train a CNN model on malicious opcodes. The model is an adaptation of the CNN described in the paper [Deep Android Malware Detection by McLaughlin et al.](https://dl.acm.org/doi/10.1145/3029806.3029823). The Raw Data folder contains the .opcode files submitted in Submission 3, which are needed to train the model.

##

### Setup

- **Python 3:** Python 3 must be installed on the system and accessible to the current user (Max version is 3.13 for TensorFlow)
- **Python Libraries:** The required python libraries must be installed either on the system or in the current virtual environment. They can be installed with pip using the command: pip install -r requirements.txt 
- **Opcode files:** The .opcode files output by the script submitted in Submission 3 are required for the machine learning preprocessing. They are included in the zip in the "Raw Data" directory.

##

### Usage

#### Model Training and Validation

python3 cnn.py \[Optional Arguments\]

|ARGUMENT|DESCRIPTION|
|---|---|
|--help, -h			    |Prints this help information|
|--input, -i \<dir_path\>	    |Sets the directory that the opcode files are in (Default "Raw Data")|
|--class, -c \<class\>		    |Sets the class to train the model on. Either (t)ype or (g)roup (Default type)|
|--seed, -s \<random_seed\>	    |Sets the random seed integer used throughout the script, used for reproducibility (Default random)|
|--output, -o \<output_string\>	    |Enables different outputs. The string can contain the following characters: p for accuracy, recall, precision, and f1 score printouts, l for a full list of class predictions, m for confusion matrix plot, n for no output (Default pm)|
|--type, -t \<types_path\>	    |Sets the path to the malware types input file (Default "Malware Types.txt")|

Example commands for ML training are:

python cnn.py -i "Raw Data" -t "Malware Types.txt" -s 42 -o pm -c type

python cnn.py -i "Raw Data" -t "Malware Types.txt" -s 42 -o pm -c group

####Note: This script takes a long time to run (multiple hours) due to the use of Leave-One-Out Cross-Validation