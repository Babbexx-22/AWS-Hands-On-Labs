## Content delivery using AWS CLOUDFRONT

Amazon CloudFront is a content delivery network operated by Amazon Web Services. Content delivery networks provide a globally-distributed network of proxy servers that cache content, such as web videos or other bulky media, more locally to consumers, thus improving access speed for downloading the content.


## STEP 1: Creating S3 bucket and uploading our files.

* A S3 bucket was created and public access was enabled. The bucket policy was configured to allow 'listbucket, getobject and putobject" from a wildcard (*) as the principal.

![policy](https://user-images.githubusercontent.com/114196715/199644131-1cee1a42-f84d-407b-8f83-b2699b9091fe.png)

* Upload the file '14.png'

![objects](https://user-images.githubusercontent.com/114196715/199645663-0391c30f-e69a-408e-bf64-da612647db27.png)

* Try to access the url of the object in a web browser.

![accessible](https://user-images.githubusercontent.com/114196715/199644395-8b0b6d46-00f6-4e50-baa7-b533dca598f9.png)

## STEP 2: Creating a customerror folder

* Create a 'customerror' folder in the S3 bucket, therein upload the pre-customised (using notepad) 'error.html' and 'block.html' file.

## STEP 3: Creating CloudFront Distribution

* Create a cloudfront distribution and select your S3 bucket as the origin domain name.

* Copy the domain name that Amazon CloudFront assigns to your distribution, input it in a web browser, append the name of your object and try access it in a web browser.

![cdn domain](https://user-images.githubusercontent.com/114196715/199644639-b60b7bcd-0a04-410a-9288-7f248216c3d4.png)

N.B: It was observed that the page loads faster than that of the object URL.

# CONFIGURING CUSTOM ERROR PAGE

* Click on the created cloudfront distribution, select the 'custom error response' and configure it as presented below:

![config error](https://user-images.githubusercontent.com/114196715/199644848-6c782c5f-80a0-4d29-b250-dda391508bbc.png)

* Navigate back to the ditribution page and allow it to deploy

* Try access a content not present in your bucket. It throws an error as configured in our error.html file

![error page](https://user-images.githubusercontent.com/114196715/199645201-850b1a36-4f72-4297-a446-059371132aed.png)

## STEP 4: Restricting the Geographic Distribution of Your Content

* Click on the cloudfront disribution created. On the distribution settings page, select geographic restrictions.
* In the restriction type section, select block list, and specify the country you are in (in a bid to simulate georestriction).
* Try to access the object using the cloudfront domain name as done in step 3 above. The page returns the following error:

![not accessible](https://user-images.githubusercontent.com/114196715/199645299-b238f730-a6e7-4b64-96d5-08894ddb3b0f.png)

# STEP 5: Configuring our error response to server the content of our block.html file

* Click on the custom error response icon, and configure it as below:

![block config](https://user-images.githubusercontent.com/114196715/199645521-c8c851ba-8f8c-45a0-b4ce-5df42f65a5df.png)

* Wait for your cloudfront distribution to finish deploying.

* Reload the webpage. The following response is returned:

![georestriction](https://user-images.githubusercontent.com/114196715/199645573-4321182d-2116-4ee2-97ca-78c60b25feb3.png)

* We have successfully used cloudfront, customised our custom error response and simulated georestriction *
