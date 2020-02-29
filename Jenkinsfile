pipeline {
    agent any
    environment {
        GITHUB_BASE_URL = 'https://github.impcloud.net/api/v3'
        SRC_GH_ORG = 'edgexfoundry' // --> GH_USER
        TARGET_BLACKLIST = 'sample-service'
        GH_TOKEN = credentials('githubcred'), GH_TOKEN_PWD
    }
    // trigger {
    //     cron('xxxxxx')
    // }
    stages {
        stage('execute shell') {
            //when { triggeredBy 'TimerTrigger' }
            steps {
                GITHUB_BASE_URL=${GITHUB_BASE_URL:-https://api.github.com}
                raw_repos=$(curl -u $GH_TOKEN:x-oauth-basic -s $GITHUB_BASE_URL/orgs/$SRC_GH_ORG/repos\?per_page\=200)
                target_repos=$(echo $raw_repos | jq -r '.[] | .name' | grep -v sample-service)
                for repo in "$target_repos"; do
                done
                sh "./github-copy-labels.sh edgex-template-repo"
            }
        }
    }
}
