# Subscriber Pipeline Starter Kit

This project automates the process of cleaning subscriber data, updating the SQLite database, and moving cleaned files from the **development** (`/dev`) directory into **production** (`/prod`).  
The pipeline is run through a Bash script (`deploy.sh`) which executes the Jupyter notebook using [Papermill](https://papermill.readthedocs.io/).

---

## 📂 Folder Structure
subscriber-pipeline-starter-kit/
│
├── dev/ # Development workspace
│ ├── cademycode.db # Source SQLite database
│ ├── Data_Pipeline.ipynb # Main Jupyter notebook (ETL pipeline)
│ ├── CleanedData.db # Output SQLite database for loading
│ ├── newlogs.log # General pipeline logs
│ ├── change.log # Captures errors during pipeline runs
│ └── Customer_data.csv # Raw / intermediate CSV data / Generated from Data_Pipeline.ipynb
│
├── prod/ # Production-ready files
│ ├── Customer_data.csv # moved Customer CSV from dev
│ ├── CleanedData.db # moved Database from dev
│ └── updated_Data_Pipeline.ipynb #gernerated by papermill
│
├── deploy.sh # Bash script to run & deploy pipeline
└── README.md # Project documentation (this file)


---

## ⚙️ Files and Roles

- **`dev/Data_Pipeline.ipynb`**  
  Main ETL notebook that loads data, cleans it, and updates the database.  

- **`dev/newlog.log`**  
  Records update history (e.g., rows added, schema changes). Used by the deployment script to decide if production needs updating.  

- **`dev/change.log`**  
  Captures runtime errors when executing the notebook. If non-empty, deployment aborts.  

- **`deploy.sh`**  
  Automates running the pipeline with Papermill. Handles logging, update detection, and file movement from `/dev` to `/prod`.  

- **`prod/` directory**  
  Holds the **latest production-ready outputs** (CSV + database + updated notebook).  

---

## 🚀 Running the Update Process

1. Make sure you have **Python**, **Papermill**, and **Jupyter** installed:  
   '''bash
   pip install papermill notebook
2. To run bash command and execute deploy.sh on windows, you need Git Bash or WSL on windows
3. Ensure the working directory is in the project root
    '''bash
   cd subscriber-pipeline-starter-kit
5. Run and deploy
   '''bash
      ./deploy.sh

🛡️ Notes

1. Always check /dev/change.log after each run to confirm updates were applied.

2. If you need to reset, clear error.log before re-running the deployment script. 

3. Use absolute paths for database connections to avoid missing-table errors when running via Papermill.
  
4. If the working environment is Jupyter Notebooks, Alaways clear exiting handlers on runtime to avoid adding handlers multiple times

5. Only create tables in a database that is not already existing to avoid OptionalErrors with table creation on each runTime.


