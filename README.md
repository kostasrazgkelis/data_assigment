# Channel VAS - Assignment for the position of Junior Data Engineer

For this assignment we will be creating on the Docker platform an Apache Spark cluster running in a local machine with 4 nodes (1 master, 3 workers). We will be also using 
the Jupyter Notebook in order to run PySpark commands and SQL commands.

System Requirements:
  - It is expected that Docker is installed in the machine of the tester. (IN THIS FILE WE WILL DISCUSS WHAT TOOLS ARE USED FROM THE DOCKER SOFTWARE AND NOT HOW TO INSTALL IT)
  
  
Implementation of the environment:

  Step 1: We need to pull the docker-compose.yml file from this repository. This file has all the information that our system needs in order to create the correct containers.

  Step 2: After we have pulled the docker-compose.yml file we need to open a Command Prompt and run the command "docker compose up" and docker will start building the containers.
          Now we have created our Jupyter Notebook, the master and 3 workers services which they are all mounted on the same volume which acts as the HDFS of an Apache Hadoop
          system. The mount point is the volume 'shared-workspace:/opt/workspace' where we will place our input data and output data.

  Step 3: We need to upload the data. For the purpose of this task a CSV file ( cvas_data.csv) was given. We need to place the csv file in our HDFS. Since our last Command Prompt 
          is running the logs of the services we need to start a new one. In this CMD we will run the command "docker cp cvas_data.csv spark-master:/opt/workspace" which it will 
          copy the data inside the HDFS. 
          
  Step 4: Finally, we have our system and data ready and running. We need to open our Jupyter Notebook which runs at "localhost:8888" HTTP address. This url is provided in the 
          logs when we first start our Jupyter service. Inside the Git repository, we provide a Jupyter Notebook file which has all the PySpark commands to read and clean the data 
          like it is required in the assignment task. In the end, we save the output file in the HDFS and it is ready to use SQL queries to take the information we need.
            
          
 
 
 
PS: All the commands and methods are used from the pyspark.sql module except the method that saves the dataframe into a parquet which it led to many errors. After some time where 
I could not find the solution, I decided in order to finish this task to use the pandas module.
