# Docker Moodle
This is the Docker Image for The Moodle LMS
Using this makes it really easy to setup a moodle installation without setting up the apache server and MySQL databases all this is done through docker.

To get the latest version of moodle head over to [MOODLE_29_STABLE](https://github.com/moodle/moodle/tree/MOODLE_29_STABLE) and download the zip file. Then unzip this file to a folder and replace all `/path/to/moodle` with the location to this moodle source code folder.

Download or clone this repo and then within its folder run this command to build the docker image
### Step 1: Build the image
```bash
docker build --tag="playlyfe/moodle" .
```

### Step 2: Run the Container
```bash
docker run -d --name moodle -p 80:80 -p 3306:3306 -v /path/to/moodle:/var/www/html playlyfe/moodle
```

### Step 3: Configure Read/Write/Execute permissions to your moodle folder
Set permissions for all files in your moodle directory using
```bash
chmod -R 755 /path/to/moodle
```
This will then allow the moodle installation script to run and configure
your files accordingly. After this you can change your permissions back
(TODO:!Need to change this)

### Step 4: Installation
Then headover to http://localhost or http://127.0.0.1 and there you should see the moodle installation page. The Moodle installation might ask you for some details regarding your server and database. The details for the configuration is given below

**Moodle**
```
moodle_path: /var/www/html
moodle_data_path: /var/www/moodledata
```

**Apache Server**
```
host: localhost
```

**MySQL Database**
```
host: localhost
port: 3306
user: moodleuser
password: moodle
```

**Container**
```bash
sudo docker-enter moodle
docker stop moodle
docker start moodle
docker rm moodle
```
