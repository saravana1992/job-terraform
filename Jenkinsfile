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
		sh "mkdir ${customer}"
		sh "cp -r vpc-network customer/${customer}"
		sh "git add customer && git commit -m 'new terraform files for ${customer}' && git push origin master"
		}

}
