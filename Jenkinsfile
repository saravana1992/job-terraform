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
		echo "${CUSTOMER}"
//		sh "mkdir -p customer/'${CUSTOMER}'"
//		sh "cp -r vpc-network customer/${customer}"
//		sh "git add customer && git commit -m 'new terraform files' && git push origin master"
		}

}
