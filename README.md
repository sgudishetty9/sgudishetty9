Start the lab and copy the aws credentials from AWS Details as we need to configure with this credentials in our EC2 instances once we SSH them.
Get into console, then navigate to EC2 > click 'Launch Instance' to create new instance.
Name the instance, we are creating 2 instances, one for recognizing cars, one for recognizing text, select suitable AMI that works with Java, better to leave the instance type to default 't2.micro' as it is sufficient for our assignment.
Create a new key-pair and download it to your OS as it's required for SSH and SCP.
Create a security group and allow traffic from SSH (only your IP), HTTPS & HTTP from Internet.
Leave all other settings to default and launch the instance, do these steps twice for both the instances.
Ensure IAM role is set to LabInstanceProfile for both the instances (Instance > Actions > Security > Modify IAM Role) as lab role provides us permissions to access SQS, S3 and Rekognition.
Once you are ready with your codes, we have to SCP .jar files into their specific instances.
Make sure to change permissions of <your-key-pair>.pem to read-only, you can run the command chmod 400 <your-key-pair>.pem for that.
Command to SCP: scp -i <your-key-pair>.pem <your-car/text-code>.jar ec2-user@<your-instance-dns>:/home/ec2-user
Now we have to SSH both the instances to run our .jar files/assignment.
You can find the command to SSH in your console (Instance > Connect > SSH Client), copy the example given there and run it in your terminal to connect to the instances.
As I stated in first step, paste the credentials into ~/.aws/credentials in both the instances and update them after every session ends (4 hrs).
Install Java on both the instances to run your .jar files.
Use the command java -jar <your-code>.jar to run the recognizing car code and suffix it with > 'output.txt' for running text code as output have to be copied into the file.
I have successfully finished my assignment in this pattern, hope this works for you as well:)
My output screen after recognizing cars:
<img width="1440" alt="Screenshot 2023-10-19 at 10 47 10 PM" src="https://github.com/sgudishetty9/sgudishetty9/assets/144736938/a323e379-274b-41e4-9f6a-0b15a67f2ed1">
My output screen after recognizing text on cars:
<img width="1440" alt="Screenshot 2023-10-19 at 10 48 06 PM" src="https://github.com/sgudishetty9/sgudishetty9/assets/144736938/b96f712d-de65-4292-8854-3fb5f70663d3">
