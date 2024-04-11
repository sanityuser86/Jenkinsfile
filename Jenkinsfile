#!groovy
// pipeline config

def environment = "test"
def machineName = "dev1"

// pipeline
node(build) {
properties([
        [$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator',daysToKeepStr: '1', numToKeepStr: '4']],
        parameters([            
            choice(
                choices: ["test","production"].join("\n"),
                defaultValue: 'test',
                description: 'Env for Index deployment',
                name: 'environment'
            )
        ])
    ])
    
    try{
        stage('Collect info') {
                checkout scm
        }
        stage('Creating Indexes'){
        
            environment=params.environment
            if(environment=="production"){
                machineName = "prod1"
            }   
            
            myVar.createIndexes environment: environment, 
                    deployToMachine: machineName        

        }

    } catch (e){
            pcSlack.notify channel:"ksr", message: "${environment}"+" Couchbase index creation failed : + {e}"
            currentBuild.result = 'FAILURE' 
    }   
}
