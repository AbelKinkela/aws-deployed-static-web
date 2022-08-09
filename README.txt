cloudFont-distribution-link: https://d30l4uuvc2uf2v.cloudfront.net/

S3-website-link: http://my-20220809-udacity-bucket.s3-website-us-east-1.amazonaws.com/


In order to achieve this I went to AWS management console and searched for S3 in the search box.
Selected S3 then selected Create Bucket option.
I gave my bucket a name, choose the region and made it public. This is important because I want it to be publicly accessible

I uploaded the files(my website). This step took a lot of time. Maybe its because there were too many byte sized files in the content

Under the permissions tab, I edited the Bucket Policy option with the following JSON:
{
"Version":"2012-10-17",
"Statement":[
 {
   "Sid":"AddPerm",
   "Effect":"Allow",
   "Principal": "*",
   "Action":["s3:GetObject"],
   "Resource":["arn:aws:s3:::your-website/*"]
 }
]
}

Where "your-website" was replaced with my bucket name.

Under the properties tab I enabled static website hosting, I specified the homepage file and error page to be index.html.
I copied the website end point provided.

Next, I searched for cloudfront in the aws management console search bar and created a new distribution.

For the domain I copied the website endpoint provided when creating the s3 static website hosting.
Under the viewer protocol policy I selected Redirect HTTP to HTTPS and left all the other options as default.

Waited a few minutes and the deployement was done. I copied the domain name provided and used it to access my website
