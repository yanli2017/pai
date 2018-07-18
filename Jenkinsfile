pipeline {
  agent {
    node {
      label 'pipeline'
    }

  }
  stages {
    stage('Choose Deployment Bed') {
      steps {
        script {
          sh (
            script: '''#!/bin/bash
set -x
IFS=", " read -r -a labels <<< "$NODE_NAME"
#echo ${labels[@]}
echo ${labels[0]} > $WORKSPACE/BED.txt
''',
            returnStdout: true
          )
          env.BED = readFile("$WORKSPACE/BED.txt").trim()

          echo env.BED
          echo 'readFile "$WORKSPACE/BED.txt"'
          echo "Select CI Cluster: ${BED}"
          echo "Select CI Cluster: ${env.BED}"
        }

        sh 'printenv'
        echo "Select CI Cluster: ${BED}"
        echo "Select CI Cluster: ${env.BED}"
        script {
          echo "+++${BED}"
          echo "---${env.BED}"
        }

      }
    }
    stage('Clean dev-box') {
      agent {
        node {
          label 'dev-box'
        }

      }
      steps {
        sh '''#!/bin/bash
set -x
sudo --preserve-env $JENKINS_HOME/scripts/prepare_build_env.sh'''
      }
    }
    stage('Build Images') {
      agent {
        node {
          label 'dev-box'
        }

      }
      steps {
        echo "Select CI Cluster: ${env.BED}"
        script {
          echo "+++${BED}"
          echo "---${env.BED}"
        }

        sh '''#! /bin/bash

set -x

# prepare path
sudo mkdir -p ${JENKINS_HOME}/${BED}/quick-start
sudo mkdir -p ${JENKINS_HOME}/${BED}/cluster-configuration
sudo chown core:core -R $JENKINS_HOME
QUICK_START_PATH=${JENKINS_HOME}/${BED}/quick-start
CONFIG_PATH=${JENKINS_HOME}/${BED}/cluster-configuration
cd pai-management/

# generate quick-start
$JENKINS_HOME/scripts/${BED}-gen_single-box.sh ${QUICK_START_PATH}
# ! fix permission
sudo chown core:core -R /mnt/jenkins/workspace

# generate config
mkdir  $CONFIG_PATH/
ls $CONFIG_PATH/
rm -rf $CONFIG_PATH/*.yaml
./paictl.py cluster generate-configuration -i ${QUICK_START_PATH}/quick-start.yaml -o $CONFIG_PATH
# update image tag
sed -i "46s/.*/    docker-tag: ${GIT_BRANCH/\\//-}-$(git rev-parse --short HEAD)-${BUILD_ID}/" $CONFIG_PATH/services-configuration.yaml
# setup registry
$JENKINS_HOME/scripts/setup_azure_int_registry.sh $CONFIG_PATH

# build images
sudo ./paictl.py image build -p $CONFIG_PATH

# push images
sudo ./paictl.py image push -p $CONFIG_PATH
'''
      }
    }
    stage('Deploy') {
      parallel {
        stage('Install A SingleBox') {
          agent {
            node {
              label 'dev-box'
            }

          }
          steps {
            sh '''#!/bin/bash
set -x

echo "Deploy SingleBox finished!"
'''
          }
        }
        stage('Install Cluster') {
          agent {
            node {
              label 'dev-box'
            }

          }
          steps {
            sh '''#!/bin/bash
set -x

echo "Deploy Cluster finished!"
'''
          }
        }
      }
    }
    stage('Test') {
      parallel {
        stage('Test A SingleBox') {
          agent {
            node {
              label 'dev-box'
            }

          }
          steps {
            script {
              try {
                sh '''#! /bin/bash

#TODO
printenv

set -x
exit -1
'''
              } catch (err) {
                echo "Failed: ${err}"
                currentBuild.result = 'FAILURE'
              }
            }

          }
        }
        stage('Test Cluster') {
          agent {
            node {
              label 'dev-box'
            }

          }
          steps {
            script {
              try {
                sh '''#! /bin/bash

set -x

exit 0
'''
              } catch (err) {
                echo "Failed: ${err}"
                currentBuild.result = 'FAILURE'
              }
            }

          }
        }
      }
    }
    stage('Pause on failure') {
      agent {
        node {
          label 'dev-box'
        }

      }
      steps {
        script {
          if(currentBuild.result == 'FAILURE'){
            // input (
              //   message: 'Test failed! Would you like to clean the deployment now?'
              // )
            }
          }

        }
      }
      stage('Clean Up') {
        parallel {
          stage('Clean up A SingleBox') {
            agent {
              node {
                label 'dev-box'
              }

            }
            steps {
              sh '''#!/bin/bash
set -x

echo "Clean up!"
'''
            }
          }
          stage('Clean up Cluster') {
            agent {
              node {
                label 'dev-box'
              }

            }
            steps {
              sh '''#!/bin/bash
set -x

echo "Clean up!"
'''
            }
          }
        }
      }
    }
    options {
      disableConcurrentBuilds()
    }
  }