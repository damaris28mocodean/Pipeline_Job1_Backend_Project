properties(
    [
        parameters([
            string(defaultValue: 'pet-rest-api-web-0.0.1-SNAPSHOT', name: 'JAR_FILE_NAME', description: ''),
            string(defaultValue: '/var/lib/jenkins/workspace/Pipeline_Job2_Backend/Artifacts', name: 'PATH_TO_ARTIFACTS', description: '')
        ])
    ]
)

node{
    def mvnHome
    stage('Preparation'){
        mvnHome = tool 'maven3.8.6'
    }
    stage('BuildWithMaven'){
         
        dir('source_code'){

            withEnv(["MVN_HOME=$mvnHome"]){
                
                sh'"$MVN_HOME/bin/mvn" clean install -DskipTests'
            }
        }
    }
    stage('StoreArtifact'){
        dir('source_code/pet-rest-api-web/target'){
            
            sh 'mv ${JAR_FILE_NAME}.jar ${PATH_TO_ARTIFACTS}/${JAR_FILE_NAME}-${BUILD_NUMBER}.jar'
        }
    }
}
