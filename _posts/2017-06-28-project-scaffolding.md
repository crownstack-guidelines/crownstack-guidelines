Welcome to the Project-Scaffolding wiki!

Project Scaffolding provides you an ecosystem for Small to Large Teams working on a project. Here at crownstack, we help you kickstart new projects, prescribing best practices and tools to stay productive. To Generate an ecosystem that puts Developers, System Administrator, and Functional teams in a roof, This Blog will tell you how to scaffold your whole project with few command execution. We know the importance of Scalability, High Availability, Resilient, Optimization factors.

### Table of Contents
1) [Steps involved in Project Scaffolding](#step-involved-in-project-scaffolding) 
2) [Server Setup and Configuration](#server-setup-and-configuration)
3) [Docker for Containerization](#docker-with-containerization)
4) [Dependency Resolution with Composer](#dependency-resolution-with-composer)
5) [Setup Version Control System](#setup-version-control-system)
6) [CICD Pipeline with Jenkins](#cicd=pipeline-with-jenkins)
7) [File System Setup](#file-system-setup)
8) [Complete Documentation and Test Report](#complete-documentation-and-test-report)
9) [Create Workbook](#create-workbook)

### Step Involved in Project Scaffolding
1. The **First step** towards project scaffolding is to setup Development, Stagging(Testing or Pre-Production), Production Server. The best analogy to setup these server using Configuration Management Tool (Puppet, Chef, Salt, Ansible). 

2. The **Second step** is to set up a Version Control System(VCS) like Github, Bitbucket, Tortoise svn. Create a Repository and Then Create Branches for production(Master Branch) and Development(Devel Branch). In Devel Branch create sub-branches for developers to the add new features and core libs. The project lead will merge those branches after reviewing and will resolve merge conflicts with team collaboration. When a merge to develop branch is made. The CI/CD Server will generate a build and will Run test cases, Linters and Coding Standard Sniffer. To Validate, verify and deploy the Project to the Development server and Then is build is stable will move it to Stagging sever. 

3. The **Third Step** is to integrate a Service and Webhook with CI/CD Server. Go to Settings of our Github repository and integrate a service, Jenkins. And Create a Webhook with `http://IP:PORT/github-webhook`. This will trigger build on push or pooling on develop branch.

4. The **Fourth Step** involves the Directory structure of your project. 

     ![file System](http://www.imageno.com/thumbs/20170622/mb1o7h3m4bhz.jpg)    


5. The Fifth Step needs to test your code and is standard. Also write unit test case relevant to your Programming Language. Postman Testcases(Collection URL), Report of project deployment and third-party libraries used.

6. The **Final Step** is to create a workbook for your project. Which means you need to cover every aspect of your project workflow and life cycle. Every phase of your project cycle from requirement gathering to deployment need to be covered in a workbook. 

### Server Setup and Configuration

You need to setup Development, Stagging, Production server. These servers have different roles in Project Management. 
Provisioning server on the cloud is effective as you can scale up and down depends on the resource usage. There are various companies providing reliable web services like AWS(Amazon Web Services), GCP(Google Compute Engine), Windows Azure. You can provision server manually as well as automatically using SDK(Software Development Kit). 

Install Puppet to install and configure tools required to run your project. We have Puppet Master which will install packages as requested. We have grouped the packages. Find the suitable script and install it.

    yum install puppet (For RHEL & CentOS)
    or
    apt-get install puppet (For Ubuntu and Debian)

Next, you need to execute puppet for installing packages from Puppetmaster.

### Docker for Containerization

Continuous integration and continuous deployment (CI/CD) are some of the most common, but impactful use cases for teams who are looking to Dockerize their environment. The key to CI/CD is being able to automate the workflow, while still keeping the necessary features in place (like performing tests and leveraging staging environments) to assure the quality of your applications.
![Image Credit Docker.coom](http://img.scoop.it/b6ZmkdGnwN24jGgg74YfjLnTzqrqzN7Y9aBZTaXoQ8Q=)
> Image Credit: Docker.com

### Dependency Resolution with Composer

Managing your dependencies manually in any programming language is a huge pain. This is why in most programming languages today you will find that they all have some implementation of a dependency management system or sometimes a package manager. The composer is the dependency management system that you will find on most modern PHP projects.
The composer is not a package manager. It deals with packages but in a “per project” way. While it provides a global installation option, it does not install anything globally by default.
Essentially, Composer allows you to declare and manage every dependency of your PHP projects. 
    
    {
	"description": "The CodeIgniter framework",
	"name": "codeigniter/framework",
	"type": "project",
	"homepage": "https://codeigniter.com",
	"license": "MIT",
	"support": {
		"forum": "http://forum.codeigniter.com/",
		"wiki": "https://github.com/bcit-ci/CodeIgniter/wiki",
		"irc": "irc://irc.freenode.net/codeigniter",
		"source": "https://github.com/bcit-ci/CodeIgniter"
	},
	"require": {
		"php": ">=5.2.4"
	},
	"suggest": {
		"paragonie/random_compat": "Provides better randomness in PHP 5.x"
	},
	"require-dev": {
		"mikey179/vfsStream": "1.1.*",
		"phpunit/phpunit": "4.* || 5.*"
	}
    }

### Setup Version Control System

Version control systems are a category of software tools that help a software team manage changes to source code over time. Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.

[Find more on Local VCS, Centralized VCS, Distributed VCS](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

[Understand Git Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)

To Learn Git, The best way is to use the manual of Git from Command Line.

    git branch --help

This is open the HTML page for Git branch. It contains all flags with description and tries out those commands, Learning by Doing.  

### CICD Pipeline with Jenkins

Jenkins is a self-contained, open source automation server which can be used to automate all sorts of tasks such as building, testing, and deploying software. Jenkins can be installed through native system packages, Docker, or even run standalone by any machine with the Java Runtime Environment installed.

[Read Continuous Integration with Jenkins](https://techbeacon.com/beginners-guide-kick-starting-your-ci-pipeline-jenkins)

[Read Continuous Delivery with Jenkins Workflow](https://dzone.com/refcardz/continuous-delivery-with-jenkins-workflow)

**Install Jenkins on CentOS 7**
* First Install EPEL Repositories and Update System
   
    `sudo yum install epel-release`

    `sudo yum update`

    `sudo reboot`

* Install Java

    `sudo yum install java-1.8.0-openjdk.x86_64`

* Set Environment variables for Java

   ` sudo cp /etc/profile /etc/profile_backup`

   ` echo 'export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk' | sudo tee -a /etc/profile`

   ` echo 'export JRE_HOME=/usr/lib/jvm/jre' | sudo tee -a /etc/profile`

    `source /etc/profile`

* Install Jenkins

    `cd ~`

    `sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo`

    `sudo rpm --import http://pkg.jenkins-ci.org/redhat-stable/jenkins-ci.org.key`

    `sudo yum install jenkins `

* Start Jenkins Service and Put in Startup

    `sudo systemctl start jenkins.service`

    `sudo systemctl enable jenkins.service`

### FileSystem Setup

File System plays a major role in managing your code and building scalable projects. read CodeIngiter HMVC design pattern to know the importance of Hierarchical Model view Controller uses Filesystem to organize code.

[Read CodeIngiter Playbook HMVC ](https://github.com/Gautam-S04/CodeIgniter-Playbook/wiki/HMVC-Extension-for-CodeIgniter)
 
### Complete Documentation and Test Report

You need to follow OpenAPI specification while writing Docs in your Code. Documentation will be created from your code. And Then you can use any tool like Swagger, Postman and Other to give a View to your API Specification.
Write Unit test cases for your feature branch. Each developer is responsible for its test case. Also, you need to commit your code with a relevant message. From your commits changelog will be generated. 

You Need Not to install swagger and configure it. Put in the directory and do all those extra stuff. You need to specify it in Puppet script. And Puppet will take care of install and configure those setups.

[Read OpenAPI Specification](https://github.com/OAI/OpenAPI-Specification)

**Sample PHPUnit Test case:**

    <?php
	use PHPUnit\Framework\TestCase;
	require_once('config/config.php');
	/**
	* Class Helpers Stores all the Methods that need to be called for almost each endpoints with different parameter
	* The Result returned by the methods of Helpers with be asserted by endpoint class Method
	*/
	# Its better to divide function for Different Request type
	class Helper 
	{
		var $info = array();
		# Create class variables here
		public function checkHTTPStatus($url)
		{
			# First Create CURL Header and Intialize it
			$ch = curl_init();
			curl_setopt($ch,CURLOPT_RETURNTRANSFER,1);
			curl_setopt($ch,CURLOPT_URL,$url);
			curl_exec($ch);
			$this->info = curl_getinfo($ch);
			return intval($this->info['http_code']);
		}
		# Now Check Content Type of Each endpoint and Also Content-Length(Optional)
		public function checkHTTPType()
		{		
			return $this->info['content_type'];
		}
	}
	class EndPoints extends TestCase
	{
		 # create an instance of helper class
		 # Remember you cannot initiate a class outside of a function. that due to scope restriction in php 
		 private $systemc;
		 public function testRest()
 		 {
			$this->systemc = new Helper;
			# read the Endpoint file and check 
			# here just a sample
			# Check Login
			 $this->assertEquals(200,$this->systemc->checkHTTPStatus(URL));
			 $this->assertEquals('text/html; charset=UTF-8',$this->systemc->checkHTTPType());
	                 $this->assertEquals(200,$this->systemc->checkHTTPStatus(URL.'/login'));
                         $this->assertEquals(200,$this->systemc->checkHTTPStatus(URL.'/register'));
		 }
	}
    ?>

### Create Workbook

You need to put details in the workbook of each stage involved in Project Life Cycle. 

To Understand how project lifecycle works:

[Read Demystifying the 5  Phases of Project Management](https://www.smartsheet.com/demystifying-5-phases-project-management-b)
