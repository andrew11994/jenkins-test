pipeline {
    agent any
    environment {
        GITHUB_BASE_URL = 'https://api.github.com'
        SRC_GH_ORG = 'sample11995' // --> GH_USER
        TARGET_BLACKLIST = 'test3'
        GH_TOKEN = credentials('fccf94be-e58b-4c2c-abfa-1e54d5178934'), GH_TOKEN_PWD
    }
    // trigger {
    //     cron('xxxxxx')
    // }
    stages {
        stage ('git_checkout') {
            steps {
                git 'https://andrew11994:2Kgmutton@github.com/andrew11994/git_labels.git'
            }
        }
        stage('execute shell') {
            //when { triggeredBy 'TimerTrigger' }
            steps {
                sh '''
                raw_repos=$(curl -u $GH_TOKEN:x-oauth-basic -s $GITHUB_BASE_URL/orgs/$SRC_GH_ORG/repos\?per_page\=200)
                target_repos=$(echo $raw_repos | jq -r '.[] | .name' | grep -v $TARGET_BLACKLIST)
                for repo in "$target_repos"; do
                sh "bash git_labels.sh $GH_TOKEN andrew11994 test andrew11994 $repo"
                done
                '''
            }
        }
    }
}
