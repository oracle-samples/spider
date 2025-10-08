# Spider 1.0 (Oracle Conversion)

Converted version of the Spider 1.0 dataset for Oracle. This repository contains only data and usage notes. 

The original Spider dataset is here: 
https://yale-lily.github.io/spider

## Installation

No software installation is required for this repository.
Use the files directly with your existing Oracle tools and environment

## Documentation

### Dataset contents
`ddl.jsonl` -
contains DDL statements for creating database tables. Each line is a JSON object with:      
&nbsp;&nbsp;&nbsp;&nbsp;`table`: Table name    
&nbsp;&nbsp;&nbsp;&nbsp;`sql`: CREATE TABLE statement in Oracle syntax


`dml.json`-
contains DML  statements - specifically INSERT statements to populate tables. Structure is:   
&nbsp;&nbsp;&nbsp;&nbsp;`metadata`: Batch information and execution statistics   
&nbsp;&nbsp;&nbsp;&nbsp;`tables`: Object containing all table names with their INSERT statements



`dev_pairs.jsonl` -
Dev dataset containing question-query pairs. Each line has:    
&nbsp;&nbsp;&nbsp;&nbsp;`question`: Natural language question   
&nbsp;&nbsp;&nbsp;&nbsp;`query`: Corresponding SQL query in Oracle syntax   
&nbsp;&nbsp;&nbsp;&nbsp;`db_name`: Database name the query applies to   



`train_others_pairs.jsonl` -
Training dataset with question-query pairs. Format is similar to `dev_pairs.jsonl`:
&nbsp;&nbsp;&nbsp;&nbsp;`question`: Natural language question   
&nbsp;&nbsp;&nbsp;&nbsp;`query`: Oracle SQL query   
&nbsp;&nbsp;&nbsp;&nbsp;`db_name`: Database name   



`train_spider_pairs.jsonl`-
Main training dataset with question-query pairs. Similar format as `dev_pairs.jsonl`   
&nbsp;&nbsp;&nbsp;&nbsp;`question`: Natural language question
&nbsp;&nbsp;&nbsp;&nbsp;`query`: Oracle SQL query   
&nbsp;&nbsp;&nbsp;&nbsp;`db_name`: Database name

### Notes and Guidance
* Run DDLs first to create and recreate objects; then run DML to populate data

* If you change schema or naming, apply a consistent prefix to table names in both `CREATE TABLE` and `INSERT INTO` statements

* Use explicit date/time conversions (e.g., `TO_DATE`/`TO_TIMESTAMP`) rather than relying on session NLS settings

* Use `executemany` to run speed up bulk inserts and updates


## Security

Please consult the [security guide](./SECURITY.md) for our responsible security vulnerability disclosure process

## License
Copyright (c) 2025 Oracle and/or its affiliates.

Released under the Universal Permissive License v1.0 as shown at
<https://oss.oracle.com/licenses/upl/>.
