properties([
    parameters([
        [$class: 'ChoiceParameter',
            choiceType: 'PT_SINGLE_SELECT',
            description: 'Select the OpenShift Release',
            filterLength: 1,
            filterable: false,
            name: 'Release',
            script: [
                $class: 'GroovyScript',
                fallbackScript: [
                    classpath: [],
                    sandbox: false,
                    script:
                        'return[\'Could not get Env\']'
                ],
                script: [
                    classpath: [],
                    sandbox: false,
                    script:
                        'return["4.6:selected", "4.7", "4.8","4.9","4.10"]'
                ]
            ]
        ]

    ])
])

pipeline {
    agent any
	
    parameters {
        string(defaultValue: 'default', description: 'Build(quay image or build number)', name: 'Build')
        string(defaultValue: '0', description: 'Enter time(in Minutes) to retain the cluster', name: 'KeepFor')
    }
     environment {
	
	      //Parameters
        OCP_RELEASE="${params.Release}"
        CONFIG_TYPE="min"
        BUILD="${params.Build}"
        TIMEOUT = "${params.KeepFor}"
        ENABLE_E2E_TEST="true"
     
     }
    stages {
        stage('Read') {
            steps {
                script {
                    echo "OCP_RELEASE: ${OCP_RELEASE}"
                    echo "CONFIG_TYPE: ${CONFIG_TYPE}"
                    echo "BUILD: ${BUILD}"
                    echo "TIMEOUT: ${TIMEOUT}"
                    sleep "${TIMEOUT}"
			
                }            
            }
        }

    
    }
}
