# VotingApplication-using-Serverless-Services

![architecture](https://user-images.githubusercontent.com/91054305/231661171-e091b49e-a8ed-4a38-8ca7-80a46607e7b7.png)

# Steps for creating a Voting Application using AWS Serverless Services
1. Login to your aws management console and go to dynamo DB service
2. Create a Dynamo DB table with candidate as an attribute.
![image](https://user-images.githubusercontent.com/91054305/231667951-33af5beb-ead3-4baa-80e8-cd265fdedca7.png)

![image](https://user-images.githubusercontent.com/91054305/231667985-62ff8fba-6040-4f66-a7bd-ef2113a6b597.png)

3. Go to Lambda function and choose create lambda function and choose use a blueprint and search for Create a microservice that interacts with a DDB Table and give the      name of the function and choose run time as nodejs 14.x.
![image](https://user-images.githubusercontent.com/91054305/231668512-aa7260ce-5772-4889-b085-3d1502b14479.png)

4. Create a new IAM Role from AWS Policy Templates and enter the name of the role and by default it will come with a policy called Simple Microservice Permissions and      click create function.
![image](https://user-images.githubusercontent.com/91054305/231668559-079f5f97-e718-4d74-ab37-da43e6f55c25.png)

5. There choose ** ADD TRIGGER **  Option and search API Gateway -> Create a new API and choose API Type as  ** REST API ** and security as Open and in additional          settings choose deployment stage as Prod and create function.
![image](https://user-images.githubusercontent.com/91054305/231668589-495e450c-f934-451d-997a-47299572f982.png)

![image](https://user-images.githubusercontent.com/91054305/231668856-319c2985-8bda-4f9a-ba6e-4215fe103797.png)

6. In the code Editor copy the code from lambda folder CastVote.js and give the table name and attribute in the code and deploy the code. and create a test event 

   {
    "httpMethod": "POST",
    "body": {
        "vote": "Clinton"
    }
  }   
  ![image](https://user-images.githubusercontent.com/91054305/231668910-c4f1d766-1423-496e-8741-b3c60ccde5b2.png)

7. Click on test . If you get the statuscode as 204 then there is no error. if you get 400 there is something error in the code
![image](https://user-images.githubusercontent.com/91054305/231668942-e3174b33-9bb1-419c-b780-a3c0d05f7467.png)

8. Configure ** API Gateway ** . Go to the API created while triggering the API . There delete the default resources and create a new resource with Resource Name as        Vote. Create a new Method called post and Go to Integration Request And Click on Add mapping template and give the name as application/x-www-from-urlencoded and click    on save you will get a pop up message as change passthrough behaviour click on no use current behavior
![image](https://user-images.githubusercontent.com/91054305/231669081-97c68bf8-de52-448c-8450-5e07182e6dc2.png)

![image](https://user-images.githubusercontent.com/91054305/231669115-133b4429-665a-41d7-8eff-9f9db4da4caf.png)

9. And copy the code from Mappingtemp in github repo. And go to method response and delete the default one and create a 204 method.

![image](https://user-images.githubusercontent.com/91054305/231669149-071a1ada-16f2-4ed8-8edc-93b574c99441.png)

![image](https://user-images.githubusercontent.com/91054305/231669184-5ff4dcbb-7bc1-4364-a665-5daae65aff4e.png)

![image](https://user-images.githubusercontent.com/91054305/231669222-dea5a456-38e9-4e13-9251-68222ab13bb9.png)

10. Go to integration response delete the default one and choose the method response created earlier and click on save. Test the ** API Gateway ** . 
    {
      "httpMethod": "POST",
      "body": {
          "vote": "Trump"
      }
  }
  
  ![image](https://user-images.githubusercontent.com/91054305/231669245-9fa2c3ec-e8b4-4946-8eff-5f02aef4186e.png)
  
  ![image](https://user-images.githubusercontent.com/91054305/231669280-1167084c-f6ac-4d4f-afd6-591c6c4ed0fb.png)  

11. If you get Successfull Execution role then you will get trump in dynamo DB table items.
![image](https://user-images.githubusercontent.com/91054305/231669359-e5137ea5-e041-46b9-98f9-a9843b1a9383.png)

12. Go to Amazon S3 and create the bucket and give the name as unique. And go to properties and enable static web hosting and give index.html and click on save . Go to     permissions edit Block public acess. uncheck and confirm it. Go to bucket policy editor and click on edit and copy the code from github repo and paste and chane       the table name and click on save. 
![image](https://user-images.githubusercontent.com/91054305/231669378-bfaa3d31-017d-46f5-a6fb-70fa3222852c.png)

![image](https://user-images.githubusercontent.com/91054305/231669399-a6330c47-c8a7-4b8b-b5b2-06896a62dd92.png)

![image](https://user-images.githubusercontent.com/91054305/231669417-38e56e15-dc04-4715-9c72-faeec4935d94.png)

![image](https://user-images.githubusercontent.com/91054305/231669447-b968c386-bb1c-4f49-af45-5c83d22ad3d1.png)

13. Copy the url and paste in brower there we can see entire front end of application
![image](https://user-images.githubusercontent.com/91054305/231669504-b9d15a0f-542e-43bb-9154-175c249317f4.png)


14. Create another function and integrate with ** Dynamo DB ** as done in the earlier steps. Copy the code and paste and deply and click on test as done earlier
![image](https://user-images.githubusercontent.com/91054305/231669549-30535313-56f8-4521-800a-8f0388f13635.png)

![image](https://user-images.githubusercontent.com/91054305/231669568-970aa1e3-3ec7-4c9f-bc21-a1d72e09e095.png)

![image](https://user-images.githubusercontent.com/91054305/231669590-cd243bac-9d80-4d05-982d-c1b11951c467.png)

![image](https://user-images.githubusercontent.com/91054305/231669614-6de140e2-6377-4a57-bea6-24dc3c34c69a.png)

15. ** And The final Output of our application **

![image](https://user-images.githubusercontent.com/91054305/231669708-cb6ba957-537a-409c-a13c-ddfb61890f15.png)

