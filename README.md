# Data_Transformation_Benchmark
## Benchmark Datasets
- `Smart Building` : Smart building dataset is curated from real-world domain specific databases. This makes total 15 groups for 105 total cases from 21 energy companies in the United States.

- `COVID-19 & Machine Log` : COVID-19 datasets is real-world data repository maintianed by John Hopkins University {[Link](csse_covid_19_data)}. Machine log dataset is curated from various operating systems such as MacOS, Android etc. 

- `Commertial dataset-1` : This consists of eight groups of single-table transformation from exisitng Autopipeline benchmark {[Link](https://gitlab.com/jwjwyoung/autopipeline-benchmarks/-/tree/main/commercial-pipelines?ref_type=heads)}.

- `Commertial dataset-2` :  This consists of eight groups of join transformation from exisitng Autopipeline benchmark {[Link](https://gitlab.com/jwjwyoung/autopipeline-benchmarks/-/tree/main/commercial-pipelines?ref_type=heads)}. 

Below is table for

| Datasets      | Number of Groups | Total cases |
| ------------- |:-------------:| -----:|
| Smart Building      | 15 | 105 |
| COVID-19 & Machine Log      | 2      |  6 |
| Commertial-1 | 8    |    8 |
| Commertial-2 | 8    |    8 |

## Structure Of Datasets

- `Group Number` is number for each group in the benchmark dataset. 
- `Target Data Name` is given name to transformed dataset. The representation is "Target'Group Number'" e.g. Target1 represents target data name for Group 1.
- `Target Data Schema` is transformed schema. 
- `Target Data Description` is domain specific explanation about dataset. 
- `Source Data Name` is given name for dataset to be transformed. The representation is "Source'Group Number_SourceNumber'" e.g. Source1_1 represents source data name for Group 1 for source 1. 
- `Source Data Schema` is schema to be transformed. 
- `Source Data Description` is domain specific explanation about dataset. 
- `Schema Change Hints` are hints about changes in schema from source to target. 
- `5 Samples of Source Data` are sample values for source schema.
- `Ground Truth SQL` are for validation of the generated SQL response from large language models.  




## How to use our benchmark
1. Clone the repository:
    ```bash
    git clone https://github.com/asu-cactus/ChatGPTwithSQLscript.git
    ```
2. Navigate to the project directory:
    ```bash
    cd ChatGPTwithSQLscript
    ```
3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```
4. Create a `config.py` file and put your OpenAI API key there.
    ```
    OPENAI_API_KEY = "{your_openai_api_key}"
    ```
5. Pick a dataset from {‘Smart Building’, ‘COVID-19 & Machine Log’,Commercial dataset-1’, ‘Commercial dataset-2’} and change the ‘excel_file_path’ and ‘json_file_path’ in ‘excel2json.py’ accordingly.
    ```
    # Path to the Excel file
    excel_file_path = '<dataset_you_picked>.xlsx'
    # Path to save the JSON file
    json_file_path = <dataset_you_picked>.json'
    ```
6. Run the `excel2json.py` script to convert the .xlsx benchmark dataset to .json format:
    ```bash
    python excel2json.py
    ```
7. You can set the configurations such as template_option, source, target in run.py. Here's an example
    ```
    template_option = 1
    target_id, max_target_id = 26, 26
    source_id, max_source_id = 1, 1
    ```

    `target_id`,`max_target_id` mean the first group and the last group the script will iterate.
    `source_id`, `max_source_id` mean the first source and the last source the script will iterate.
8. Run the run.py script to start the experiment:
    ```bash
    python run.py
    ```


## How to extend our benchmark
You can build your own dataset following the [Structure Of Datasets](#structure-of-datasets) to extend this benchmark.


The new spreadsheet muct have above explained structure of the datasets. 
