node {
    stage('Check Python Version') {
        writeFile file: 'test.py', text: '''
print("Hello, World!")
'''
        sh "python3 test.py"

        sh 'python3 -c "print(\\"Hello World!\\")"'
    }
}