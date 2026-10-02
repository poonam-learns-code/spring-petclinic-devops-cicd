# 🚀 End-to-End Enterprise Java CI/CD Pipeline

An automated, production-grade DevOps CI/CD pipeline built on AWS EC2 to build, test, analyze, containerize, and deploy the Spring PetClinic Java application.
[GitHub (Source)] ➡️ [Jenkins (CI/CD)] ➡️ [SonarQube (Static Analysis)]
                            ⬇️
                     [Maven (Package)]
                            ⬇️
                     [Docker (Build)]
                            ⬇️
               [AWS EC2 Deployment (Port 8081)]
    ```                                                                                                              
                                                                                                                   
  * **Checkout Code:** Jenkins triggers automated checkout from the official Spring PetClinic repository.         
  * **Code Quality Analysis:** Executes SonarQube Scanner to detect vulnerabilities and enforce Quality Gate.      
  * **Build & Package:** Maven compiles the source code and packages it into an executable JAR.                  
  * **Containerization:** Generates a lightweight runtime Dockerfile and builds a Docker image.                    
  * **Continuous Deployment:** Safely deploys the container on EC2 port 8081.                                      
                                                                                                                   
 ---
 ## 🛠️ Tech Stack & Tools                                                                                        
                                                                                                                   
  * **Cloud Provider:** AWS (EC2 Ubuntu Instance)                                                                  
  * **CI/CD Orchestration:** Jenkins                                                                               
  * **Code Quality & Security:** SonarQube Server                                                                 
  * **Build Automation:** Apache Maven 3.x                                                                         
 * **Language & Framework:** Java 17, Spring Boot                                                                 
 * **Containerization:** Docker                                                                                   
                                                                                                                   
     ---
   ## 📊 Pipeline Stages Status                                                                                     
                                                                                                                   
  | Stage | Tool | Status |                                                                                         
  | :--- | :--- | :--- |                                                                                             
  | Checkout Code | Git | ✅ Passed |                                                                               
  | SonarQube Code Analysis | SonarQube Scanner | ✅ Passed (Quality Gate Passed) |                                
  | Package Application | Apache Maven | ✅ Passed |                                                               
  | Docker Build & Package | Docker Engine | ✅ Passed |                                                             
  | Deploy Application | Docker Container | ✅ Passed (Port 8081) 
