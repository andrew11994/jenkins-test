pipeline {
    agent any
    environment {
        GITHUB_BASE_URL = 'https://api.github.com'
        SRC_GH_ORG = 'sample11995' // --> GH_USER
        TARGET_BLACKLIST = 'test3'
        //GH_TOKEN = credentials('fccf94be-e58b-4c2c-abfa-1e54d5178934')
    }
    // trigger {
    //     cron('xxxxxx')
    // }
    stages{
	stage ('git_checkout') {
                steps {
                	git 'https://andrew11994:2Kgmutton@github.com/andrew11994/git_labels.git'
        		}
        	}
        stage('execute shell') {
            //when { triggeredBy 'TimerTrigger' }
            steps {
                script {
                  withCredentials([string(credentialsId: 'git', Variable: 'GH_TOKEN')]) {
                  def raw_repos= sh(script: "curl -u ${GH_TOKEN}:x-oauth-basic -s ${env.GITHUB_BASE_URL}/orgs/${env.SRC_GH_ORG}/repos | jq '.[] | .name'")
                  echo "raw_repos = ${raw_repos}"
                  //def target_repos= sh(script: "echo ${raw_repos} | jq -r '.[] | .name'| grep -v ${env.TARGET_BLACKLIST}",returnStdout: true)          
                  for (repo in raw_repos)
                	sh "git_labels.sh ${env.GH_TOKEN} andrew11994 test andrew11994 $repo"    
                    }
                }    
            }
        }
    }
}
