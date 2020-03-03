pipeline {
	agent any
	environment {
		GITHUB_BASE_URL = 'https://api.github.com'
     		SRC_GH_ORG = 'sample11995'
     		TARGET_BLACKLIST = 'test3'
     	//GH_TOKEN = credentials('fccf94be-e58b-4c2c-abfa-1e54d5178934')
     	}
	def getRequiredPackages(DSL steps) {
    		steps.withCredentials([steps.string(credentialsId: 'git', variable: 'GIT_OAUTH_TOKEN')]) {
        	steps.sh(returnStdout: false,
                script: "curl -L " +
                        "-H 'Authorization: token ${GIT_OAUTH_TOKEN}' " +
			 "https://api.github.com/orgs/${env.SRC_GH_ORG} " +
                        "-vvv"
        		)	
    		}
	}
}	
return this
