stage 'Build'
node {
    bat 'echo "building..."'
    bat 'sleep 5'
}
  
stage 'Test in Parallel'
parallel "quality scan": {
    node {
        bat 'echo "quality scan..."'
        bat 'sleep 10'
    }
}, "integration test": {
    node {
        bat 'echo "integration test..."'
        bat 'sleep 10'
    }
}, failFast: true

stage 'Stage'
input message: 'Proceed to staging?'
node {
    bat 'echo "deploy to staging..."'
}

stage 'Production'
input 'Proceed to production?'
node {
    bat 'echo "deploy to production..."'
}
