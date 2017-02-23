node {
  stage 'Checkout'
  
  checkout scm

  def mvnHome = tool 'M3'
  //env.PATH = "${tool 'M3'}/bin:${env.PATH}"
  
  stage 'Build the JAR'
  
  sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
  //sh "mvn clean package"
  
  sh 'cp target/*.jar /tmp/'
                  
  
  step([$class: 'ArtifactArchiver', artifacts: '**/target/*.jar', fingerprint: true])
  step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])


}
