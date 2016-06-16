stage 'Build'
node('Windows7JNLPSlave32bit') {
    bat 'echo "building..."'
    
}
  
stage 'Test in Parallel'
parallel "quality scan": {
    node('Windows7JNLPSlave32bit') {
        bat 'echo "quality scan..."'
        
    }
}, "integration test": {
    node('Windows7JNLPSlave32bit') {
        bat 'echo "integration test..."'
        
    }
}, failFast: true

stage 'Stage'
node('Windows7JNLPSlave32bit') {
    bat 'echo "deploy to staging..."'
}

stage 'Production'
node('Windows7JNLPSlave32bit') {
    bat 'echo "deploy to production..."'
}
