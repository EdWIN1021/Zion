# Jenkins

### docker 

```shell
docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins
```

### check password

```shell
docker logs <container-id>
```

### jenkinsfile

```
pipeline {
	agent any
	
	stages {
	    stage("build") {
	        stages {
				sh 'npm install'
	            sh 'npm build'
	        }
	    }
	
	    stage("test") {
	        stages {
	
	        }
	    }
	
	    stage("deploy") {
	        stages {
	
	        }
	    }
	}
}
```