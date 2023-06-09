# DevOps and AWS

## What is DevOps?

DevOps is a combination of Development and Operation skills which help to bridge the gap between the two, and creates the tools that make the development and deployment pipeline more efficient through the automation.

The main reason why DevOps became so popular lays in its benefits, which are:

* Improved efficiency - by automating processes teams are able to release product quicker
* Adaptability - as DevOps mainly uses Agile methodology, it allows the team to be more flexible and adapt to the customers needs
* Improved Collaboration - as we established in its term, DevOps helps to reduce the gap between Development and Operation teams and make their communication better
* Security - DevOps helps to integrate security protocols into agile workflow

### 4 Main Pillars of DevOps

* Communication - face to face communications are important. Team has to constantly communicate with each other to improve the quality of their product, troubleshoot any problems and learn from each other.
* Collaboration - better collaboration between development and Operation teams helps to better prepare the product that goes from development into deployment.
* Automation - it is the core of the DevOps. It helps to reduce the time gap between development and deployment stages, making the delivery of the product more efficient.
* Monitoring - provides an information about service uptime and performance. This information can help the team to determine any areas of improvements that could be done for the next release.



## What is Cloud Computing?

Cloud Computing is the on-demand provider of IT resources over the Internet. Instead of buying and maintaining on your own, Cloud Computing allows you to "rent" technology services, such as storage, databases, and computing power.

The benefits of the cloud computing are following:
* Agility - you get access to many technologies in the matter of minutes and don't need to spend time on setting them up.
* Elasticity - depending on your business activity, resources you use can be scaled up or down, depending on the demand, meaning, you don't have to pay for more resources in advance.
* Cost saving - you only pay for what you are using.
* Deploy globally - by having databases around the world you can easily deploy your product anywhere you need.

The reason "Why we should use Cloud Computing" lays in the benefits that are explained above. 
It also helps businesses to protect their data against loss, in case the local machine is malfunctioning or corrupted, and companies that use Cloud Computing don't have to worry about the security, as it will be cloud service provider's responsibility to ensure that all the data stored is secured.

### How cloud computing fits into DevOps?

As DevOps is about automation and making the workflow quicker it relays a lot on Cloud services.  
Cloud Computing allows DevOps to create tools that will be hosted on the cloud server for easier access and maintenance.
Having accessible tools on the cloud server helps DevOps to improve collaboration in the team, as all the files will be centralized and located in one space. 


## Create a VM on AWS

1. Once you logged in to AWS, you have to ensure that your selected region is correct. In our case it has to be `Ireland`, as it is the closest one to us that has all the tools we need.
   ![Select region](resources/aws_region.JPG)
2. In the search bar type `EC2` and search for `EC2 Services`. Once you found it - click on it
   ![EC2](resources/ec2_search.JPG)
3. In the new page search for a button called `Launch instance`. This button also has a dropdown menu where you can select to create a new instance or use the template. Currently, we are going to create a new one from scratch.
   ![Launch Instance](resources/launch_instance.JPG)
4. There are few settings we need to change before we create our instance:
   * Add the name of your instance. Ensure you are using the correct name convention
      ![Instance Name](resources/instance_name.JPG)
   * Select the OS for your VM. In our case we are using `Ubuntu Server 20.04 LTS (HVM), SSD Volume Type`
      ![AIM version](resources/vm_os_version.JPG)
   * Select instance type. For our example default one is enough - `t2.micro`
      ![Instance Type](resources/instance_type.JPG)
   * Select your SSH key. Search for the key called `tech221` in the search bar and select the key
      ![Instance Key](resources/instance_key.JPG)
   * Now you need to edit security groups:
      * add the name and the description to your security group
         ![SG name](resources/network_settings_name.JPG)
      * set your SSH security group. Ensure that `Type` is set to `ssh` and `Source Type` is set to `My IP`
         ![Security Group 1](resources/security_group_1.JPG)
      * Add new security rule by clicking on `Add security group rule`
         ![Add Security Group](resources/add_security_group.JPG)
      * set your HTTP security group. Ensure that `Type` is set to `HTTP` and `Source Type` is set to `Anywhere`
         ![Security Group 2](resources/security_group_2.JPG)
   * Rest of the settings you can leave be default for now. Then head to `Summary` to verify everything and then click on `Launch Instance` to start your VM
      ![Create Instance](resources/launch_created_instance.JPG)
   
## Connect to your Instance through GitBash

1. Go to `Instances` and in the search bar type the name of your instance, the one you have created
2. Once you found your instance ensure that it is running. 
3. You can use `Instance State` menu to `Start`, `Stop`, `Reboot`, `Terminate` your instance
4. When instance is running and it is selected, click on `Connect` in the top right corner
5. In the new window make sure you are on `SSH` connection tab
6. Follow the instructions provided to connect to your instance through GitBash. Make you you run everything from your `.ssh` folder
7. !!!Please note, when you restart your instance the IP address will change so you will have to visit this page again and copy a new link to connect!!!


## Creating an AMI
AMI allows you to create a "snapshot" of your instance, to prevent lose of data in case of instance being terminated. You can use then AMI to launch a new instance with all the data you had on it previously. You can also share this AMI with someone else so they could start working with it without worrying about setting it up first.

![AMI Diagram](resources/custom_ami_1.gif)

When start working with AWS user has a few options:
* User can use some of the default AMI available if they meet user's needs
* User can create a new instance from scratch and customize it for their needs
* User can use their custom instance in order to create an AMI to save the data and then re-use this version later

You can use AMI similar to version control on Git, whenever you make changes, configurate or install new services, you can create a new image with those updates, so then you can use updated version later, or if updates don't work, you can roll back to the previous image.


### How to create an image

1. Go to Instances
2. Search for your instance, you can use a searchbar, and then select it
3. Once selected, click on `Actions` in the top right corner, and then go to `Image and Templates` --> `Create Image`
4. In the new window you need to give the name to your instance, remember to follow naming convention and give it a logical name
5. You can add description (optional), for example what services are installed or what security groups need to be added
6. Once it's done you can leave the rest as default and click on `Create Image`

### How to make an instance from your image

1. On the left panel search for `Images -> AMIs` and click on it
2. Search for the image you have created, you can use the searchbar, and select it
3. On the top right corner click on `Launch Instance from AMI`
4. On the new page just follow the same instructions as when you are creating a new custom instance, the only difference you do not have to change anything for "Application and OS Images", as it will use the image we have created
   * If you are not planning to make any changes to the instace and you only want to allow the user to use what is there you can skip SSH connection
5. When all the setting are completed you have to click on `Launch Instance`
6. Now, just wait for your instance to start and it will be ready to use shortly!



## Add custom user data to your instance
To make your process of creating and setting up new instance faster you can use "Custom User Data" in order to automate some of the configuration. 
For example, after we create an instance we used to connect to it throught Bash and then write and run the script in order to update the environment and install required packages. With "User Data" we can write our script there and it will execute it and do all the required installations whilst creating the instance, making th process much quicker for us.

Steps to add "User Data":

1. Select to launch a new instance and follow all the steps above to set up the instance.
2. Before confirming and creating a new instance open `Advanced details` tab
3. Scroll to the very bottom of this tab and you will see a box that says `User data`
4. Write your script there and it will be executed when you click on `Launch instance`

_Please note! Ensure that your script is correct and there are no errors. Script will run only once when creating the instance. If there are any errors in your script it might not work and you will have to do installation manualy, or you will have to create a new instance!_ 
