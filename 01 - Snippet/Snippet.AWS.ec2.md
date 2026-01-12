## EC2 instance

```bash
chmod 400 "<key>.pem"
```

### ssh to ec2

```bash
ssh -i "<key>.pem" ec2-user@ec2-54-80-252-170.compute-1.amazonaws.com
```

### Update the installed packages on the system

```bash
sudo yum update -y
```

### Install docker

```bash
sudo amazon-linux-extras install docker
```

### Start docker

```bash
sudo service docker start
```

```
sudo usermod -a -G docker ec2-user
```

### Build docker image locally

```bash
docker build --platform linux/amd64
```

### restart docker

```
sudo service docker restart
```

### Push to docker hub

```bash
docker push
```

### Run docker container in ec2

```bash
docker run
```

### Add the Jenkins repo using the following command

```
sudo wget -O /etc/yum.repos.d/jenkins.repo \\
    <https://pkg.jenkins.io/redhat-stable/jenkins.repo>
```

### Import a key file from Jenkins-CI to enable installation from the package

```
sudo rpm --import <https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key>
```

```
sudo yum upgrade
```

### install java

```
sudo yum install java-17-amazon-corretto
```

### Install Jenkins

```
sudo yum install jenkins -y
```

### Enable the Jenkins service to start at boot

```
sudo systemctl enable jenkins
```

### Start Jenkins as a service

```
sudo systemctl start jenkins
```

### check the status and `key` of the Jenkins service using the command

```
sudo systemctl status jenkins
```

### add jenkins user to docker group

```
sudo usermod -aG docker jenkins
```

### Restart jekins

```
sudo systemctl restart jenkins
```

### Add Inbound rules
<img width="1080" alt="Untitled" src="https://github.com/EdWIN1021/cheatsheet/assets/17692914/f127b934-b5c9-4274-96e9-419664fbfb30">

