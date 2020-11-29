#!groovy 

node {
   stage 'Checkout'
        checkout scm

   stage 'Setup'
        sh '''
            sudo npm config set registry http://registry.npmjs.org/  
            sudo npm cache clean --force
            sudo npm install -g npm@latest
            sudo npm get registry
            sudo npm install --registry=http://registry.npmjs.org/
        '''
//        sh 'npm install'

   stage 'Mocha test'
        sh './node_modules/mocha/bin/mocha'

   stage 'Cleanup'
        echo 'prune and cleanup'
        sh 'npm prune'
        sh 'rm node_modules -rf'
}
