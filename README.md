# Deploy-React-Redux-App-to-Azure-App-Service-using-Azure-Pipelines

Prerequisites :
- An Azure account with an active subscription. <a href="https://azure.microsoft.com/en-us/free/?WT.mc_id=A261C142F" target="_blank">Create an account for free.</a> 
- An Azure DevOps organization. <a href="https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/pipelines-sign-up?view=azure-devops" target="_blank">Create an account for free.</a> 

# Project Task and Steps:
1- Create a Azure Container Registry >>> <a href="https://github.com/hkaanturgut/azure-devops-apps/tree/main/terraspace%20codes/app/stacks/acr" target="_blank">ACR Terraspace Codes</a> 

![Screenshot 2023-02-05 at 8 52 24 AM](https://user-images.githubusercontent.com/113396342/217688610-006dc446-8ecf-4a3d-b15f-f154b2cf40b5.png)

#

2- Create a Azure DevOps Project 

![Screenshot 2023-02-09 at 6 39 14 PM](https://user-images.githubusercontent.com/113396342/218094325-34e10cc1-1c29-44ef-aae6-eb4e897980a2.png)

#

3- Create new service connection to make a connection between ACR-AzureDevOps and Github-AzureDevOps
   
   - Project Settings > Service Connections > Create service connection 

![Screenshot 2023-02-09 at 6 41 18 PM](https://user-images.githubusercontent.com/113396342/218096222-0777ce26-895c-414d-bebd-beb9f2108a86.png)

![Screenshot 2023-02-05 at 8 58 37 AM](https://user-images.githubusercontent.com/113396342/217633906-991d0dc1-4bd3-4c3b-8d25-0ad1460d7c16.png)

#

4- Create a new Pipeline 

![Screenshot 2023-02-09 at 6 42 27 PM](https://user-images.githubusercontent.com/113396342/218094460-627632b9-821d-4e82-8538-755e55b80da9.png)

#

5-  Walk through the steps of the wizard by first selecting GitHub as the location of your source code. 

![Screenshot 2023-02-09 at 6 42 35 PM](https://user-images.githubusercontent.com/113396342/218094501-17d4e346-e943-4376-bb40-eed21632e6b5.png)

#
6- When the list of repositories appears, select your repository. 

![Screenshot 2023-02-09 at 6 42 54 PM](https://user-images.githubusercontent.com/113396342/218094644-0d3ef104-d07d-41ba-a2c7-53dee72b2e9f.png)

#

7- When the Configure tab appears, select Docker build and push an image to ACR.

![image](https://user-images.githubusercontent.com/113396342/218094689-81d171e6-19ba-4e82-a00e-cb20d16d08fa.png)
#

8- Pipeline has been created 

![Screenshot 2023-02-09 at 6 48 36 PM](https://user-images.githubusercontent.com/113396342/218094731-cb80ff0a-7cf8-44c7-ab35-ec916df26fb8.png)
#


9- Build and Push job has been done.

![Screenshot 2023-02-09 at 6 51 32 PM](https://user-images.githubusercontent.com/113396342/218094769-d92265a4-a7e7-404c-93de-31823b6bdade.png)

    - Image has been deployed to ACR

![Screenshot 2023-02-09 at 6 51 55 PM](https://user-images.githubusercontent.com/113396342/218094825-97c39b38-d43d-4fad-961a-00c0b173af03.png)

#

# RELEASE TO AZURE WEB APPS

- Create a Azure Linux Web App for Containers >>> <a href="https://github.com/hkaanturgut/DEPLOY-5-WEBAPPS-TO-AZURE-APP-SERVICE-USING-AZURE-DEVOPS-PIPELINES/tree/main/terraspace%20codes/app/stacks/react-redux_linux_webapp" target="_blank">App Service Terraspace Codes</a> 

![Screenshot 2023-02-09 at 6 56 09 PM](https://user-images.githubusercontent.com/113396342/218094989-c362a6c4-9d2f-4cb9-b692-03b3e8e1f2d8.png)
#

1- Create a Release Pipeline from the Release tab of the Pipeline

![Screenshot 2023-02-09 at 6 56 22 PM](https://user-images.githubusercontent.com/113396342/218095126-b49f18fc-2d32-4704-934b-316836411a2a.png)

#

2- Select Azure App Service deployment

![Screenshot 2023-02-05 at 9 24 59 AM](https://user-images.githubusercontent.com/113396342/217689291-709b0b52-0965-41c0-ac6c-86b159c9e55b.png)
#

3- Add the artifact 

![Screenshot 2023-02-09 at 6 57 00 PM](https://user-images.githubusercontent.com/113396342/218095182-ccae466c-251e-42ab-9854-7473b6d50ebd.png)


    - Do not forget to enable continuous deployment trigger
    
![Screenshot 2023-02-09 at 6 57 15 PM](https://user-images.githubusercontent.com/113396342/218095301-2998409c-9efb-4c8f-bdd0-b6f71f96b350.png) 
#

4- Make the configurations of the stage 
   
    - Save and click on Create release
    
![Screenshot 2023-02-09 at 6 58 06 PM](https://user-images.githubusercontent.com/113396342/218095590-14435bf4-26ce-4073-9d06-86ee967c92e5.png)

![Screenshot 2023-02-09 at 6 58 23 PM](https://user-images.githubusercontent.com/113396342/218095612-8dedb713-1f58-4543-8396-8da8d9d3b2fe.png)
#

- Release pipeline is succesfull

![Screenshot 2023-02-09 at 7 00 57 PM](https://user-images.githubusercontent.com/113396342/218095706-869ea307-97e6-4311-acf1-f4943b7c7638.png)

#

- Logs of the stage can be viewed from logs tab

![Screenshot 2023-02-09 at 7 01 13 PM](https://user-images.githubusercontent.com/113396342/218095744-b1ba742f-0e65-4702-8420-4540eaa2447d.png)

#


## Add the website expose port from the Azure Portal otherwise website will not work
   
   App Service > Configuration > Application Settings > New application setting > 
   
   ![Screenshot 2023-02-09 at 7 01 45 PM](https://user-images.githubusercontent.com/113396342/218096900-4851e758-d2a7-4c03-a361-480c5a02e254.png)

   Add the exposing port that is on the Dockerfile ( this port is just for example )
   
   ![Screenshot 2023-02-09 at 7 02 06 PM](https://user-images.githubusercontent.com/113396342/218097051-68ad3708-9d14-49b8-8815-70d20ec1cd76.png)
#

# Here is the working website throug Azure Web App

![Screenshot 2023-02-09 at 7 08 03 PM](https://user-images.githubusercontent.com/113396342/218095796-75e302bc-654e-4215-8757-05ee5aa77059.png)
#

# TROUBLESHOOTING

- If you are getting this port error , make sure you add the website port setting > <a href="https://github.com/hkaanturgut/DEPLOY-5-WEBAPPS-TO-AZURE-APP-SERVICE-USING-AZURE-DEVOPS-PIPELINES#add-the-website-expose-port-from-the-azure-portal-otherwise-website-will-not-work" target="_blank">Solution</a> 

![Screenshot 2023-02-09 at 7 08 23 PM](https://user-images.githubusercontent.com/113396342/218098268-eeb103b1-55e9-4e9d-973b-689b2b53ddab.png)
