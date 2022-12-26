### Elastic Backup Configuration

The script configures the s3 buckets and then initiates snapshot process.

##### _Requirements_
we need the following python packages:
  - Jinja2==2.11.3
  - PyYaml==5.4.1
  - requests==2.25.1

We will also require python3 installed 
and pip version 21.0.1


##### Using `venv` 
Python3 comes with virtual env module which can help keep the env isolated from root packages.

*Steps*:
  - within the folder use the following command:
    ```
    python3 -m venv .
    ```
  - this will setup a venv folder and then we need to activate the virtual env:
    ```
    source venv/bin/activate
    ```
  - Once activated the pip can be upgraded easily.

  - now, we can install the packages and they won't be affecting our root system. To install the packages:
    ```
    pip install -r reqirements.txt
    ```

    
##### Running the Script
The `configuration` folder contains the templates and yamls.

The YAML file (configuration/es.yaml) is used as metadata and contains the configuration that we will use.

The templates will help generate the payload for every curl request.

we have the following structure of the yaml
```
---
config:
  url: "<URL for the elasticsearch instance>"
  repository: "<name of repository>"
  bucket:
    s3: "<name of s3 bucket>"
    region: "us-east-1"
    snapshot:
      indices:
        - <index-*>
        - <_all>
```

Run the script as follows:
````
 # export the aws access key and secret key
 
 export AWS_ACCESS_KEY_ID=**********
 export AWS_SECRET_ACCESS_KEY=***********
 
 ./elastic_configure.py --metadata configuruation/es.yaml
````

