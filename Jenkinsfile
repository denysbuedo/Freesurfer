node{
		
     stage('DATA ACQUISITION') {
		
		//Read new task data
		echo "Reading the task data"
		def tast_xml = readFile "/var/lib/jenkins/workspace/ToolBox_Tasks/Freesurfer/Pending/Task2.xml"
		def parser = new XmlParser().parseText(tast_xml)
		def BUILD_ID ="${parser.attribute("build")}"
		def OWNER ="${parser.attribute("owber_task")}"
		def SUBJECT="${parser.attribute("subject")}"
		def FSF_SUBJECT="${parser.attribute("fsf_output")}"
		
		//Copy de Subject file to SUBJECT_DIR in Freesuerfer Server
		echo "Connecting to freesurfer server to copy subject file"
		sshagent(['id_rsa_fsf']) {      
			def subject_data = new File ("/var/lib/jenkins/workspace/Freesurfer_recon_all/subject_file")  
			sh "scp subject_data root@192.168.17.132:/usr/local/freesurfer/subjects/"
        }
     }
      
     stage('DATA PROCESSING-recon-all') {
	    
	    echo "Connecting to Freesuefer server"
	    
	    sshagent(['id_rsa_fsf']) {        
	    
            sh 'ssh root@192.168.17.132'     
            
        }
                	
     }
      
     stage('DATA STORAGED') {
	      echo "DELIVERY RESULT"	
     }
      
     stage('NOTIFICATION') {
	 	 echo "NOTIFICATION"	   
     }
}
