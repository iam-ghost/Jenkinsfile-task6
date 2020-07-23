job("Git_Pull") {
  description("This job will pull code from GitHub repository")  
  
  scm {
    github("iam-ghost/task6-deploy", "master") 
  }

  triggers {
      scm("* * * * *")
  }
  steps {
  shell('sh cp -rf * ./ ')
}

job("2 Check And Deploy") {
  description("This job is for deploying web server")
  
  triggers {
    upstream("Git_Pull")
  }

  steps {
    shell(sh conifg.sh)
  }
}

buildPipelineView("K8s Deploy WebApp") {
  title("automating CI/CD pipeline")
  description("This is build pipeline view for task 6")
  selectedJob("Git_Pull")
  alwaysAllowManualTrigger(true)
  refreshFrequency(33)
  displayedBuilds(1)
  showPipelineParameters()
}
