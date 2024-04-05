# mysql-docker-commands

markdown
Copy code
# MySQL Commands for Docker

This `.readme` file contains a list of useful commands for working with MySQL in Docker containers. These commands can help you manage MySQL instances, databases, and data within Docker environments.

## Useful Commands

### Run MySQL Container

# docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=your_password -d mysql:latest
Starts a new MySQL container with the specified root password.

Stop MySQL Container
bash
Copy code
# 
    docker stop mysql-container
Stops the running MySQL container named mysql-container.

Start MySQL Container
bash
Copy code
#            
      docker start mysql-container
Starts the previously stopped MySQL container named mysql-container.

Restart MySQL Container
bash
Copy code
#   
     docker restart mysql-container
Restarts the MySQL container named mysql-container.

Remove MySQL Container
bash
Copy code
#          
       docker rm mysql-container
Removes the MySQL container named mysql-container. Use with caution as this will delete all data in the container.

Connect to MySQL CLI
bash
Copy code

      docker exec -it mysql-container mysql -u root -p
Connects to the MySQL CLI inside the running MySQL container. You will be prompted to enter the root password.

Create a New Database (from MySQL CLI)
sql
Copy code
       
        CREATE DATABASE your_database_name;
Creates a new database with the specified name.

List Docker Containers
bash
Copy code
 
       docker ps -a
Lists all Docker containers, including stopped ones (-a flag).

          View Docker Container Logs
bash
Copy code
             
             docker logs mysql-container
Displays the logs of the MySQL container named mysql-container.

       Inspect Docker Container
bash
Copy code 
       
       docker inspect mysql-container
Displays detailed information about the MySQL container named mysql-container, including IP address, configuration, etc.

      Copy Files to/from Container
bash
Copy code
        
        docker cp /path/to/local/file.txt mysql-container:/path/in/container/file.txt
Copies a file from your local machine to the specified path inside the MySQL container.

Export MySQL Database Dump
bash
Copy code

        docker exec mysql-container mysqldump -u root -p your_database_name > database_dump.sql
Exports a MySQL database dump from the container to a file named database_dump.sql on your local machine.

Import MySQL Database Dump
bash
Copy code 

          docker exec -i mysql-container mysql -u root -p your_database_name < database_dump.sql
Imports a MySQL database dump file (database_dump.sql) into the specified database in the MySQL container.

Additional Commands
Connect to MySQL using MySQL Workbench:

bash
Copy code
            
            mysql -h localhost -P 3306 -u root -p
Show MySQL Container IP Address:

bash
Copy code
 
         docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mysql-container
Access MySQL Shell in Running Container:

bash
Copy code
          
          docker exec -it mysql-container mysql -u root -p
Access MySQL Shell in Specific Database:

bash
Copy code
      
      docker exec -it mysql-container mysql -u root -p your_database_name
Execute SQL File in MySQL Container:

bash
Copy code
    
    docker exec -i mysql-container mysql -u root -p your_database_name < your_sql_file.sql
Export MySQL Database as CSV:

bash
Copy code
 
    docker exec mysql-container mysqldump -u root -p --fields-enclosed-by='"' --fields-terminated-by=',' --fields-escaped-by='\\' --tab=/path/in/container your_database_name your_table_name
Import CSV Data into MySQL Table:

bash
Copy code
     
     docker exec -i mysql-container mysql -u root -p --local-infile=1 -e "LOAD DATA LOCAL INFILE '/path/in/container/your_csv_file.csv' INTO TABLE your_table_name FIELDS TERMINATED BY ',' ENCLOSED BY '\"' ESCAPED BY '\\\\' LINES TERMINATED BY '\\n' IGNORE 1 LINES;"
You can save this content in a single file named README.readme or any other suitable name in your project directory or documentation folder for easy reference and usage of MySQL commands in Docker environments. Adjust the commands and placeholders as needed for your specific setup and requirements.




