# Automatic File Sorter (Python)

A Python script, written in a Jupyter notebook, that cleans up a cluttered folder by sorting files into subfolders by file type.

## What it does

Given a folder, the notebook:

1. Creates the subfolders `csv files`, `image files`, and `text files` if they don't exist
2. Reads each file's extension
3. Moves the file into the matching subfolder
4. Skips any file whose name already exists in the destination, so nothing is overwritten
5. Prints each move and a summary of how many files were moved or skipped

**Before**
```
automatic file sorter folder/
├── sales.csv
├── chart.png
├── notes.txt
└── report.docx
```

**After**
```
automatic file sorter folder/
├── csv files/
│   └── sales.csv
├── image files/
│   └── chart.png
├── text files/
│   └── notes.txt
└── report.docx          
```

## Tools

Python 3, the built-in `os` and `shutil` modules, and Jupyter Notebook

## How to run it

1. Open `Automatic_File_Sorter.ipynb` in Jupyter.
2. Change the `path` variable to the folder you want to sort.
3. Choose **Kernel → Restart & Run All Cells**.

To sort more file types, add their extensions to the `folders` dictionary.

## How it works

- A dictionary maps each folder name to its file extensions, so adding a new type takes one line instead of a new `if` block.
- `os.path.splitext` reads the real extension, so a name like `data.csv.bak` isn't treated as a CSV.
- Extensions are converted to lowercase, so `.CSV` and `.csv` are handled the same way.
- `os.path.isfile` makes the script ignore folders, so the subfolders it creates are never moved.
- `os.makedirs(..., exist_ok=True)` creates folders safely whether or not they already exist.

## What I learned

- Automating file management with `os` and `shutil`
- Replacing repeated `if/elif` blocks with a dictionary
- Why checking a file's actual extension is safer than searching for text in its name
- Testing a script on a sample folder before running it on real files

## Ideas for next steps

- Add more file types, such as PDFs, Excel files, and Word documents
- Sort files into dated folders
- Turn the notebook into a `.py` script that runs from Terminal
