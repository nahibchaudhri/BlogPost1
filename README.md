# BlogPost1
##Introduction
I took on the Cloud Resume Challenge because I wanted to showcase my technical skills and demonstrate my ability to learn something new from scratch. This project was an opportunity to deepen my understanding of cloud infrastructure and gain hands-on experience with AWS. Through the challenge, I learned many essential skills while building a web application to host my resume on the cloud. I developed a front-end website using HTML and CSS to display my resume, a serverless API to support an encrypted visitor counter using AWS services like S3 and Lambda, and automated the entire deployment process with CI/CD pipelines and Terraform.

##Building the Front End
The front end of the project began with Route 53, which managed the DNS configuration, allowing visitors to access the website using a simple domain name, nahibchaudhri.com, instead of a long, hard-to-remember AWS endpoint. The domain was registered through Namecheap, and SSL certificates were managed using AWS Certificate Manager, enabling secure HTTPS connections for a professional user experience. To enhance performance, CloudFront was used to cache the website in edge locations, ensuring faster loading times for users far from the hosting region (us-east-1). The actual platform hosting the website was an S3 bucket, where the index.html file resides. While the CSS was embedded directly into the HTML for simplicity, a small amount of JavaScript powered the visitor counter. This script called API Gateway, which connected the front end to a Lambda function. The Lambda function retrieved and updated the visitor count stored in a DynamoDB NoSQL database, ensuring the system was cost-efficient, serverless, and scalable.

##Building the Back End
To enable the visitor counter, a serverless architecture was implemented using several AWS services. DynamoDB, a NoSQL database, was chosen to store visitor counts due to its scalability and reliability. The logic for interacting with the database was handled by an AWS Lambda function written in Python. This function securely and efficiently processed requests without the need to maintain a server. The API Gateway connected the front end to the Lambda function, ensuring requests were properly authenticated and routed. Together, these components created a seamless and scalable system for tracking and updating visitor counts dynamically.

##Building the Infrastructure
The infrastructure of the project was built and managed using Terraform, which played a crucial role in automating changes to the backend, including upgrades to the S3 bucket that hosted the website. Updates to the infrastructure were deployed through GitHub, following a simple process. Changes were staged using git add, a descriptive commit message was created with git commit, and updates were pushed to the repository using git push. These actions triggered GitHub Actions, which automated the workflow to deploy updates to the S3 bucket. This streamlined approach ensured efficient and consistent upgrades while leveraging automation to minimize errors and maximize reliability.

##Challenges
One specific challenge I faced was integrating the visitor counter with AWS services. Initially, the API Gateway, Lambda function, and DynamoDB weren’t communicating as expected. The visitor counter failed to update, and debugging revealed that the Lambda function lacked proper permissions to access DynamoDB. To fix this, I had to carefully review and update the IAM role attached to the Lambda function, granting it the necessary read and write access to the database. This process taught me the importance of correctly configuring permissions and thoroughly testing each component of the system.
Another challenge arose when configuring HTTPS for the website using AWS Certificate Manager. I struggled to validate the SSL certificate because the domain settings in Route 53 were misconfigured. After troubleshooting, I realized that I hadn’t correctly added the CNAME records provided by the Certificate Manager to Route 53. Once the records were correctly added, the certificate was validated, and HTTPS was successfully enabled. This experience highlighted the value of attention to detail when managing DNS and security configurations.

##Reflection
The Cloud Resume Challenge was an incredible learning experience that allowed me to explore the intricacies of cloud technologies and apply them to create a live, functional product. Completing this project gave me a deeper understanding of AWS services like S3, Lambda, DynamoDB, CloudFront, and Route 53, all of which played essential roles in building and deploying the resume. From hosting the website and managing data to optimizing performance and securing access, every component enhanced my appreciation for cloud infrastructure. One of the most impactful lessons was working with serverless architecture. Implementing a visitor counter using Lambda and DynamoDB showcased the efficiency and scalability of serverless solutions. Securing the website with SSL certificates and enabling HTTPS using AWS Certificate Manager provided valuable insights into cloud security. Using CloudFront to cache data at edge locations further emphasized the importance of performance optimization for global users. Beyond technical skills, this challenge gave me the rewarding experience of creating a tangible product I can proudly showcase as part of my portfolio. It demonstrated my ability to design and deploy cloud-based solutions, reinforcing my confidence in tackling real-world challenges in the field of cloud computing.



