# Apache Tomcat Init Configuration

## Ex : MacOS M1 Chips

### 1. Download

Go to https://tomcat.apache.org/download-10.cgi

+ Choose the version you are going to use

+ Click `tar.gz (pgp, sha512)` to download
+ Unzip the folder you just download



### 2. Configuration 

1. Open your ternimal, type the following command lines step by step: 

```
cd apache-tomcat-10.1.10 
```

```
cd bin
```

```
ls-al *.sh
```

2. you will find all the .sh file in this folder, example:

`-rwxr-x---@ 1 yun  staff    23K Jun  2 14:11 catalina.sh
-rwxr-x---@ 1 yun  staff   2.0K Jun  2 14:11 ciphers.sh
-rwxr-x---@ 1 yun  staff   1.9K Jun  2 14:11 configtest.sh
-rwxr-x---@ 1 yun  staff   8.1K Jun  2 14:11 daemon.sh
-rwxr-x---@ 1 yun  staff   1.9K Jun  2 14:11 digest.sh
-rwxr-x---@ 1 yun  staff   3.3K Jun  2 14:11 makebase.sh
-rwxr-x---@ 1 yun  staff   1.9K Jun  2 14:11 migrate.sh
-rwxr-x---@ 1 yun  staff   3.8K Jun  2 14:11 setclasspath.sh
-rwxr-x---@ 1 yun  staff   1.9K Jun  2 14:11 shutdown.sh
-rwxr-x---@ 1 yun  staff   1.9K Jun  2 14:11 startup.sh
-rwxr-x---@ 1 yun  staff   4.5K Jun  2 14:11 tool-wrapper.sh
-rwxr-x---@ 1 yun  staff   1.9K Jun  2 14:11 version.sh`

3. type this command line: 

```
chmod +x *.sh
```

​	you will find the .sh files' permission was been changed:

`ls: s-al: No such file or directory

-rwxr-x--x@ 1 yun staff  23K Jun 2 14:11 catalina.sh

-rwxr-x--x@ 1 yun staff  2.0K Jun 2 14:11 ciphers.sh

-rwxr-x--x@ 1 yun staff  1.9K Jun 2 14:11 configtest.sh

-rwxr-x--x@ 1 yun staff  8.1K Jun 2 14:11 daemon.sh

-rwxr-x--x@ 1 yun staff  1.9K Jun 2 14:11 digest.sh

-rwxr-x--x@ 1 yun staff  3.3K Jun 2 14:11 makebase.sh

-rwxr-x--x@ 1 yun staff  1.9K Jun 2 14:11 migrate.sh

-rwxr-x--x@ 1 yun staff  3.8K Jun 2 14:11 setclasspath.sh

-rwxr-x--x@ 1 yun staff  1.9K Jun 2 14:11 shutdown.sh

-rwxr-x--x@ 1 yun staff  1.9K Jun 2 14:11 startup.sh

-rwxr-x--x@ 1 yun staff  4.5K Jun 2 14:11 tool-wrapper.sh

-rwxr-x--x@ 1 yun staff  1.9K Jun 2 14:11 version.sh`

4. type in :  to start your web broser in chorme

```
./startup.sh
```

5. Open chorme: type `localhost: 8080`
6. If the page show, Apache tomcat configure successfully
7. type in : to shutdown the connection 

```
./shutdown.sh
```

### 

### 3. Init 

Open the `webapps`  folder, you can put your project in it. It alrrady init some project, you could check them, or just ignore them.



### 4. Change the :8080 port 

if you want to change your port, just open `conf` folder, open `server.xml`to change the port.



==Note==: Video Link : https://www.youtube.com/watch?v=2KD7L8j1tio

