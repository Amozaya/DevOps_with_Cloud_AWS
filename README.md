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
2. In the search bar type `EC2` and search for `EC2 Services`. Once you found it - click on it
3. In the new page search for a button called `Launch instance`. This button also has a dropdown menu where you can select to create a new instance or use the template. Currently, we are going to create a new one from scratch.
4. There are few settings we need to change before we create our instance:
   * Add the name of your instance. Ensure you are using the correct name convention
   * Select the OS for your VM. In our case we are using `Ubuntu Server 20.04 LTS (HVM), SSD Volume Type`
   * Select instance type. For our example default one is enough - `t2.micro`
   * Select your SSH key. Search for the key called `tech221` in the search bar and select the key
   * Now you need to edit security groups:
      * add the name and the description to your security group
      * set your SSH security group. Ensure that `Type` is set to `ssh` and `Source Type` is set to `My IP`
      * Add new security rule by clicking on `Add security group rule`
      * set your HTTP security group. Ensure that `Type` is set to `HTTP` and `Source Type` is set to `Anywhere`
   * Rest of the settings you can leave be default for now. Then head to `Summary` to verify everything and then click on `Launch Instance` to start your VM
