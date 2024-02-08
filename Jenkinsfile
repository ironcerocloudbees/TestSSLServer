/**
  Workfow to download and execute a SSL Test connexion
  @author kuisatahverat
  Test
  Test2
  Test3
  Test4
  Test5
  Test6
  Test7
  Test8
  Test9
  Test10
  Test11
  Test12
  Test13
  Test14
  Test15
 **/
env.targetHost = targetHost
env.JAVA_HOME = jdkHomePath
node () {
  stage ('Env'){
    sh 'export'
  }
  stage ('Download sources'){
    tool name: 'Default', type: 'hudson.plugins.git.GitTool'
    git 'https://github.com/ironcerocloudbees/TestSSLServer.git'
    lastChanges()
  }
  stage ('Compile sources'){
    //tool name: 'maven3', type: 'hudson.tasks.Maven$MavenInstallation'
    sh '''
      mvn clean compile
    '''
  }
  stage ('Execute Test SSL support features'){
    sh '''
      mvn -Djavax.net.debug=ssl:handshake -Dexec.mainClass=org.bolet.TestSSLServer -Dexec.args=${targetHost} exec:java
    '''
  }
  stage ('Execute Test SSL handshake'){
    sh '''
      mvn -Djavax.net.debug=ssl:handshake -Dexec.mainClass=org.bolet.TestSSLHandShake -Dexec.args=https://${targetHost} exec:java
    '''
 }
}
