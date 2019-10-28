# SQL Server 2017 Installation Guide
##### Option 1: Native Windows
For native Windows enviroments, SQL Server can be downloaded from [SQL Server Downloads](https://www.microsoft.com/en-us/sql-server/sql-server-downloads). This option was not tested and support from the author of this guide isn't available. Read the instructions for support.
##### Option 2: Windows (only Pro and Enterprise versions) and Linux
For these specific Windows versions and Linux the use of Docker is supported. Docker is an application that allows users and developers to separate (containarize) applications into different containers.
###### Windows Installation:
For the Windows version a Docker Hub account needs to be created at the [Docker Hub](https://hub.docker.com/signup).
After that Docker For Windows can be downloaded [here](https://hub.docker.com/?overlay=onboarding).
###### Linux Installation:
For the Linux version of docker you can simply use the package manager of your distro. In Arch Linux, for example, pacman can be used and we can install docker by running:
```
sudo pacman -S docker
```
##### Docker SQL configuration
After the installation of Docker we need to create a Microsoft SQL Server 2017 container to support our relational DBMS. To create the container run this command in your system command line:
```
docker run --name sql -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=yourStrong(!)Password' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```
Warning 1: **In Windows replace all single-quotes with double-quotes**
Warning 2: **In Linux you need to run this command with superuser**
Warning 3: **Don't forget to replace the SA_PASSWORD with a strong password. If there's any error connecting to the container later on this may be the cause of such error.**

Finally to start your SQL container you can simply run
```
docker start sql
```
Warning 1: **In Linux you need to run this command with superuser**

To check that our container is running we can execute:
```
docker ps
```
Warning 1: **In Linux you need to run this command with superuser**

If the container is not shown an error occurred and further research is required. Try searching about the `docker logs` command. (If the container is not running it will show by executing `docker ps -a`)
##### Accessing your DBMS
To access your newly created SQL Server with DBeaver, for example, you can use the following connection details:
```
host: localhost
port: 1433
user: sa
password: the password you chose
```
That should connect you to the database. If it does not please read above again.