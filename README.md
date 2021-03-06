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

<!-- ABOUT THE PROJECT -->
## About The Project

This purose of this project is to demonstrate the knowledge of deploying webservers using CloudFormation for a web application that is highly available. We will be creating and deploying the infrastructure and a sample appication. The first componenet to deploy is to set up the network, the the servers, and then the storage and database. This project provides hands-on experience with Infrastructure as a code.


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
1. Install VScode -> https://code.visualstudio.com/, this is a useful text editor for writing the CloudFormation script using YAML and JSON

  
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- Instructions -->
## Instructions
1. Make sure you are signed in as IAM user, and not root user, as it is a secure practice to work as IAM user, and should not use or share root user as it is not a good practice and unsecure.

2. Then we will need YAML files to code the CloudFormation(more about this below) template files and JSON files to provide the parameters.
3. For the purpose of this project, template files (in YAML) are used to provide the configuration information of the resources in AWS that we desire to include in the stack.
   
#### CloudFormation
3. Create a CloudFormation stack.<br>
    What is CloudFormation?<br>
    "AWS CloudFormation is a service that helps you model and set up your AWS resources so that you can spend less time managing those resources and more time focusing
    on your applications that run in AWS. You create a template that describes all the AWS resources that you want (like Amazon EC2 instances or Amazon RDS DB 
    instances), and CloudFormation takes care of provisioning and configuring those resources for you. You don't need to individually create and configure AWS
    resources and figure out what's dependent on what; CloudFormation handles that" [Refer to this link for more info](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)
    
    a. Search for CloudFormation on AWS search and go to CloudFormation page. This pag shows all your CloudFormation stacks that were created
    ![image](https://user-images.githubusercontent.com/68451169/159187898-5783cded-4d4e-4692-a0f7-b188b8bae81a.png)

    b. In this step, click on create stack. You will be redirected to the Creat Stack page. ![image](https://user-images.githubusercontent.com/68451169/159188118-e7b29cc2-8d91-4a7a-a47a-3d9bf1ec0d23.png)

    c. From the above image select the option "Template is ready", under the Prerequisite section. And select "Upload a template file" for the Specify Template section.
    
    d. From this step the first file we will upload is the provided network template file called "ci-network.yaml". This file has establishes resources to set up NAT gateway, 2 private and 2 public in each of the 2 availability zones. This file can be viewed in the designer and it will look like screenshot below: ![image](https://user-images.githubusercontent.com/68451169/159191185-ef5d0abc-38f7-4a54-ad10-eba38e5980ee.png)
    
    e. Then click next on the "Specify Template" page, this will redirect to step 2 of the creation which is "Specify stack details". This will require a stack name, and Parameters for this stack. In this particular case we are setting up the network, for which we need 2 private subnet IP addresses in CIDR notation, and 2 public subnet IPs, along with the VPC. This can be left at the default values that are provided in the YAML file, an JSON parameters file as shown below. 
    f. The next is step 3 - configure stack options - this can be left as it is. And finally review the details in the next page and click "Create Stack".
    g. In the first stack we created using the ci-network.yaml file and parameters, we deployed VPC, with a pair of public and private subnets spread across two Availabilty Zones. It deploys an Internet Gateway, with a default route on the public subnets. It deploys a pair of NAT Gateways (one in each AZ), and default routes for them in the private subnets. The progress of ceating each resource can be seen in the events page as shown below: ![image](https://user-images.githubusercontent.com/68451169/160034936-f056983d-2f8f-44e0-a9bc-367fe580ed54.png)
    h. Additionally searching for VPC resource in AWS will show all the different resources we created, such as the NAT gateways, Subnets, and internet gateway.

    
4. The next step is to deploy 2 servers, 1 of which is given in the servers.yaml file. In this configuration, we are using Autoscaling and loadbalancer. Following same steps as above, we can create a cloudformation stack for the first server, which deploys 3 EC2 instances.  .... This is what the diagram looks like in the designer ![image](https://user-images.githubusercontent.com/68451169/160035562-10176e00-2438-4fcb-a1f6-a644705c722a.png)

5. The second instance is created in a much simpler manner without Auto Scaling or load balancer in order to demonstrate the knowledge of deploying servers based on the output of the network stack, using Yaml. Here is the diagram that shows how the EC2 that will be created in this stack is connected to the security group created from the network stack. The important thing is to use !Ref in yaml and reference the VPCID created by the network stack, the details of the process can be seen in the yaml file, how it uses the AMI, and current keyname as well as referes to the subnets of the network that we created earlier. ![image](https://user-images.githubusercontent.com/68451169/160171736-ad6ce01d-b975-4daf-b8af-859ad0860a57.png)

6. The important parameters needed to create this ec2 instance on this 2nd server that is different from the previous server (which used autoscaling and loadbalancer) is that this doesn't require the process of autoscaling, but since we need to deploy it on the network created in the first cloudformation stack, we include a subnet parameter to input the appropriate subnet id associated with the vpcid of the network interface we want it in.

7. The stack events page will clearly state if the instance is successfully created. Then we can go to the EC2 service page to see if the specific instance has been deployed.
![image](https://user-images.githubusercontent.com/68451169/160223747-d91c52e4-3f86-41c2-b6ad-155ec7f203e9.png)

![image](https://user-images.githubusercontent.com/68451169/160223711-622f247d-87a8-4346-8262-07ed2be35162.png)

 
8. A jumpbox is needed to be setup so that we can test to see whether or not the instances were successfully deployed in the right network that was created using yaml in the earlier step. The reason is because we deployed ec2 instances on the private subnets of the network which cannot be accessed directly, therefore we will create a jumpbox and ssh for this step. The first step is launch a new EC2 instance and with type t2.micro. For configuration step in creating instance, in network section select vpc created from the deployment of network from earlier step, then select a public subnet for the next section, and enable Auto-assign Public IP. Leave storage step as default. Then for Tags add a key with name "Jumpbox" for your reference. Then create a new security group, and add rule to allow SSH on port 22 from your ip source. Below are screenshots that will help with these details. ![image](https://user-images.githubusercontent.com/68451169/160222638-89e07c8f-700d-4e87-891c-ed37de669e18.png)
![image](https://user-images.githubusercontent.com/68451169/160222651-fdbe129c-65f3-49c3-a8b5-e1be40e831dd.png)
![image](https://user-images.githubusercontent.com/68451169/160222665-9ee3045d-38d8-4235-81e3-4ea7f603799d.png)

9. Now enter the command: (screenshot below) replace with jumpbox ec2 instance key, and the key used for the private server instance, and ensure to enter your jumpbox ip address respectively.  ![image](https://user-images.githubusercontent.com/68451169/160222941-1d920ab0-fa98-4ee3-ac9d-b114a1227cb3.png)

10. After this use ssh command to ssh to jumpbox. Once in the Jumpbox "ls" to ensure the key of the private server is in, then use chmod 400 on the key to change permission. The next step is to ssh to the private server using ubuntu@(private server ip). Once you ssh inside this private instance, run the command "service apache2 status", to check if Apache server is running in this ubuntu machine. This can be repeated for all the instances that are created. 


<p align="right">(<a href="#top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

Viswa Bhargavi - viswa.bhargavi.2000@gmail.com

Project Link: https://github.com/ViswaB/cloudcomputing-a2

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [GitHub Readme.md reference](https://github.com/othneildrew/Best-README-Template/blob/master/README.md)
* [AWS CloudFormation Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

<p align="right">(<a href="#top">back to top</a>)</p>
