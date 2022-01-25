pipeline {

	agent any
	
	environment {
	    STAGE = ''
	}

	parameters {
		choice(name: 'buildTool', choices: ['gradle', 'maven'], description: 'Indicar herramienta de construcción')
	}

	stages{
		stage('Pipeline'){
			steps{
				script{
					try {
						println 'Pipeline'
						
	                    if (params.buildTool == "gradle") {
	                        def ejecucion = load 'gradle.groovy'
		                    ejecucion.call()
	                    } else {
	                        def ejecucion = load 'maven.groovy'
		                    ejecucion.call()
	                    }

	                    slackSend color: 'good', message: "[Rodrigo Catalán][${env.JOB_NAME}][${params.buildTool}] Ejecución exitosa"

					} catch (Exception e){
					    slackSend color: 'danger', message: "[Rodrigo Catalán][${env.JOB_NAME}][${params.buildTool}] Ejecución fallida en stage ${STAGE}"
					    error "Ejecución fallida en stage ${STAGE}"
					}
				}
			}
		}
	}
}