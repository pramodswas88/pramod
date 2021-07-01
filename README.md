# Frontend Application AWS workflow
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




















