node {
  stage 'Checkout'
  
  checkout scm

  def mvnHome = tool 'M3'
  //env.PATH = "${tool 'M3'}/bin:${env.PATH}"
  
  stage 'Build the JAR'
  
  sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
  //sh "mvn clean package"
  
  step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])

}
