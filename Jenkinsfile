node {
    def GITHUB_BASE_URL = "https://api.github.com"
    def SRC_GH_ORG = "sample11995" // --> GH_USER
    def TARGET_BLACKLIST = "test3"
    def GH_TOKEN = credentials('fccf94be-e58b-4c2c-abfa-1e54d5178934')
    stage ('git_checkout') {
                git 'https://andrew11994:2Kgmutton@github.com/andrew11994/git_labels.git'
        }
    stage('execute shell') {
	    withCredentials([text(credentialsId: 'fccf94be-e58b-4c2c-abfa-1e54d5178934', variable: GH_TOKEN)]) {
                sh '''
                    raw_repos=$(curl -u ${GH_TOKEN}:x-oauth-basic -s ${GITHUB_BASE_URL}/orgs/${SRC_GH_ORG}/repos)
                    target_repos=$(echo $raw_repos | jq -r '.[] | .name' | grep -v ${TARGET_BLACKLIST})
                    for repo in "$target_repos"; do
                        bash git_labels.sh ${GH_TOKEN} andrew11994 test andrew11994 $repo
                    done
                '''
	    }
        }
}
