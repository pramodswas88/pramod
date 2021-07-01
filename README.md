############ Frontend Application AWS workflow #####################################

For Frontend AWS Services -

First create s3 bucket - Enable Static website hosting - bucket permissions as per your requirement.
Take the s3 bucket endpoint. 
Create the Cloudfront distribution (follow cloudfront basic steps)--- you'll get cloudfront Domain name.
Take the cloudfront Domain name, create the record set in Route53.

**s3 origin Domain name ------------- Cloudfront Domain name ------------- Route53 CNAME Recordset**

And the Record Name is in Godaddy account - so, you are adding the Recordset to the Godaddy Recordname. for confirmation - goto godaddy account, select the Domain name, check the Domain name and DNS Settings.

Now the enduser request is from

**Enduser -------- Godaddy ------- Route53 CNAME Recordset ----------- Cloudfront Domain name ---------- s3 origin Domain name.**


Feed to s3 bucket is from 

**Developer - Code ------ SCM(GitHub) -----(webhooks/pollscm)----- Jenkins job will trigger builds the code, Artifactories are storing in Nexus Repository and deployed into s3 Bucket. **

How it is happening, By using Execute shell commands in Jenkins.


################ Backend Application AWS Workflow ################################


For Backend AWS Services -

First create EC2 Instance (install required softwares)
Create Target Groups - Select the EC2 instance
Create Network Load Balancer -  Select the Target Groups
Take the NLB endpoint - 
Create API in API Gateway - 
Create VPC Links - here select the NLB Option  (update NLB endpoint) and you'll get VPC Link ID
Create stage - in stage variables update VPC Link ID & NLB endpoint
Create Custom Domain Name - you'll get API Gateway Domain Name 
Take the API Gateway Domain Name - update in Route53
Create a Record set in Route53. (This is the Backend Application URL)



























