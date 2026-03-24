The zip file in this repository contains the preprocessing and classification script used to train ML models on malicious opcodes. The Dataset folder contains the .csv files output by the preprocessing script when run on the .opcode files submitted in Submission 3.

##

### Setup

- **Python 3:** Python 3 must be installed on the system and accessible to the current user
- **Python Libraries:** The required python libraries must be installed either on the system or in the current virtual environment. They can be installed with pip using the command: pip install -r requirements.txt 
- **Opcode files:** The .opcode files output by the script submitted in Submission 3 are required for the machine learning preprocessing

##

### Usage

#### Preprocessing

python3 preprocess.py \[Optional Arguments\]

|ARGUMENT|DESCRIPTION|
|---|---|
|--help, -h			    |Prints this help information|
|--input, -i \<dir_path\>	    |Sets the directory that the opcode files are in (Default "Raw Data")|
|--type, -t \<types_path\>	    |Sets the path to the malware types input file (Default none)|
|--output, -o \<csv_path\>	    |Sets the path to the output csv file (Default "Processed Data.csv")|
|--ngram, -n \<ngram\>		    |Sets the ngram value used when vectorizing (Default 1)|

The commands used to create the included .csv files are as follows (where the "Raw Data" folder contains the .opcode files from Submission 3):

python preprocess.py -i "Raw Data" -t "Malware Types.txt" -n 1 -o "Processed Data 1-gram.csv"

python preprocess.py -i "Raw Data" -t "Malware Types.txt" -n 2 -o "Processed Data 2-gram.csv"

#### Model Training and Validation

python3 model.py -i \<csv_paths\> \[Optional Arguments\]

|ARGUMENT|DESCRIPTION|
|---|---|
|--help, -h			    |Prints this help information|
|--input, -i \<csv_paths\>	    |Sets the paths to one or more input csv files, as comma separated values (Required)|
|--model, -m \<model\>		    |Sets the ML algorithm to use. Valid values are: (k)nn, (d)ecision_tree, (s)vm, or (a)ll (Default all)|
|--combined, -c \<combined\>	    |Sets if combined models should be analysed using consensus. Either (t)rue or (f)alse (Default true)|
|--type, -t \<category_type\>	    |Sets the category to train the model on. Either (t)ype or (g)roup (Default type)|
|--state, -s \<random_state\>	    |Sets the random_state value used in certain models (Default random)|
|--neighbors, -n \<n_neighbors\>    |Sets the number of neighbors used for the k-NN algorithm (Default 4)|
|--output, -o \<output_string\>	    |Enables different outputs. The string can contain the following characters: p for accuracy, recall, precision, and f1 score printouts, g to plot the scores graph, m for confusion matrix plot, n for no output (Default pgm)|

Example commands for ML training are:

python model.py -i "Processed Data 1-gram.csv,Processed Data 2-gram.csv" -m all -c true -n 4 -o pgm -s 42 -t type

python model.py -i "Processed Data 1-gram.csv,Processed Data 2-gram.csv" -m all -c true -n 4 -o pgm -s 42 -t group
