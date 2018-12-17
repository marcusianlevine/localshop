@Library('OpenSlateProd')_  // https://github.com/openslate/jenkins-shared-library

def deployWhen = {
    env.GIT_BRANCH == 'master' || env.GIT_BRANCH == 'develop'
}

def getDeployEnv = {
    if (env.GIT_BRANCH == 'develop') {
        return 'dev'
    }
    else if (env.GIT_BRANCH == 'master') {
        return 'prod'
    }
    else {
        return 'unknown'
    }
}

def customDeployFunction = {
    cfDeployRancher()
}

openslatePipeline {
    mentions = '<@marcusian>'
    build = false
    publish = deployWhen
    deploy = deployWhen
    deployEnv = getDeployEnv
    deployFunction = customDeployFunction
}
