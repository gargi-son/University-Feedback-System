
Part 1: Creating a website using S3 bucket

AWS URL of the homepage: http://swe645-gss04.s3-website-us-east-1.amazonaws.com


Name of the bucket: swe645-gss04

File names uploaded to the S3 bucket:
	- HTML Homepage File: index.html
  	- HTML Error Page file: error.html
  	- Image files folder: Files
   	- Image filenames in Files folder: bahai.png, Beach.jpg, chicago.png, galaxy.jpg, Lincoln.jpg, sky.png


Creating a S3 bucket:
	- Create an account on AWS
	- Go to AWS Management Console --> Services --> Storage --> S3 Bucket -->  Create Bucket
	- Give your bucket a name and select the appropriate region.
	- Unselect the 'Block all Public Access' --> Create Bucket.
	- You should be able to see the created bucket on the main homepage of your console.
	- Click on the bucket --> Go to properties --> Static Website Hosting --> Edit --> Enable --> Hosting type: Host a Static Website --> Give name for your index document and error document. --> Save Changes.
	- You can now upload your index file, error file and all the related files to the S3 bucket.
	- To get the URL for your website --> go to the bucket --> properties --> Static Website Hosting. You should be able to see your URL under that tab.


To navigate to the Student Survey Form, Click on the Survey Form link on the navigation bar at the top of the page.