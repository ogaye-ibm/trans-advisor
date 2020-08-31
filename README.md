# CP4A Transformation Advisor (TA)

WORK IN PROGRESS
# Basic Docker commands:

docker stop twas-plantsbywebsphere

docker rm twas-plantsbywebsphere

docker logs -f twas-plantsbywebsphere

# Scan the existing application
    -Build the Docker image
        docker build -t twas-plantsbywebsphere .

    -Verify Image
        docker images | grep websphere

    - Start an instance of the Docker image
        docker run -d -p 9080:9080 -p 9043:9043 -v "$(pwd)":/data --name twas-plantsbywebsphere twas-plantsbywebsphere:latest
        
# Run the Data Collector
    - Enter the twas-plantsbywebsphere Docker container
       docker exec -it twas-plantsbywebsphere bash
       
    - Navigate to the data collector directory
       cd /demo/transformationadvisor-2.1.1
       
    - Execute the data collector
      ./bin/transformationadvisor -w /opt/IBM/WebSphere/AppServer -p AppSrv01 wsadmin passw0rd
      
    - Verify that the results zip file has been created
         ls -la AppSrv01.zip
         -rw-r--r-- 1 was was 340860 Nov 22 15:32 AppSrv01.zip
    - Use CTRL+D to exit from the Docker container
    - Copy the AppSrv01.zip file from within the Docker container to your local 
        docker cp twas-plantsbywebsphere:/demo/transformationadvisor-2.0.1/AppSrv01.zip .
    - Stop and remove the Docker container
    
# Analyze the scan results
    -Use the Developer Dashboard to open the Transformation Advisor dashboard
    -Add a new workspace named AppMod-{initials}
    -Add a new collection named Lab1
    -Click Upload data and specify the AppSrv01.zip
# Migrate to WebSphere Liberty
    - Enter the twas-plantsbywebsphere Docker container
       docker exec -it twas-plantsbywebsphere bash
    - Navigate to the data collector directory
       cd /demo/transformationadvisor-2.0.1
    - Execute the data collector
      ./bin/transformationadvisor -w /opt/IBM/WebSphere/AppServer -p AppSrv01 wsadmin passw0rd
    - Verify that the results zip file has been created
         ls -la AppSrv01.zip
         -rw-r--r-- 1 was was 340860 Nov 22 15:32 AppSrv01.zip
        Use CTRL+D to exit from the Docker container
    - Copy the AppSrv01.zip file from within the Docker container to your local disk
        docker cp twas-plantsbywebsphere:/demo/transformationadvisor-2.0.1/AppSrv01.zip .

    - Stop and remove the Docker container
# Run the application on Liberty


