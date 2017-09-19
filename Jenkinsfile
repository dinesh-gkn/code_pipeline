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
    stage('aft_bulld_gtest') {
      steps {
        echo 'bulding aft and run gtest'
      }
    }
    stage('aft_local_publish') {
      steps {
        echo 'Publishing AFT'
      }
    }
    stage('trigger_Z_pipelines') {
      steps {
        parallel(
          "trigger_ZX_Pipeline": {
            echo 'trigger EVO ZX'
            
          },
          "trigger_ZT_Pipeline": {
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
    stage('aft_volume_publish') {
      steps {
        echo 'publish AFT after validation'
      }
    }
  }
}