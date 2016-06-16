stage 'Build'
node('Windows7JNLPSlave32bit') {
    bat 'echo "building..."'
    bat 'timeout 5'
}
  
stage 'Test in Parallel'
parallel "quality scan": {
    node('Windows7JNLPSlave32bit') {
        bat 'echo "quality scan..."'
        bat 'timeout 10'
    }
}, "integration test": {
    node('Windows7JNLPSlave32bit') {
        bat 'echo "integration test..."'
        bat 'timeout 10'
    }
}, failFast: true

stage 'Stage'
input message: 'Proceed to staging?'
node('Windows7JNLPSlave32bit') {
    bat 'echo "deploy to staging..."'
}

stage 'Production'
input 'Proceed to production?'
node('Windows7JNLPSlave32bit') {
    bat 'echo "deploy to production..."'
}
