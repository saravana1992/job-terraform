node {
	stage 'Checkout'
		checkout scm

	stage 'Edit files'
		sh '' sed -i 's/variable01/project_name/g' vpc-network/variables.tf
		sed -i 's/variable02/region/g' vpc-network/variables.tf
		sed -i 's/variable03/prefix_name/g' vpc-network/variables.tf
		''

}
