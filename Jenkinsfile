pipeline {
    agent any
        stages {
            stage('Parameters'){
                steps {
                    script {
                    properties([
                            parameters([
                                [$class: 'ChoiceParameter', 
                                    choiceType: 'PT_SINGLE_SELECT', 
                                    description: 'Select the Environemnt from the Dropdown List', 
                                    filterLength: 1, 
                                    filterable: false, 
                                    name: 'Env', 
                                    script: [
                                        $class: 'GroovyScript', 
                                        fallbackScript: [
                                            classpath: [], 
                                            sandbox: false, 
                                            script: 
                                                "return['Could not get The environemnts']"
                                        ], 
                                        script: [
                                            classpath: [], 
                                            sandbox: false, 
                                            script: 
                                                "return['dev','stage','prod']"
                                        ]
                                    ]
                                ],
                                [$class: 'CascadeChoiceParameter', 
                                    choiceType: 'PT_SINGLE_SELECT', 
                                    description: 'Select the ECS CLUSTER',
                                    name: 'CLUSTER', 
                                    referencedParameters: 'Env', 
                                    script: 
                                        [$class: 'GroovyScript', 
                                        fallbackScript: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: "return['Could not get Environment from Env Param']"
                                                ], 
                                        script: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: '''
                                                if (Env.equals("dev")){
                                                    return["CLUSTER-PAY-DEV"]
                                                }
                                                else if(Env.equals("stage")){
                                                     return["CLUSTER-PAY-UAT"]
                                                }
                                                else if(Env.equals("prod")){
                                                     return["CLUSTER-PAY-PROD"]
                                                }
                                                '''
                                            ] 
                                    ]
                                ],
                                [$class: 'CascadeChoiceParameter', 
                                    choiceType: 'PT_SINGLE_SELECT', 
                                    description: 'Select the Task Defination',
                                    name: 'Task_Defination', 
                                    referencedParameters: 'Env', 
                                    script: 
                                        [$class: 'GroovyScript', 
                                        fallbackScript: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: "return['Could not get Environment from Env Param']"
                                                ], 
                                        script: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: '''
                                                if (Env.equals("dev")){
                                                    return["TASK-PAY-DEV"]
                                                }
                                                else if(Env.equals("stage")){
                                                     return["TASK-PAY-UAT"]
                                                }
                                                else if(Env.equals("prod")){
                                                     return["TASK-PAY-PROD"]
                                                }
                                                '''
                                            ] 
                                    ]
                                ],
                                [$class: 'CascadeChoiceParameter', 
                                    choiceType: 'PT_SINGLE_SELECT', 
                                    description: 'Select the ECS SERVICE ',
                                    name: 'SERVICE_NAME', 
                                    referencedParameters: 'Env', 
                                    script: 
                                        [$class: 'GroovyScript', 
                                        fallbackScript: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: "return['Could not get Environment from Env Param']"
                                                ], 
                                        script: [
                                                classpath: [], 
                                                sandbox: false, 
                                                script: '''
                                                if (Env.equals("dev")){
                                                    return["SEV-PAY-DEV"]
                                                }
                                                else if(Env.equals("stage")){
                                                     return["SEV-PAY-UAT"]
                                                }
                                                else if(Env.equals("prod")){
                                                     return["SEV-PAY-PROD"]
                                                }
                                                '''
                                            ] 
                                    ]
                                ]
                                
                            ])
                        ])
                    }
                }
            }
        }   
}
