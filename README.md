# Housing Data Analysis

## Project Overview
This repository showcases my work on housing data analysis. Through this project, I've learned how to fetch datasets, explore them, and perform basic operations like data loading and initial exploration using Python and its powerful libraries like `pandas`.

## What I've Learned

- **Data Acquisition**: I learned how to download and extract data from online sources using Python's `urllib` and `tarfile` modules. This gave me hands-on experience with handling compressed files and managing data directories.
  
- **Data Loading**: I became proficient in loading CSV data into a pandas DataFrame for further processing and analysis. This step is crucial in any data science workflow.
  
- **Data Exploration**: I learned how to inspect datasets to understand their structure and key characteristics. I used methods like `head()`, `info()`, and basic pandas functionality to examine data types, memory usage, and missing values.

## Key Features of the Project

- **Fetch Data**: The script downloads the housing dataset from a remote source and extracts it into a local directory for use.
- **Data Loading**: It loads the dataset into a pandas DataFrame for easier manipulation and analysis.
- **Basic Data Exploration**: The notebook includes code to explore the dataset, checking the first few rows and getting metadata about the dataset such as column names, data types, and memory usage.

## Getting Started

### Prerequisites

To run the project, you need to have the following Python libraries installed:

- `pandas`
- `six`
- `urllib`
- `tarfile`

You can install the necessary libraries by running:

```bash
pip install pandas six
```

### Fetching and Extracting the Dataset

The data is downloaded from [this URL](https://raw.githubusercontent.com/ageron/handson-ml/master/datasets/housing/housing.tgz). The function `fetch_housing_data()` handles downloading and extracting the dataset automatically.

```python
import os
import tarfile
from six.moves import urllib

DOWNLOAD_ROOT = "https://raw.githubusercontent.com/ageron/handson-ml/master/"
HOUSING_PATH = "datasets/housing"
HOUSING_URL = DOWNLOAD_ROOT + HOUSING_PATH + "/housing.tgz"

def fetch_housing_data(housing_url=HOUSING_URL, housing_path=HOUSING_PATH):
    if not os.path.isdir(housing_path):
        os.makedirs(housing_path)
    tgz_path = os.path.join(housing_path, "housing.tgz")
    urllib.request.urlretrieve(housing_url, tgz_path)
    housing_tgz = tarfile.open(tgz_path)
    housing_tgz.extractall(path=housing_path)
    housing_tgz.close()
```

### Loading the Data

After fetching the dataset, I load it into a pandas DataFrame using the `load_housing_data()` function:

```python
import pandas as pd

def load_housing_data(housing_path=HOUSING_PATH):
    csv_path = os.path.join(housing_path, "housing.csv")
    return pd.read_csv(csv_path)
```

### Data Exploration

Once the data is loaded, I can explore it to get a better understanding of its structure and contents.

- **First five rows of the data**:

```python
housing = load_housing_data()
housing.head()
```

- **Dataset info (columns, types, missing values)**:

```python
housing.info()
```

## Running the Project

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/yourusername/housing-data-analysis.git
   cd housing-data-analysis
   ```

2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Run the Jupyter Notebook:

   ```bash
   jupyter notebook project_housing.ipynb
   ```

## Future Learning Goals

- **Data Cleaning**: In the future, I aim to handle missing values and outliers in the dataset.
- **Feature Engineering**: I want to learn how to create new features to better represent the data and improve model performance.
- **Machine Learning**: I plan to apply machine learning algorithms on this dataset to predict housing prices and gain insights from the data.

