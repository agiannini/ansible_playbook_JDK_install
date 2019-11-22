// Requires two variables: NODE_ADDRESS (address of node) and ROLES (all available roles)
pipeline {
    parameters{
        string( name:'NODE_ADDRESS',
        defaultValue: '172.17.0.5',
        description:'Please enter the ip address of environment that must be built.'
        )
    }
    agent any

   stages {
      stage('Hello') {
         steps {
            echo 'Hello World'
         }
      }
    stage('SetupFile'){
          steps{
             sh 'echo root@${NODE_ADDRESS} > /etc/ansible/hosts'
             sh 'echo $date root@${NODE_ADDRESS} >> /etc/ansible/host_record'
             sh 'sed -i "4d;$d" /etc/ansible/main.yml'
             sh 'echo "    - ${ROLES}" >> /etc/ansible/main.yml'
          }
         }
    stage('Execute'){
          steps{
             sh 'ansible-playbook /etc/ansible/main.yml'
        }

    }
   }
}
