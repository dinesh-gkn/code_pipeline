pipeline {
  agent any
  stages {
    stage('aft_start') {
      steps {
        echo 'starting CI for aft'
      }
    }
    stage('aft_checkout') {
      steps {
        echo 'checkout aft from evo git'
      }
    }
    stage('build_aft_run_gtest') {
      steps {
        echo 'bulding aft and run gtest'
      }
    }
    stage('sandbox_publish_aft') {
      steps {
        echo 'Publishing AFT'
      }
    }
    stage('trigger_ZX') {
      steps {
        parallel(
          "trigger_ZX_Pipeline": {
            echo 'trigger EVO ZX'
            
          },
          "trigger ZT Pipeline": {
            echo 'Trigger JUNOS ZT ( Formula 1)'
            echo 'Checkout Junos PVT Branch'
            echo 'Build Junos with AFT PKG'
            echo 'Run ZT Sanity'
            
          },
          "Trigger_ZH_PIpeline": {
            echo 'Trigger ARGUS ZH'
            
          }
        )
      }
    }
    stage('volume_publish_aft') {
      steps {
        echo 'publish AFT after validation'
      }
    }
  }
}