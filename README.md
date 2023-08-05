# jenkins
Jenkins with agent

ERROR: anonymous is missing the Overall/Read permission
Aug 05, 2023 8:48:07 PM org.jenkinsci.remoting.engine.WorkDirManager initializeWorkDir
INFO: Using /home/jenkins/agent/remoting as a remoting work directory
Aug 05, 2023 8:48:08 PM org.jenkinsci.remoting.engine.WorkDirManager setupLogging
INFO: Both error and output logs will be printed to /home/jenkins/agent/remoting
Failed to obtain http://11.0.0.2:8080/computer/agent/jenkins-agent.jnlp?encrypt=true
java.io.IOException: Failed to load http://11.0.0.2:8080/computer/agent/jenkins-agent.jnlp?encrypt=true: 404 Not Found

https://github.com/TedFak/jenkins/blob/master/ansible/roles/deploy/templates/script.sh.j2

JENKINS_TOKEN=$(curl -s -u admin:"$ADMIN_PASS" 'http://11.0.0.2:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)' | sed 's/Jenkins-Crumb://g')
java -jar /home/jenkins/agent.jar -jnlpUrl http://11.0.0.2:8080/computer/agent/jenkins-agent.jnlp -secret "$JENKINS_TOKEN" -workDir "/home/jenkins/agent"
