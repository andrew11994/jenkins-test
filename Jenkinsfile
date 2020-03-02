node {
	def GITHUB_BASE_URL = "https://api.github.com"
    	def SRC_GH_ORG = "sample11995" 
    	def TARGET_BLACKLIST = "test3"
	stage ('git_checkout') {
                git 'https://andrew11994:2Kgmutton@github.com/andrew11994/git_labels.git'
        }
    stage('execute shell') {
	    withCredentials([string(credentialsId: 'fccf94be-e58b-4c2c-abfa-1e54d5178934', variable: 'GH_TOKEN')]) {
                sh '''
		    echo $GH_TOKEN
                    raw_repos=$(curl -u ${GH_TOKEN}:x-oauth-basic -s ${GITHUB_BASE_URL}/orgs/${SRC_GH_ORG}/repos | jq '.[] | .name')
		    echo ${raw_repos}
                    target_repos=$(echo ${raw_repos} | jq -r '.[] | .name' | grep -v ${TARGET_BLACKLIST})
                    for repo in "${target_repos}"; do
                        bash git_labels.sh ${GH_TOKEN} andrew11994 test andrew11994 $repo
                    done
                '''
	    }
        }
}
