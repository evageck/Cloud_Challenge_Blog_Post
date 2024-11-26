# Cloud Resume Challenge

This semester, I have been enrolled in the Network and Cloud Computing course at Loyola Marymount University. In this course, I was tasked with completing the Cloud Resume Challenge, a project created by cloud architect Forrest Brazeal. Initially, I found the challenge daunting, as I had never worked with Amazon Web Services or tackled such a multifaceted project. However, that initial overwhelm turned into motivation, reminding me why I chose Information Systems and Business Analytics: I thrive on challenges that push me beyond my comfort zone and foster intellectual growth.

## The Frontend
To kick off the project, I familiarized myself with AWS services and set up my S3 buckets to store the files for my website and resume. The main bucket hosts my `index.html` file, which forms the foundation of my resume's structure using HTML, along with CSS for styling. Additionally, this bucket contains my JavaScript file, which I'll discuss later. To enhance my website's professionalism, I purchased 'evageck.com' from Namecheap and linked it to my S3 bucket, replacing the default AWS endpoint. I then took steps to ensure my resume was hosted securely using HTTPS through AWS Certificate Manager by creating and validating an SSL/TLS certificate. This certificate was then associated with my CloudFront distribution, which is a content delivery network (CDN) designed to optimize performance. This setup ensures that my website is accessible quickly and efficiently from any region worldwide while enhancing both security and privacy for users.

## The Backend
I implemented a visitor counter to display the number of users visiting my website, incrementing with each new visit. Using DynamoDB, a NoSQL database, I created a table to store and update the visitor count, enabling seamless data sharing and interaction between the backend and frontend of my project. A Lambda function, coded in Python, handled retrieving and updating the count, which was made accessible via a secure API endpoint hosted on AWS API Gateway. To secure the endpoint, I implemented IAM roles for authorized access and configured CORS settings to enable frontend API calls while blocking unauthorized origins. I then created a JavaScript file to call this API and incorporated it into my `index.html` file, allowing the visitor count to update and display in real time. This bridged the backend and frontend, enabling the API to be triggered by users visiting my site. I validated my implementation using the testing framework `pytest`, conducting three tests: a unit test to verify Lambda functionality, a system test to ensure DynamoDB updates were accurate, and an end-to-end test to simulate the user journey and confirm seamless interaction between the frontend and backend.

## Infrastructure as Code (IaC)
To enhance productivity and minimize simple errors, I implemented Infrastructure as Code (IaC) using Terraform. By defining and deploying my infrastructure through code, I eliminated the need for repetitive manual updates in the AWS Management Console. This allowed me to efficiently manage and configure my resources, such as my S3 bucket and CloudFront distribution, directly in code.

## CI/CD Integration
Continuous Integration and Continuous Deployment (CI/CD) were essential for seamless updates across my project. I created three GitHub repositories for the frontend, backend, and infrastructure code, using GitHub Actions workflows to automate testing and deployment. These workflows ensured that changes pushed to the repositories were automatically tested and deployed to the appropriate AWS resources, streamlining updates and maintaining consistency across all components.  
Checkout my repositories: Frontend, Backend, Infrastructure.

## Challenges
While updating my S3 bucket and testing my website, I was initially confused when changes didn’t appear. I realized I needed to manually invalidate the CloudFront cache after each update to my `index.html` file. This highlighted the importance of CI/CD pipelines, so I added a step to my GitHub Actions workflow to automate cache invalidation, ensuring users always saw the latest version.

## In Conclusion
This project provided valuable insights into cloud architecture, allowing me to develop practical skills with AWS services like S3, Lambda, API Gateway, DynamoDB, and CloudFront. I learned how these services integrate to build scalable, secure, and efficient systems. It highlighted the importance of automation through Infrastructure as Code and CI/CD pipelines, as well as the need for precise configuration to ensure functionality. This process sharpened my problem-solving abilities, strengthened my understanding of cloud design, and reinforced my academic resilience.  

You can view my completed Cloud Resume Challenge at [evageck.com]. Wishing everyone a wonderful and blessed Thanksgiving!
