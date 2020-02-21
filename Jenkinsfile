ansiColor('xterm') {
	node {

		try {
		    def Git_Scm_Url = "https://shubh11994:2Kgmutton@github.com/shubh11994/gitlabels.git"
			def GH_TOKEN = "4271c2f9462c0a26af8486a6ff3d54b23b2d1d0b"
			def SRC_GH_USER = "shubh11994"
			def SRC_GH_REPO = "Automation-of-cloudera-installation"
			def TGT_GH_USER = "shubh11994"
			def TGT_GH_REPO = "TIG-ECS-Terraform"

				stage('Checkout SCM') {
					checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, userRemoteConfigs: [[url: "${Git_Scm_Url}"]]])
				}

        		stage('Creating Docker Image') {
        			sh """bash git_labels.sh $GH_TOKEN $SRC_GH_USER $SRC_GH_REPO $TGT_GH_USER $TGT_GH_REPO"""
        		}
		}
		catch (exc) {
			echo 'I failed'
		}
		finally {
			cleanWs()
		}
	}
}
