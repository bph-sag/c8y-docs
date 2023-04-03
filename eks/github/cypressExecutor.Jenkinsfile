
pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '50', artifactNumToKeepStr: '15'))
        copyArtifactPermission('/**')
        ansiColor('xterm')
        skipDefaultCheckout(true)
    }

    parameters {
        string(name: 'URL', defaultValue: 'https://<cumulocityDomain>', description: 'URL of the cumulocity instance')
        string(name: 'USERNAME', defaultValue: 'e2edocker')
        string(name: 'PASSWORD', defaultValue: 'e2ePassword123!')
        string(name: 'BRANCH', defaultValue: 'develop', description: 'develop or release/x.y.0')
        string(name: 'ADDITIONAL_ENV_PARAMS', defaultValue: '', description: 'additional environment parameters, e.g. "burn=20,grep=Logout"')
        string(name: 'PROJECT_ID', defaultValue: 'c8y-cypress-tests', description: 'Project ID for sorry-cypress, e.g. "platformTeam"')
        string(name: 'SPEC', defaultValue: '', description: 'pass spec files, e.g. cypress/e2e/administration/alarmMapping.cy.ts')
        choice(name: 'BROWSER', choices: ['chrome','firefox'], description: 'Choose a browser in which tests should be triggered')
    }

    agent {
        kubernetes {
            yaml '''
            apiVersion: v1
            kind: Pod
            metadata:
              labels:
              some-label: some-label-value
            spec:
              containers:
              - name: cypress
                image: "cypress/browsers:node14.19.0-chrome100-ff99-edge"
                command:
                - cat
                resources:
                  limits:
                    cpu: "2"
                    memory: "3Gi"
                  requests:
                    cpu: "2"
                    memory: "2Gi"
                tty: true
            '''
        }
    }

   stages {
        stage('Install') {
            steps {
                retry(3) {
                    container ('cypress') {
                        sh 'yarn install --frozen-lockfile'
                    }
                }
            }
        }
        stage('Test run on E2E tenants') {
            steps {
                container('cypress') {
                    script {
                        def username = params.USERNAME ? params.USERNAME : "e2edocker"
                        def userPassword = params.PASSWORD ? params.PASSWORD : "e2ePassword123!"

                        def e2eParameters = "--e2e --env "
                        if(!ADDITIONAL_ENV_PARAMS.equals("")) {
                            e2eParameters += ADDITIONAL_ENV_PARAMS + ","
                        }
                        e2eParameters += "username=${username},password=${userPassword} --config baseUrl=${params.URL},projectId=${params.PROJECT_ID} "
                        if (!params.BROWSER.equals("")) {
                            e2eParameters += "--browser ${params.BROWSER} "
                        }
                        if(params.SPEC && !SPEC.equals("")) {
                            e2eParameters += "--spec ${params.SPEC} "
                        }
                        def jobName = "${env.JOB_NAME}"

                        def jobBuildNumber
                        if (currentBuild.upstreamBuilds) jobBuildNumber = currentBuild.upstreamBuilds[0].number else jobBuildNumber = "${env.BUILD_NUMBER}"

                        for(upstreamBuild in currentBuild.upstreamBuilds) {
                          jobName = upstreamBuild.projectName
                        }

                        sh "COMMIT_INFO_BRANCH=${params.BRANCH} CYPRESS_API_URL='http://sorry-cypress-director.sorry-cypress.svc.cluster.local:1234' npx cy2 run --record --key jenkins-cypress-tests --parallel --ci-build-id ${params.BRANCH}-${jobName}-${jobBuildNumber} ${e2eParameters}"
                    }
                }
            }
        }
    }
}
