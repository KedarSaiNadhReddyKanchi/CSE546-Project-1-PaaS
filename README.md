# Group Project2 : PAAS

## CSE 546: Cloud Computing Project

Group members:

- Atul Prakash - 
- Abhi Teja Veresi- 
- Kedar Sai Nadh Reddy Kanchi - 

<hr>

S3 bucket names: `cc-input-546` and `cc-output-546`

Credentials:

aws_access_key_id = ` `

aws_secret_access_key = ``

Config: `region=us-east-1`

AWS ID: `kkanchi@asu.edu`

AWS Password: `@Fall2023`

IAM role: `  - arn:aws:iam:::role/`

PEM key -

-----BEGIN RSA PRIVATE KEY-----

-----END RSA PRIVATE KEY-----

<hr>

## Member Tasks

### Atul Prakash - **(ASU ID: )**

* **Setting up Infrastructure:** I have created the infrastructure requirements for the project and some testing of the project, which includes setting up all the buckets (input bucket and the output bucket), DynamoDB, and AWS Lambda along with Kedar. The workload generator was used to upload the input video to the input bucket and use it as a target. As the video is uploaded to the bucket the Lambda function gets triggered as an object creation event occurs in the input bucket. After uploading the file to the AWS S3 input bucket, it will automatically trigger the lambda function. The video file was then downloaded to the Lambda function’s directory before extracting the name of the video for the event.  For DynamoDB, the student’s academic information provided (students_data.json) was uploaded to the database, and the unique ID given was used as the primary key for the database. I  also helped in testing the code and checking whether the data was being processed correctly or not and whether we were getting the desired results or not and fixing the problem if any issue occurred.
* **Code:** Generated code in the handler.py file to create the CSV file from the given data and uploaded the file along with the results to the output S3 bucket. I have also implemented the dynamodb_result function to get the data from DynamoDB that matches the results from face recognition. And initially, upfront I have written the code file “loadStudentData.py” to upload data from the provided student_data JSON file to an Amazon DynamoDB table.
* **Report and Readme creation:** Helped in writing the report using the provided template and also created the README file which contains the details of the installation requirements and the steps to run the application.

### Abhi Teja Veresi – (ASU ID: )

* ****Code Generation**:** Generated code in the handler.py file for the image processing function. In this function, the first thing I did was load one of the image files that were extracted from the video. In this project, I have chosen to go with the 2nd extracted image “image-002.jpeg”. The code command to load the image file was present in the face_recognition Python documentation provided by the professor in the project description on Canvas. After loading the image, I then moved to extract the face encodings for that image using the code command present in the documentation. The extracted encoding is the unknown encoding. Now, the main functionality of this function was to compare this unknown encoding with all the known encodings present in the encoding file. So, for this, I now moved to load the encoding file from the working directory using the pickle library. After loading the encoding file, I extracted the names into one list and the corresponding face encodings into one list. Then, we used the comapre_faces function which is provided in the documentation to compare the unknown encoding which we extracted with each of the provided known encodings. Finally, I find the index at which the unknown encoding matches with some known encoding and return at that name at that index.
* **Testing:** Tested the results after completion of the application by sending videos by increasing the input limit and verifying the output with the provided mapping file.

* **Report and Readme creation:** Helped in writing the report for testing and code sections in it using the provided template.

### Kedar Sai Nath Reddy Kanchi-  (ASU ID: )

- **Setting up Infrastructure:** To set up the Lambda function, a lot of prerequisite things had to be set up. For this, the first thing me and Atul did was to create a new IAM Policy “S3-DYNAMODB-CLOUDWATCHLOGS-ACCESS-FOR-LAMDA-FUNCTION-PROJECT2” within which I have defined the permissions for the CloudWatch Logs, DynamoDB, and S3 buckets. Then I and Atul created a new IAM Role “CSE546PROJECT2ROLE” to which the above-mentioned IAM Policy was attached. Now, with the access set, the next step was to build the Elastic Container Registry Image. So, for this, me and Atul installed the Docker Desktop for Windows. Then we opened the Docker Desktop and started a new session to help us with the next step. Now, we opened the command prompt and created the Elastic Container Registry Image. Finally, using this Elastic Container Registry Image we have created the Lambda Function “AWSLAMDAFUNCTIONPROJECT2CSE546” and while creating the Lambda Function we have attached the new IAM Role that we created for this project. To finish the infrastructure, we made small changes in the Lambda Function, such as increasing the memory size to 512 MB from the default set value of 128 MB and the timeout from 3 seconds to 5 minutes. Lastly, we have set the trigger for the Lambda function to be when there is any create event specified by “ALL CREATE EVENTS” in the input S3 bucket “cc-input-546”.
- **Code Generation:** I specifically have worked on extracting the new event triggered when a new file is uploaded into the S3 bucket. This is basically to extract the newly uploaded video from the input S3 bucket and save it in a local directory “videos” and subsequently delete the event which basically deletes the newly uploaded video from the input S3 bucket. Post implementing this I then moved on to implement the function to extract the images from the currently extracted video. This function was simple to implement with the help of the professor’s sample command provided to us in the project description.
- **Report and Readme creation:** Helped in writing the report for testing and code sections in it using the provided template.
