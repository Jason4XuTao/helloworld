#!groovy 

node {
   stage 'Checkout'
        checkout scm

   stage 'Setup'
        sh '''
            npm cache clean --force
            npm install -g npm@latest
            npm get registry
            npm install --registry=http://registry.npmjs.org/
        '''
//        sh 'npm install'

   stage 'Mocha test'
        sh './node_modules/mocha/bin/mocha'

   stage 'Cleanup'
        echo 'prune and cleanup'
        sh 'npm prune'
        sh 'rm node_modules -rf'
}
