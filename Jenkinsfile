pipeline {

	parameters {
		string(name: 'BUILD_NUMBER', defaultValue: '', description: 'Build Number', trim: true)
		string(name: 'RELEASE_NUMBER', defaultValue: '', description: 'Release Number', trim: true)
		string(name: 'ENVIRNOMENT', defaultValue: '', description: 'Envirnoment Name', trim: true)
		string(name: 'NUMBER_ONE', defaultValue: '80', description: 'Number one', trim: true)
		string(name: 'NUMBER_TWO', defaultValue: '40', description: 'Number Two', trim: true)
		booleanParam(name: 'STATUS', defaultValue: true, description: 'Status')

	}

	options {
		timestamps()
	}

	agent any

	environment {
		EMAIL = "animeshranjan024@gmail.com"
		MOBILE_NUM = "7322027026"
	}

	stages {

		stage("update run name"){
			steps {
				script {
					currentBuild.displayName = "${params.RELEASE_NUMBER}:${params.BUILD_NUMBER}_${params.ENVIRNOMENT}"
				}
			}
		}

		stage("checkout code"){
			steps {
				script {
					echo 'checkout the code.'
				}
			}
		}

		stage("prep phase"){
			when {
				equals expected: 'SUCCESS', actual: currentBuild.currentResult
			}

			parallel {

				stage("add"){
					steps {
						script {
							def num1 = "${params.NUMBER_ONE}".toInteger()
							def num2 = "${params.NUMBER_TWO}".toInteger()
							def sum = num1 + num2
							echo "Sum of $num1 and $num2 is $sum"
						}
					}
				}

				stage("subtract") {
					steps {
						script {
							def num1 = "${params.NUMBER_ONE}".toInteger()
							def num2 = "${params.NUMBER_TWO}".toInteger()
							def sub = num1 - num2
							echo "subtract from $num1 and $num2 is $sub"
						}
					}
				}
			}
		}

		stage("post phase")
		{
			when {
				equals expected: 'SUCCESS', actual: currentBuild.currentResult
			}

			parallel {
				stage("multiplication"){
					steps {
						script {
							def num1 = "${params.NUMBER_ONE}".toInteger()
							def num2 = "${params.NUMBER_TWO}".toInteger()
							def mult = num1 * num2
							echo "Multiplication of $num1 and $num2 is $mult"
						}
					}
				}

				stage("Modulus Division"){
					steps {
						script{
							def num1 = "${params.NUMBER_ONE}".toInteger()
							def num2 = "${params.NUMBER_TWO}".toInteger()
							if(num2 != 0) {
								def mod = num1 % num2
								echo "Modulus Division of $num1 and $num2 is $mod"
							}
							else {
								echo "Modulus Division not possible"
							}
						}
					}
				}

				stage("Division"){
					steps {
						script{
							def num1 = "${params.NUMBER_ONE}".toInteger()
							def num2 = "${params.NUMBER_TWO}".toInteger()
							if(num2 != 0) {
								def div = num1 / num2
								echo "Division of $num1 and $num2 is $div"
							}
							else {
								echo "Division not possible"
							}
						}
					}
				}
			}
		}
	}
	post {
		always {
			sleep 5
		}
	}
}