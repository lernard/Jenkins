# Jenkins

This is the Jenkins course code for www.lernard.com. It accompanies the lessons that can be found in Chapter 4 of the Lernard courses, at https://https://www.lernard.com/courses/a99xa0jqh6

## Installing Jenkins

The second section in the Jenkins course after the introduction deals with installing Jenkins. Rather than having to painstakingly copy out the commands you see in the lesson, you can cut and paste them from this readme below.

For installing most things on Ubuntu, I can highly recommend just using a search engine and typing the words "Install [ whatever ] on Ubuntu 18.04" and usually the first hit will be an excellent page on how to install that very thing. 

### First install java 8

1. sudo apt install openjdk-8-jdk

### Now add the Jenkins package repo and install Jenkins

2. wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
3. sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
4. sudo apt update
5. sudo apt install jenkins

### Now start the jenkins service, and make it start when the server boots

6. sudo systemctl start jenkins
7. sudo systemctl enable jenkins

### Finally, if you are running on a remote server, configure the ubuntu firewall

8. sudo ufw allow 8080
9. sudo ufw status

Now browse to http://localhost:8080 to continue the setup in the web browser, as per the video.