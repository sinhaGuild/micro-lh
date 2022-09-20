# 1. MSSQL - DREMIO - TABLEAU

# Run container

```
docker run -e 'HOMEBREW_NO_ENV_FILTERING=1' -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=yourStrong(!)Password" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

# Install the ODBC Driver and SQL Command Line Utility for SQL Server

```
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=Y brew install msodbcsql17 mssql-tools
```

# Connect to SQL

```
sqlcmd -S 127.0.0.1 -U sa -P yourStrong(!)Password
sqlcmd -S 127.0.0.1 -U sa -P yourStrong(!)Password -Q "SELECT @@VERSION"
```

SQL command tool can be used inside the container

```
docker exec -it <container_id|container_name> /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P yourStrong(!)Password
```

# Alternative containers

MS SQL Express Edition

```
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=yourStrong(!)Password" -e "MSSQL_PID=Express" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

[Microsoft SQL Server at Docker Hub](https://hub.docker.com/_/microsoft-mssql-server)

Developer : This will run the container using the Developer Edition (this is the default if no MSSQL_PID environment variable is supplied)
Express : This will run the container using the Express Edition
Standard : This will run the container using the Standard Edition
Enterprise : This will run the container using the Enterprise Edition
EnterpriseCore : This will run the container using the Enterprise Edition Core
