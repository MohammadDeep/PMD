# PainMonit Dataset (PMD)
==change code lidares==
## Description
This repository summarises the code made publicly available for the **PainMonit Dataset** (PMD), which can be found via the following link: [PMD][PMD_link]

The dataset comprises two parts: the heat-based **PainMonit Experimental Dataset** ([PMED][PMED_link]) and the physiotherapy-based **PainMonit Clinical Dataset** ([PMCD][PMCD_link]). The code for the former can be found in the [PMED/](PMED/) directory, and the code for the latter can be found in the [PMCD/](PMCD/) directory.

A more detailed description of the dataset can be found in the paper **An Experimental and Clinical Physiological Signal Dataset for Automated Pain Recognition**, which was published in *Scientific Data* and can be accessed via the following [link][paper_link].

## How to use this repository
- Clone the project
    ```bash 
    git clone https://github.com/gouverneurp/PMD
    ```

- Install Python (tested under [Python 3.12](https://www.python.org/downloads/release/python-3120/)).

- Create a Python environment and activate it. 
    Windows:
    ```bash
    python -m venv venv
    .\venv\Scripts\activate
    ```
    Linux:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

- Install the requirements
    ```bash 
    pip install -r requirements.txt
    ```

## How to use the PMED
- Go to the subdirectory [PMED](PMED/)
    ```bash 
    cd PMED
    ```

- Place the PMED dataset (available under [link][PMED_link]) in the subdirectory [dataset](PMED/dataset/) following the description in the [README](PMED/dataset/README.md) file there.

- Run [create_np_files.py](PMED/create_np_files.py) to create a segmented dataset for machine learning. A numpy dataset composed of three files (_X.npy_, _y.npy_ and _subjects.npy_) will be generated.
    ```bash
    python create_np_files.py
    ```

- After creating the segmented dataset, a Machine Learning pipeline can be applied. An example of such can be found in the following paper '[Explainable Artificial Intelligence (XAI) in Pain Research: Understanding the Role of Electrodermal Activity for Automated Pain Recognition](https://www.mdpi.com/1424-8220/23/4/1959)'. The code is available on [GitHub](https://github.com/gouverneurp/XAIinPainResearch) as well.

- If you want to read in the original raw data files, you can do so in Python with the following code:
    ```python 
    pd.read_csv(filename, sep=";", decimal=",")
    ```
    where _filename_ is the path to the file of one subject.
    Functions on how to read in the data can be found in the [read_data.py](PMED/read_data.py) script.

- Functions on how the heater signal was cleaned can be found in the [heater.py](PMED/heater.py) script.

## How to use the PMCD
- Go to the subdirectory [PMCD](PMCD/)
    ```bash 
    cd PMCD
    ```
- Place the PMCD dataset (available under [link][PMCD_link]) in the directories under [dataset](PMCD/dataset/) following the description in the [README](PMCD/dataset/README.md) file there.

- Run [create_np_files.py](PMCD/create_np_files.py) to create a segmented dataset for machine learning. A Numpy dataset composed of three files (_X.npy_, _y\_heater.npy_, _y\_covas.npy_ and _subjects.npy_) will be generated.
    ```bash
    python create_np_files.py
    ```

- If you want to want to read in the original raw data files, you can do so by using the functions in the [read_data.py](PMCD/read_data.py) script:
    ```python 
    python read_data.py
    ```

## Please cite our paper if you use the PMD or our code
Bibtex entry:
```bibtex
@article{gouverneur2024experimental,
  title={An Experimental and Clinical Physiological Signal Dataset for Automated Pain Recognition},
  author={Gouverneur, Philip and Badura, Aleksandra and Li, Fr{\'e}d{\'e}ric and Bie{\'n}kowska, Maria and Luebke, Luisa and Adamczyk, Wac{\l}aw M and Szikszay, Tibor M and My{\'s}liwiec, Andrzej and Luedtke, Kerstin and Grzegorzek, Marcin and others},
  journal={Scientific Data},
  volume={11},
  number={1},
  pages={1051},
  year={2024},
  publisher={Nature Publishing Group UK London}
}
```

[PMD_link]: https://doi.org/10.6084/m9.figshare.26965159
[PMED_link]: https://github.com/gouverneurp/PMD/tree/main?tab=readme-ov-file#how-to-use-the-pmed
[PMCD_link]: https://github.com/gouverneurp/PMD/tree/main?tab=readme-ov-file#how-to-use-the-pmcd
[paper_link]: https://rdcu.be/enIRG
