node
{
    stage ('Checkout')
    {
        checkout([$class: 'GitSCM', branches: [[name: '*/dev']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '8dd19141-029a-4892-ab1f-aa24451f5c82', url: 'git@github.com:kinecosystem/kre-compute-engine.git']]])
    }

    stage('Unit Test')
    {
        echo 'Unit tests'
        
    }

    stage ('Build Image')
    {
        echo 'Docker build'
        sh 'docker build -t krejenkins/test:${BUILD_NUMBER} .'
    }

    stage ('Deploy to DockerHub')
    {
        echo 'Pushing to DockerHub'
        sh 'docker push krejenkins/test:${BUILD_NUMBER}'
    }

}
