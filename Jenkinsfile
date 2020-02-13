environment {
        CUSTOMER = 'test'
    }

node {
	stage ('checkout SCM') {
		withCredentials([usernamePassword(credentialsId: 'git', usernameVariable: 'username', passwordVariable: 'password')]){
			checkout scm
		}
	}
	stage ('Edit files') {
		sh "sed -i 's/variable01/${project_name}/g' vpc-network/variables.tf"
		sh "sed -i 's/variable02/${region}/g' vpc-network/variables.tf"
		sh "sed -i 's/variable03/${prefix_name}/g' vpc-network/variables.tf"
		}

	stage ('write back to customer git dir') {
		withCredentials([usernamePassword(credentialsId: 'git_new', usernameVariable: 'username', passwordVariable: 'password')]){
			sh ("mkdir -p vpc")
			sh ("cp -r vpc-network vpc/")
			sh ("git add . && git commit -m 'new terraform files' && git config --global push.default simple && git remote set-url origin https://$username:$password@github.com/saravana1992/test-terraform-new.git && git push origin HEAD:master")
		}
	}
}
