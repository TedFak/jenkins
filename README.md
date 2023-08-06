# jenkins
Jenkins with agent
# Agent
INFO: Both error and output logs will be printed to /home/jenkins/agent/remoting
Failed to obtain http://11.0.0.2:8080/computer/agent/jenkins-agent.jnlp?encrypt=true
java.io.IOException: Failed to load http://11.0.0.2:8080/computer/agent/jenkins-agent.jnlp?encrypt=true: 404 Not Found
        at hudson.remoting.Launcher.parseJnlpArguments(Launcher.java:514)
        at hudson.remoting.Launcher.run(Launcher.java:346)
        at hudson.remoting.Launcher.main(Launcher.java:297)
Waiting 10 seconds before retry
# Host
java -jar /home/admin/test/jenkins-cli.jar -ssh -user admin -s http://11.0.0.2:8080/ create-node agent1 -v
Aug 06, 2023 10:09:12 PM io.jenkins.cli.shaded.org.apache.sshd.common.util.security.AbstractSecurityProviderRegistrar getOrCreateProvider
INFO: getOrCreateProvider(EdDSA) created instance of io.jenkins.cli.shaded.net.i2p.crypto.eddsa.EdDSASecurityProvider
Aug 06, 2023 10:09:13 PM io.jenkins.cli.shaded.org.apache.sshd.common.io.DefaultIoServiceFactoryFactory getIoServiceProvider
INFO: No detected/configured IoServiceFactoryFactory; using Nio2ServiceFactoryFactory
io.jenkins.cli.shaded.org.apache.sshd.common.SshException: No more authentication methods available

WARNING: verifyServerKey(ClientSessionImpl[admin@/11.0.0.2:36645]) Could not reload known hosts file /root/.ssh/known_hosts
java.io.StreamCorruptedException: Failed (IllegalArgumentException) to parse line #2 '/root/.ssh/rsa_key.pub': Missing host patterns end delimiter in line=/root/.ssh/rsa_key.pub

https://github.com/TedFak/jenkins/blob/master/ansible/roles/deploy/templates/script.sh.j2
```bash
JENKINS_TOKEN=$(curl -s -u admin:"$ADMIN_PASS" 'http://11.0.0.2:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)' | sed 's/Jenkins-Crumb://g')
java -jar /home/jenkins/agent.jar -jnlpUrl http://11.0.0.2:8080/computer/agent/jenkins-agent.jnlp -secret "$JENKINS_TOKEN" -workDir "/home/jenkins/agent"
```
