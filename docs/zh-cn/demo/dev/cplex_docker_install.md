[toc]

## CPLEX on docker

### Download

in matrix os, create a new script `download.py` and download the executable file to `uos`, eg. `/uos/demo/`

```shell
pip install gdown
```

```python
import gdown
"""
https://stackoverflow.com/questions/38511444/python-download-files-from-google-drive-using-url
"""
url = "https://drive.google.com/uc?id=1MLUJZ7W186RrhQd4zKlimWLJKClzyUIc&authuser=zjin%40ctps.org&usp=drive_fs"
output = "cplex_studio128.linux-x86-64.bin"
gdown.download(url,output,quiet=False)

```

List the downloaded file and see the new file named `cplex_studio128.linux-x86-64.bin`

```shell
(base) root@b37a5642a4b9:/uos/demo/cplex# ls
cplex_studio128.linux-x86-64.bin   download.py  requirement.txt  
```



### install

1. Make sure the .bin file is executable. If necessary, change its permission using the chmod command from the directory where the .bin is located:

```
cd /uos/demo/cplex

chmod +x cplex_studio128.linux-x86-64.bin
```

2. install Java env

   ```
   ./cplex_studio128.linux-x86-64.bin
   
   ----
   Preparing to install
   Extracting the JRE from the installer archive...
   Unpacking the JRE...
   Extracting the installation resources from the installer archive...
   Configuring the installer for this system's environment...
   No Java virtual machine could be found from your PATH
   environment variable.  You must install a VM prior to
   running this program.
   
   --------solution 
   
   https://stackoverflow.com/questions/67920408/no-java-virtual-machine-could-be-found-from-your-path-environment-variable-you
   
   > Maybe it has been too late but i encounter the same problem when installing the CPLEX progrom. I had found the solution here at IBM support. Simply pass the java path using the LAX_VM flag.
   
   https://www.ibm.com/docs/en/ds8870/7.3?topic=HW213_7.3.0/com.ibm.storage.ssic.help.doc/f2c_clijavaerror_2lfq3j.html
   
   After ensuring that Java 6 or later is installed, complete one of the following actions to correct the Java Virtual Machine Not Found error:
   ```

   * install Java 6 Java 6 or later [guide](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-do-I-install-Java-on-Ubuntu)

     * before installing openjdk-8-jre-headless, running 

     ```shell
     ## https://github.com/geerlingguy/ansible-role-java/issues/64
     mkdir -p /usr/share/man/man1
     ```

     Then,

     ```shell
     
     ##  install the JRE instead
     ## The full Java suite includes the Java Runtime Environment (JRE), 
     ### The JDK additionally has a few extra features packaged with it to facilitate software development.
     apt install default-jre
     ```

     Check the version and java PATH

     ```
     java --version
     
     (base) root@b37a5642a4b9:/uos/demo/cplex# which java
     /usr/bin/java
     
     ```

   * install bin file with Java PATH


   ```
   ./cplex_studio128.linux-x86-64.bin LAX_VM /usr/bin/java
   ```

   ```shell
   Preparing to install
   Extracting the JRE from the installer archive...
   Unpacking the JRE...
   Extracting the installation resources from the installer archive...
   Configuring the installer for this system's environment...
   
   Launching installer...
   
   ===============================================================================
   Choose Locale...
   ----------------
   
       1- Deutsch
     ->2- English
       3- Espa?ol
       4- Fran?ais
       5- Portugu?s  (Brasil)
       
       
   ==== agreement  ...===
   skip chekcing the agreements
   ====
   
   Choose Install Folder
   ---------------------
   
   Where would you like to install?
   
     Default Install Folder: /opt/ibm/ILOG/CPLEX_Studio128
     
     ===============================================================================
   Pre-Installation Summary
   ------------------------
   
   Please Review the Following Before Continuing:
   
   Product Name:
       IBM ILOG CPLEX Optimization Studio 12.8.0
   
   Install Folder:
       /opt/ibm/ILOG/CPLEX_Studio128
   
   Product Version
       12.8.0
   
   Disk Space Information (for Installation Target): 
       Required:    1,831,327,268 Bytes
       Available: 249,194,717,184 Bytes
       
       
   Installation Complete
   ---------------------
   
   IBM ILOG CPLEX Optimization Studio 12.8.0 has been successfully installed to:
   
      /opt/ibm/ILOG/CPLEX_Studio128
   ```

   


`````````````````````shell
test installation:

/opt/ibm/ILOG/CPLEX_Studio128/cplex/bin/x86-64_linux/cplex

or 
--------
cd /opt/ibm/ILOG/CPLEX_Studio128/cplex/bin/x86-64_linux
./cplex

````````````````````

Welcome to IBM(R) ILOG(R) CPLEX(R) Interactive Optimizer 12.8.0.0
  with Simplex, Mixed Integer & Barrier Optimizers
5725-A06 5725-A29 5724-Y48 5724-Y49 5724-Y54 5724-Y55 5655-Y21
Copyright IBM Corp. 1988, 2017.  All Rights Reserved.

Type 'help' for a list of available commands.
Type 'help' followed by a command name for more
information on commands.

CPLEX> 
"q" to exit
`````````````````````

### [How can I make a program executable from everywhere](https://unix.stackexchange.com/questions/3809/how-can-i-make-a-program-executable-from-everywhere) 

```shell
vi ~/.bashrc
or 
/usr/bin/vi ~/.bashrc

## type `i` to enter insert mode
```

```shell
## add the following path to ~/.bashrc

PATH="/opt/ibm/ILOG/CPLEX_Studio128/cplex/bin/x86-64_linux:$PATH"
export PATH

## type 'esc' exit from insert mode
## type ":wq" to save and quit from vi editor
```

```shell
## in terminal
export PATH=$PATH:opt/ibm/ILOG/CPLEX_Studio128/cplex/bin/x86-64_linux
```

```shell
echo $PATH
```

```shell
## activate PATH
source ~/.bashrc
[ ok ] Starting OpenBSD Secure Shell server: sshd.
```

`````````````````````shell
## test if cplex is callable 

cplex
````````````````````

Welcome to IBM(R) ILOG(R) CPLEX(R) Interactive Optimizer 12.8.0.0
  with Simplex, Mixed Integer & Barrier Optimizers
5725-A06 5725-A29 5724-Y48 5724-Y49 5724-Y54 5724-Y55 5655-Y21
Copyright IBM Corp. 1988, 2017.  All Rights Reserved.

Type 'help' for a list of available commands.
Type 'help' followed by a command name for more
information on commands.

CPLEX> 
"q" to exit
`````````````````````




