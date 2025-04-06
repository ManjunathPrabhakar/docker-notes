# docker-postgres-db

### DOWNLOAD POSTGRES IMAGE
* Refer Docker Hub : https://hub.docker.com/_/postgres?uuid=D72549DD-FF19-404B-B3C0-4E853493AB49
* Command to Pull (in CMD / Docker Terminal)
> docker pull postgres
* wait for the pull to be successful and complete
* Now youll see an image in DOcker Desktop with name "postgres"
* In Docker Desktop : Click on Run on that Image, and Give a container name(postgres-db), set host port(use same as it shows i.e 5432), In Environment Variables (enter POSTGRES_PASSWORD = password(or your own password))
* In Terminal :
  > docker run --name postgres-db -e POSTGRES_PASSWORD=password -d postgres
  

In SQL Developer: 
* download JDBC driver for Postgres (http://jdbc.postgresql.org/download/)
* in SQL Developer go to Tools → Preferences, Database → Third Party JDBC Drivers and add the jar file (see http://www.oracle.com/technetwork/products/migration/jdbc-migration-1923524.html for step by step example)
* <img width="795" alt="image" src="https://github.com/user-attachments/assets/ea12b559-8dfb-4f53-b405-c79045f29a88" />
* now just make a new Database Connection and instead of Oracle, select PostgreSQL tab
* <img width="569" alt="image" src="https://github.com/user-attachments/assets/78a1d56f-85bf-4c9c-b832-44c50065646e" />

connection string
> username: postgres, password: password, host: localhost, port: 5432

  


