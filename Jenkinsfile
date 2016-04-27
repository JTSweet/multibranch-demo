stage 'Build'
node {
    sh 'echo "building..."'
    sh 'sleep 5'
}

try {
    checkpoint 'Done Building'
} catch (Exception e) {
    echo "Checkpoint only available in Jenkins Enterprise"
}
  
stage 'Test in Parallel'
parallel "quality scan": {
    node {
        sh 'echo "quality scan..."'
        sh 'sleep 10'
    }
}, "integration test": {
    node {
        sh 'echo "integration test..."'
        sh 'sleep 10'
    }
}, failFast: true

try {
    checkpoint 'Done Building'
} catch (Exception e) {
    echo "Checkpoint only available in Jenkins Enterprise"
}

stage 'Stage'
input message: 'Proceed to staging?'
node {
    sh 'echo "deploy to staging..."'
}
  
try {
    checkpoint 'Done Building'
} catch (Exception e) {
    echo "Checkpoint only available in Jenkins Enterprise"
}

stage 'Production'
input 'Proceed to production?'
node {
    sh 'echo "deploy to production..."'
}
