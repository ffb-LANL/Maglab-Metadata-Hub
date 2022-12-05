## Step 1: Install linux packages 
``` sh
sudo yum install nginx emacs java-1.8.0-openjdk-devel git
You can run java -version command to verify the JDK installation.
java -version
readlink -f $(which java)
```
## Step 2: Download the Maven Binaries
``` sh
wget https://mirrors.estointernet.in/apache/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz 
tar -xvf apache-maven-3.6.3-bin.tar.gz
sudo mv apache-maven-3.8.5 /opt/
```
## Step 3: Setting JAVA_HOME and maven home and Path Environment Variables
``` sh
emacs .bashrc
add to profile your variables.
export M2_HOME='/opt/apache-maven-3.8.5'
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.352.b08-2.el8_7.x86_64/jre/
PATH="$M2_HOME/bin:"$JAVA_HOME/bin:$PATH"                                                                                                                                                                                                                           
export PATH  
```
You can relaunch the terminal or execute source .bashrc command to apply the configuration changes.
Verify the Maven installation
``` sh
mvn -version
```
## Step 4:  Create directory for project
``` sh
sudo mkdir /data
sudo chown -R ludab:users /data 
cd /data
mkdir web
sudo chown -R ludab:users web
cd web
git clone https://github.com/luda171/Maglab-Metadata-Hub/
```
## Step 5 Nginx config
copy /data/web/Maglab-Metadata-Hub/magx.conf to /etc/nginx/conf.d
Adjust hostname, directories to your own
### start nginx
``` sh
sudo service nginx start
```
## Folow readme to config application 