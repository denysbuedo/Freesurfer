node{
		
     stage('DATA ACQUISITION') {
	      
	      echo "DATA ACQUISITION"
	      
	      def tast_xml = readFile "/var/lib/jenkins/workspace/ToolBox_Tasks/Freesurfer/Pending/Task2.xml"
   		  
   		  if (fileExists (tast_xml)){
	      	def parser = new XmlParser().parseText(xml)
            def BUILD_ID ="${parser.attribute("build")}"
            def OWNER ="${parser.attribute("owner")}"
            def SUBJECT="${parser.attribute("subject")}"
            def FSF_SUBJECT="${parser.attribute("fsf_output")}"
	      }
	      
	      else {
	      	error("${task} still missing. Will now fail the job.")
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
