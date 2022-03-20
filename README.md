<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#project-link">Project Link</a></li>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#instructions">Instructions</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

## Project Link


<!-- ABOUT THE PROJECT -->
## About The Project

This purose of this project is to demonstrate the knowledge of deploying webservers using CloudFormation


<p align="right">(<a href="#top">back to top</a>)</p>


### Built With
 
* YAML, JSON
* [Amazon Web services](https://aws.amazon.com/)
* [AWS IAM](https://aws.amazon.com/iam/#:~:text=AWS%20Identity%20and%20Access%20Management%20(IAM)%20provides%20fine%2Dgrained,to%20ensure%20least%2Dprivilege%20permissions.)
* [AWS CloudFormation](https://aws.amazon.com/cloudformation/)


<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

#### AWS (Amazon Web Services)
1. Create an account in AWS for free using Free Tier-> https://aws.amazon.com/.<br>
      What is AWS?<br>
      AWS stands for Amazon web services and it is a fundamental cloud service used for cloud computing which offers a wide array of cloud-based products at a global scale
![image](https://user-images.githubusercontent.com/68451169/153737463-07b67189-4ebf-48c1-94a8-a78ab0022f9c.png)

#### IAM
2. Once you have created a Free Tier account, and verified it, search for the service of IAM (Identity and Access Management Service) in the search bar of AWS.<br>
   What is IAM?<br>
    IAM is a service of AWS has for multiple users and group users of same account 
    because the root account should not used or shares for security purposes. IAM is a global service therefore does not need region selection, and in the service users, who are     people within an organization, can be grouped into not just one but miltiple groups, although not required to. 
    
3. Create an IAM user and provide admin access. 
      a. Once you click on IAM from search results, you'll be on the IAM service page. On the left there is a menu, labeled Dashboard. In this dashboard the first category is
      Access management under it find the option "Users" and click on it, where you'll be taken to a page to create users. Click on Add users on top right. 
      b. Provide a username, and next select "Password" under Select AWS access type, where you'll be provided with a few options. Either choose to autogenerate password, or
      provide custom password, and choose whether or not to require a reset of password when IAM user login for the first time. For the purpose of this project it is required to       create an IAM user for yourself, so you can choose custome password and not require to reset it. Click next.
      ![image](https://user-images.githubusercontent.com/68451169/153738844-6859c8a4-a214-429d-b33d-50f7cb769dd0.png)

      c. Add user to group, by creating a group and including with policy "AdministratorAccess" as shown below. Click next. This takes you to add tags, which is not required.
      Click next for review. Create user. The next page you'll see a confirmation for successfully creating user, and option to send email instructions. You can close this page
      now. 
      ![image](https://user-images.githubusercontent.com/68451169/153738972-5aae80ce-9163-44bb-aa60-0e772452958d.png)

      d. Take note of the Account ID from your root account by clicking on your username on top right of root account. Then Sign out of root account. Sign into console using IAM
      user. IAM sign in requires the Account ID, along with username and password of the IAM user provided during creation of the user. Now we have secured the project using IAM
      policies. 

### Installation
1. Install VScode -> https://code.visualstudio.com/, inorder to code in html and css, which will then be uploaded to the S3 bucket.

  
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- Instructions -->
## Instructions
1. Make sure you are signed in as IAM user, and not root user, as it is a secure practice to work as IAM user, and should not use or share root user as it is not a good practice and unsecure.
   
#### S3 
2. Create an S3 bucket.<br>
    What is S3?<br>
    Amazon S3 allows the storage of objects (files) in forms of buckets.
    Buckets must have a name that is globally unique are defined at the region level.
    The Naming convention requires the following: No uppercase, No underscore, 3-63 characters long, Not an IP.
    
    a. Search for S3 on AWS search and go to S3 page. This pag shows all your S3 buckets that you have created
    ![image](https://user-images.githubusercontent.com/68451169/153739102-33a3d2a3-fc2e-478a-827f-fe5e5eedcfdb.png)
    
    b. In this step, click on create bucket, and provide a globally unique name to the bucket. All other settings for creating a
    bucket can be left as default.
    Once this is done, click create at the bottom of the page.
    ![image](https://user-images.githubusercontent.com/68451169/153739117-f437a099-253a-4b55-8f4d-ce1b14c49a29.png)
    
    c. You will now see the bucket you created in the main S3 page. click on it. Here you'll see an option to upload your files. For the purpose project I uploaded 5 html pages,        2 image file, one video, and 1 css styling sheet. S3 is very useful when creating a webpage using HTML, CSS and Javascript.
3. S3 bucket allows for versioning of files where you can upload a file of same name more than once and the bucket will show the latest update upfront, but also it stores all
   other uploads as different versions. It is best to version buckets, as it is easy to access or go back to a previous version, as well as restore a version if deleted
   unintentionally. To use this feature, click on bucket and go to the "Properties" tab and select the edit option under Bucket versioning, select "enable" and save changes.
4. The best practice is to not allow public access of buckets. Go to "Permissions" tab of your bucket and ensure that public access is blocked. Public access is blocked by
   default is blocked when creating the bucket. There will be no direct link to access the site or contents of the S3 bucket, which leads to next step.
   
#### CloudFront 
5. Create a CloudFront Distribution.<br>
   What is CloudFront?<br>
    CloudFront is a content delivery network (CDN) service of AWS. Since the S3 bucket is private, CloudFront helps in accessing the site as it works with both public and
    private buckets. It cahes the content to imrove performance, and make it available fast and secure for the 200+ edge locations. It uses Origin Access Identity (OAI) which is
    a feature of CloudFront that enhances security
    
    a. Search for cloud front in AWS. Go to the Cloud front page and click Create Distribution. 
      ![image](https://user-images.githubusercontent.com/68451169/153740436-bfdd20e1-fe00-4408-a3f3-f3797dd3a29e.png)
      
    b. When clicking into the Origin Domain blank, a drop down menu pops up with your current S3 buckets, select the S3 bucket with the current projects' contents. This will auo
       fill the rest of the distribution creation settings page. 
       
    c. Next take look at the S3 bucket access section of this page. Select "Yes use OAI". Then Create new OAI. And uncer bucket policy sub section of OAI, select Yes update the
       bucket policy, which will automatically change the access permission of the S3 bucket, instead of the user having to manually update it. 
       
    d. All other settings can be left to default. 
    
    e. Scroll down to Default root object section, which is optional, but you can provide the name of file from S# bucket that you want to set as default. For the purpose of
       this project I set index.html as default root page.
       
    f. Leaving all other sections to its default settings, click Create Distribution at bottom of page. It takes a few minutes for the CloudFront distribution to deploy.
    
6. Once the distribution is deployed, click on it, and under the General tab there is a Distribution Domain Name section under it a link to your S3 website. This is the main
   link used to access the contents of S3 bucket. Enter the link in browser to ensure the website works as intended. The link for this project is provided in the top.
   ![image](https://user-images.githubusercontent.com/68451169/153740718-145b19bc-185f-411a-8b28-84fbf27dbbf9.png)

7. Now this link can be shared for public access, while the S3 bucket is secure.

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

Viswa Bhargavi - viswa.bhargavi.2000@gmail.com

Project Link: https://github.com/ViswaB/cloudcomputing-a1

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [GitHub Readme.md reference](https://github.com/othneildrew/Best-README-Template/blob/master/README.md)

<p align="right">(<a href="#top">back to top</a>)</p>
