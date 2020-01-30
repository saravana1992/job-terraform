environment {
        CUSTOMER = 'test'
    }

node {
	stage ('checkout SCM') {
		checkout scm
	}
	stage ('Edit files') {
		sh "sed -i 's/variable01/${project_name}/g' vpc-network/variables.tf"
		sh "sed -i 's/variable02/${region}/g' vpc-network/variables.tf"
		sh "sed -i 's/variable03/${prefix_name}/g' vpc-network/variables.tf"
		}

	stage ('write back to customer git dir') {
		withCredentials([usernamePassword(credentialsId: 'git', usernameVariable: 'username', passwordVariable: 'password')]){
			//		echo "${CUSTOMER}"
			//		sh "mkdir -p customer/'${CUSTOMER}'"
			sh "cp -r vpc-network customer/techolution"
			sh "git config --global push.default simple"
			sh ("git add customer && git commit -m 'new terraform files' &&  git push https://$username:$password@github.com/saravana1992/job-terraform.git")
		}
	}
}
