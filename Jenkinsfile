pipeline {
    agent any
    environment {
        GITHUB_BASE_URL = 'https://api.github.com'
        SRC_GH_ORG = 'sample11995' // --> GH_USER
        TARGET_BLACKLIST = 'test3'
        //GH_TOKEN = credentials('gitcred')
    }
    // trigger {
    //     cron('xxxxxx')
    // }
    stages{
        stage('execute shell') {
            //when { triggeredBy 'TimerTrigger' }
            steps {
                script {
                  withCredentials([string(credentialsId: 'git', variable: 'GH_TOKEN')]) {
                  def raw_repos= sh(script: "curl -u ${GH_TOKEN}:x-oauth-basic -s ${env.GITHUB_BASE_URL}/orgs/${env.SRC_GH_ORG}/repos | jq '.[] | .name'")
                  echo "raw_repos = ${raw_repos}"
                  //def target_repos= sh(script: "echo ${raw_repos} | jq -r '.[] | .name'| grep -v ${env.TARGET_BLACKLIST}",returnStdout: true)          
                  //for (repo in target_repos)
                //sh "./github-copy-labels.sh ${GH_TOKEN} Test-labels ${repo}"    
                    }
                }    
            }
        }
    }
}
