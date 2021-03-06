# Elastic Beanstalk Supported Platforms<a name="concepts.platforms"></a>

AWS Elastic Beanstalk provides platforms for programming languages \(Java, PHP, Python, Ruby, Go\), web containers \(Tomcat, Passenger, Puma\) and Docker containers, with multiple configurations of each\.

Elastic Beanstalk provisions the resources needed to run your application, including one or more Amazon EC2 instances\. The software stack running on the Amazon EC2 instances depends on the configuration\. In a configuration name, the version number refers to the version of the platform configuration\.

You can use the solution stack name listed under the configuration name to launch an environment with the EB CLI, [Elastic Beanstalk API](http://docs.aws.amazon.com/elasticbeanstalk/latest/api/), or [AWS CLI](https://aws.amazon.com/cli/)\. You can also retrieve solution stack names from the service with the [ListAvailableSolutionStacks](http://docs.aws.amazon.com/elasticbeanstalk/latest/api/API_ListAvailableSolutionStacks.html) API \([aws elasticbeanstalk list\-available\-solution\-stacks](http://docs.aws.amazon.com/cli/latest/reference/elasticbeanstalk/list-available-solution-stacks.html) in the AWS CLI\)\. This operation returns all of the solution stacks that you can use to create an environment\.

**Note**  
You can use solution stacks for the latest platform configurations \(the current versions listed on this page\) to create an environment\.  
In addition, a platform configuration that you used to launch or update an environment remains available \(to the account in use, in the region used\) even after it's no longer current, as long as the environment is active, and up to 30 days after its termination\.

All current Linux\-based platform configurations run on Amazon Linux 2017\.09 \(64\-bit\)\. You can customize and configure the software that your application depends on in your Linux platform\. Learn more at [Customizing Software on Linux Servers](customize-containers-ec2.md)\. Detailed release notes are available for recent releases at [aws\.amazon\.com/releasenotes](https://aws.amazon.com/releasenotes/AWS-Elastic-Beanstalk)\. 


+ [Packer Builder](#concepts.platforms.packer)
+ [Single Container Docker](#concepts.platforms.docker)
+ [Multicontainer Docker](#concepts.platforms.mcdocker)
+ [Preconfigured Docker](#concepts.platforms.dockerpreconfig)
+ [Go](#concepts.platforms.go)
+ [Java SE](#concepts.platforms.javase)
+ [Java with Tomcat](#concepts.platforms.java)
+ [\.NET on Windows Server with IIS](#concepts.platforms.net)
+ [Node\.js](#concepts.platforms.nodejs)
+ [PHP](#concepts.platforms.PHP)
+ [Python](#concepts.platforms.python)
+ [Ruby](#concepts.platforms.ruby)

## Packer Builder<a name="concepts.platforms.packer"></a>

Packer is an open\-source tool for creating machine images for many platforms, including AMIs for use with Amazon EC2\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Packer Version  | 
| --- | --- | --- | 
|   **Elastic Beanstalk Packer Builder version 2\.4\.4**   *64bit Amazon Linux 2017\.09 v2\.4\.4 running Packer 1\.0\.3*   |  2017\.09\.1  |  1\.0\.3  | 

For information about previous configurations, see \.

## Single Container Docker<a name="concepts.platforms.docker"></a>

Docker is a container platform that allows you to define your own software stack and store it in an image that can be downloaded from a remote repository\. Use the Single Container Docker platform if you only need to run a single Docker container on each instance in your environment\. The single container configuration includes an nginx proxy server\.

See  for more information about the Docker platform\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Docker Version  |  Proxy Server  | 
| --- | --- | --- | --- | 
|   **Single Container Docker 17\.09 version 2\.8\.4**   *64bit Amazon Linux 2017\.09 v2\.8\.4 running Docker 17\.09\.1\-ce*   |  2017\.09\.1  |  17\.09\.1\-ce  |  nginx 1\.12\.1  | 

For information about previous configurations, see \.

## Multicontainer Docker<a name="concepts.platforms.mcdocker"></a>

Docker is a container platform that allows you to define your own software stack and store it in an image that can be downloaded from a remote repository\. Use the Multicontainer Docker platform if you need to run multiple containers on each instance\. The Multicontainer Docker platform does not include a proxy server\.

**Note**  
Elastic Beanstalk uses Amazon Elastic Container Service \(Amazon ECS\) to coordinate container deployments to multicontainer Docker environments\. Some regions don't offer Amazon ECS\. Multicontainer Docker isn't supported in these regions\.  
For information about the AWS services offered in each region, see [Region Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)\.

See  for more information about the Docker platform\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Docker Version  |  ECS Agent  | 
| --- | --- | --- | --- | 
|   **Multicontainer Docker 17\.09 version 2\.8\.4**   *64bit Amazon Linux 2017\.09 v2\.8\.4 running Multi\-container Docker 17\.09\.1\-ce \(Generic\)*   |  2017\.09\.1  |  17\.09\.1\-ce  |  1\.16\.1  | 

For information about previous configurations, see \.

## Preconfigured Docker<a name="concepts.platforms.dockerpreconfig"></a>

Preconfigured Docker platform configurations use Docker, but do not let you provide your own Docker images\. The preconfigured containers provide application frameworks that are not available on other platforms, such as Glassfish\. They also provide support for Go applications prior to the release of the full\-fledged Go platform\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Platform  |  Container OS  |  Language  |  Proxy Server  |  Application Server  |  Docker Image  | 
| --- | --- | --- | --- | --- | --- | --- | --- | 
|   **Glassfish 4\.1 \(Docker\) version 2\.8\.4**   *64bit Debian jessie v2\.8\.4 running GlassFish 4\.1 Java 8 \(Preconfigured \- Docker\)*   |  2017\.09\.1  |  Docker 17\.09\.1\-ce  |  Debian Jessie  |  Java 8  |  nginx 1\.12\.1  |  Glassfish 4\.1  |  amazon/aws\-eb\-glassfish:4\.1\-jdk8\-onbuild\-3\.5\.1  | 
|   **Glassfish 4\.0 \(Docker\) version 2\.8\.4**   *64bit Debian jessie v2\.8\.4 running GlassFish 4\.0 Java 7 \(Preconfigured \- Docker\)*   |  2017\.09\.1  |  Docker 17\.09\.1\-ce  |  Debian Jessie  |  Java 7  |  nginx 1\.12\.1  |  Glassfish 4\.0  |  amazon/aws\-eb\-glassfish:4\.0\-jdk7\-onbuild\-3\.5\.1  | 
|   **Go 1\.4 \(Docker\) version 2\.8\.4**   *64bit Debian jessie v2\.8\.4 running Go 1\.4 \(Preconfigured \- Docker\)*   |  2017\.09\.1  |  Docker 17\.09\.1\-ce  |  Debian Jessie  |  Go 1\.4\.2  |  nginx 1\.12\.1  |  none  |  golang:1\.4\.2\-onbuild  | 
|   **Go 1\.3 \(Docker\) version 2\.8\.4**   *64bit Debian jessie v2\.8\.4 running Go 1\.3 \(Preconfigured \- Docker\)*   |  2017\.09\.1  |  Docker 17\.09\.1\-ce  |  Debian Jessie  |  Go 1\.3\.3  |  nginx 1\.12\.1  |  none  |  golang:1\.3\.3\-onbuild  | 
|   **Python 3\.4 with uWSGI 2 \(Docker\) version 2\.8\.4**   *64bit Debian jessie v2\.8\.4 running Python 3\.4 \(Preconfigured \- Docker\)*   |  2017\.09\.1  |  Docker 17\.09\.1\-ce  |  Debian Jessie  |  Python 3\.4  |  nginx 1\.12\.1  |  uWSGI 2\.0\.8  |  amazon/aws\-eb\-python:3\.4\.2\-onbuild\-3\.5\.1  | 

For information about previous configurations, see \.

## Go<a name="concepts.platforms.go"></a>

Elastic Beanstalk supports the following Go configurations\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Language  |  Proxy Server  | 
| --- | --- | --- | --- | 
|   **Go 1\.9 version 2\.7\.5**   *64bit Amazon Linux 2017\.09 v2\.7\.5 running Go 1\.9*   |  2017\.09\.1  |  Go 1\.9\.1  |  nginx 1\.12\.1  | 

For information about previous configurations, see \.

## Java SE<a name="concepts.platforms.javase"></a>

Elastic Beanstalk supports the following Java SE configurations\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Language  |  Tools  |  AWS X‑Ray  |  Proxy Server  | 
| --- | --- | --- | --- | --- | --- | 
|   **Java 8 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running Java 8*   |  2017\.09\.1  |  Java 1\.8\.0\_151  |  Ant 1\.9\.6, Gradle 2\.7, Maven 3\.3\.3  |  2\.0\.0  |  nginx 1\.12\.1  | 
|   **Java 7 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running Java 7*   |  2017\.09\.1  |  Java 1\.7\.0\_161  |  Ant 1\.9\.6, Gradle 2\.7, Maven 3\.3\.3  |  2\.0\.0  |  nginx 1\.12\.1  | 

For information about previous configurations, see \.

## Java with Tomcat<a name="concepts.platforms.java"></a>

Elastic Beanstalk supports the following Tomcat configurations\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Language  |  AWS X‑Ray  |  Application Server  |  Proxy Server  | 
| --- | --- | --- | --- | --- | --- | 
|   **Java 8 with Tomcat 8 version 2\.7\.5**   *64bit Amazon Linux 2017\.09 v2\.7\.5 running Tomcat 8 Java 8*   |  2017\.09\.1  |  Java 1\.8\.0\_151  |  2\.0\.0  |  Tomcat 8\.0\.47  |  Apache 2\.2\.34  | 
|   **Java 7 with Tomcat 7 version 2\.7\.5**   *64bit Amazon Linux 2017\.09 v2\.7\.5 running Tomcat 7 Java 7*   |  2017\.09\.1  |  Java 1\.7\.0\_161  |  2\.0\.0  |  Tomcat 7\.0\.82  |  Apache 2\.2\.34  | 
|   **Java 6 with Tomcat 7 version 2\.7\.5**   *64bit Amazon Linux 2017\.09 v2\.7\.5 running Tomcat 7 Java 6*   |  2017\.09\.1  |  Java 1\.6\.0\_41  |  2\.0\.0  |  Tomcat 7\.0\.82  |  Apache 2\.2\.34  | 

For information about previous configurations, see \.

## \.NET on Windows Server with IIS<a name="concepts.platforms.net"></a>

You can get started in minutes using the [AWS Toolkit for Visual Studio](http://aws.amazon.com/visualstudio/)\. The toolkit includes the AWS libraries, project templates, code samples, and documentation\. The AWS SDK for \.NET supports the development of applications using \.NET Framework 2\.0 or later\. 

**Note**  
This platform does not support worker environments, enhanced health reporting, managed updates, bundle logs, immutable updates, or log streaming\.

To learn how to get started deploying a \.NET application using the AWS Toolkit for Visual Studio, see [Creating and Deploying Elastic Beanstalk Applications in \.NET Using AWS Toolkit for Visual Studio](create_deploy_NET.md)\.

For information about the latest Microsoft security updates, see [Security TechCenter](https://portal.msrc.microsoft.com/en-us/) and [Security Advisories and Bulletins](https://technet.microsoft.com/en-us/library/security/)\.

For information about previous \.NET configurations for Elastic Beanstalk, see \.

**Note**  
To use the C5 instance type family, choose Windows Server 2012 R2 or newer\.

Elastic Beanstalk supports the following \.NET configurations\.

### Configuration basics<a name="concepts.platforms.net.basics"></a>


****  

|  Configuration  |  Solution Stack Name  |  Framework  |  Proxy Server  | 
| --- | --- | --- | --- | 
|   **Windows Server 2016 with IIS 10\.0 version 1\.2\.0**   |   *64bit Windows Server 2016 v1\.2\.0 running IIS 10\.0*   |  \.NET Core 2\.0, supports 2\.0\.x, 1\.1\.x, 1\.0\.x \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 10\.0  | 
|   **Windows Server Core 2016 with IIS 10\.0 version 1\.2\.0**   |   *64bit Windows Server Core 2016 v1\.2\.0 running IIS 10\.0*   |  \.NET Core 2\.0, supports 2\.0\.x, 1\.1\.x, 1\.0\.x \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 10\.0  | 
|   **Windows Server 2012 R2 with IIS 8\.5 version 1\.2\.0**   |   *64bit Windows Server 2012 R2 v1\.2\.0 running IIS 8\.5*   |  \.NET Core 2\.0, supports 2\.0\.x, 1\.1\.x, 1\.0\.x \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 8\.5  | 
|   **Windows Server 2012 R2 Server Core with IIS 8\.5 version 1\.2\.0**   |   *64bit Windows Server Core 2012 R2 v1\.2\.0 running IIS 8\.5*   |  \.NET Core 2\.0, supports 2\.0\.x, 1\.1\.x, 1\.0\.x \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 8\.5  | 
|   **Windows Server 2012 with IIS 8 version 1\.2\.0**   |   *64bit Windows Server 2012 v1\.2\.0 running IIS 8*   |  \.NET Core 2\.0, supports 2\.0\.x, 1\.1\.x, 1\.0\.x \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 8  | 
|   **Windows Server 2008 R2 with IIS 7\.5 version 1\.2\.0**   |   *64bit Windows Server 2008 R2 v1\.2\.0 running IIS 7\.5*   |  \.NET Core 2\.0, supports 2\.0\.x, 1\.1\.x, 1\.0\.x \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 7\.5  | 
|   **Windows Server 2012 R2 with IIS 8\.5**   |   *64bit Windows Server 2012 R2 running IIS 8\.5*   |  \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 8\.5  | 
|   **Windows Server 2012 R2 Server Core with IIS 8\.5**   |   *64bit Windows Server Core 2012 R2 running IIS 8\.5*   |  \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 8\.5  | 
|   **Windows Server 2012 with IIS 8**   |   *64bit Windows Server 2012 running IIS 8*   |  \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 8  | 
|   **Windows Server 2008 R2 with IIS 7\.5**   |   *64bit Windows Server 2008 R2 running IIS 7\.5*   |  \.NET Framework 4\.7, supports 4\.x, 2\.0, 1\.x  |  IIS 7\.5  | 

### More details<a name="concepts.platforms.net.details"></a>


****  

|  Configuration  |  AMI version  |  AWS SDK for \.NET  |  EC2Config  |  SSM Agent  |  Web Deploy  |  AWS X‑Ray  | 
| --- | --- | --- | --- | --- | --- | --- | 
|   **Windows Server 2016 with IIS 10\.0 version 1\.2\.0**   |  2018\.01\.05  |  3\.15\.304\.0  |   * [SSM only](http://docs.aws.amazon.com/systems-manager/latest/userguide/) *   |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server Core 2016 with IIS 10\.0 version 1\.2\.0**   |  2018\.01\.05  |  3\.15\.304\.0  |   * [SSM only](http://docs.aws.amazon.com/systems-manager/latest/userguide/) *   |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2012 R2 with IIS 8\.5 version 1\.2\.0**   |  2018\.01\.05  |  3\.15\.304\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2012 R2 Server Core with IIS 8\.5 version 1\.2\.0**   |  2018\.01\.05  |  3\.15\.304\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2012 with IIS 8 version 1\.2\.0**   |  2017\.12\.13  |  3\.15\.277\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2008 R2 with IIS 7\.5 version 1\.2\.0**   |  2018\.01\.05  |  3\.15\.304\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2012 R2 with IIS 8\.5**   |  2018\.01\.05  |  3\.15\.304\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2012 R2 Server Core with IIS 8\.5**   |  2018\.01\.05  |  3\.15\.304\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2012 with IIS 8**   |  2017\.12\.13  |  3\.15\.277\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 
|   **Windows Server 2008 R2 with IIS 7\.5**   |  2018\.01\.05  |  3\.15\.304\.0  |  4\.9\.2262\.0  |  2\.2\.93\.0  |  3\.6  |  1\.0\.0  | 

## Node\.js<a name="concepts.platforms.nodejs"></a>

The Node\.js platform includes a few Node\.js versions in a single configuration\. The following table lists them\. The default version applies when the NodeVersion option in the `aws:elasticbeanstalk:container:nodejs` namespace isn't set\. See [Node\.js Platform Options](command-options-specific.md#command-options-nodejs) for details\.

Each Node\.js version includes a respective version of npm \(the Node\.js package manager\)\. The table lists npm versions in parentheses\.

Elastic Beanstalk supports the following Node\.js configurations\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Node\.js version \(npm version\)  |  Proxy Server  |  Git  |  AWS X‑Ray  | 
| --- | --- | --- | --- | --- | --- | 
|   **Node\.js version 4\.4\.4**   *64bit Amazon Linux 2017\.09 v4\.4\.4 running Node\.js*   |  2017\.09\.1  |  8\.9\.3 \(5\.5\.1\), 8\.8\.1 \(5\.4\.2\), 7\.10\.1 \(4\.2\.0\), 6\.12\.2 \(3\.10\.10\), 6\.11\.5 \(3\.10\.10\), 5\.12\.0 \(3\.8\.6\), 4\.8\.7 \(2\.15\.11\), 4\.8\.5 \(2\.15\.11\)  Default platform: 6\.11\.5  |  nginx 1\.12\.1, Apache 2\.4\.27  |  2\.13\.6  |  2\.0\.0  | 

For information about previous configurations, see \.

**Note**  
When support for the version of Node\.js that you are using is removed from the platform configuration, you must change or remove the version setting prior to doing a platform upgrade\. This may occur when a security vulnerability is identified for one or more versions of Node\.js  
When this occurs, attempting to upgrade to a new version of the platform that does not support the configured NodeVersion will fail\. To avoid needing to create a new environment, change the *NodeVersion* configuration option to a version that is supported by both the old configuration version and the new one, or remove the option setting, and then perform the platform upgrade\.

## PHP<a name="concepts.platforms.PHP"></a>

Elastic Beanstalk supports the following PHP configurations\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Language  |  Composer  |  Proxy Server  | 
| --- | --- | --- | --- | --- | 
|   **PHP 7\.1 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running PHP 7\.1*   |  2017\.09\.1  |  PHP 7\.1\.11  |  1\.4\.2  |  Apache 2\.4\.27  | 
|   **PHP 7\.0 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running PHP 7\.0*   |  2017\.09\.1  |  PHP 7\.0\.25  |  1\.4\.2  |  Apache 2\.4\.27  | 
|   **PHP 5\.6 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running PHP 5\.6*   |  2017\.09\.1  |  PHP 5\.6\.32  |  1\.4\.2  |  Apache 2\.4\.27  | 
|   **PHP 5\.5 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running PHP 5\.5*   |  2017\.09\.1  |  PHP 5\.5\.38  |  1\.4\.2  |  Apache 2\.4\.27  | 
|   **PHP 5\.4 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running PHP 5\.4*   |  2017\.09\.1  |  PHP 5\.4\.45  |  1\.4\.2  |  Apache 2\.4\.27  | 

For information about previous configurations, see \.

## Python<a name="concepts.platforms.python"></a>

Elastic Beanstalk supports the following Python configurations\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Language  |  Package Manager  |  Packager  |  meld3  |  AWS X‑Ray  |  Proxy Server  | 
| --- | --- | --- | --- | --- | --- | --- | --- | 
|   **Python 3\.6 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running Python 3\.6*   |  2017\.09\.1  |  Python 3\.6\.2  |  pip 9\.0\.1  |  setuptools 28\.8\.0  |  meld3 1\.0\.2  |  2\.0\.0  |  Apache 2\.4\.27 with mod\_wsgi 3\.5  | 
|   **Python 3\.4 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running Python 3\.4*   |  2017\.09\.1  |  Python 3\.4\.3  |  pip 9\.0\.1  |  setuptools 28\.8\.0  |  meld3 1\.0\.2  |  2\.0\.0  |  Apache 2\.4\.27 with mod\_wsgi 3\.5  | 
|   **Python 2\.7 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running Python 2\.7*   |  2017\.09\.1  |  Python 2\.7\.12  |  pip 9\.0\.1  |  setuptools 28\.8\.0  |  meld3 1\.0\.2  |  2\.0\.0  |  Apache 2\.4\.27 with mod\_wsgi 3\.5  | 
|   **Python 2\.6 version 2\.6\.4**   *64bit Amazon Linux 2017\.09 v2\.6\.4 running Python 2\.6*   |  2017\.09\.1  |  Python 2\.6\.9  |  pip 9\.0\.1  |  setuptools 28\.8\.0  |  meld3 1\.0\.2  |  2\.0\.0  |  Apache 2\.4\.27 with mod\_wsgi 3\.5  | 

For information about previous configurations, see \.

## Ruby<a name="concepts.platforms.ruby"></a>

Elastic Beanstalk supports the following Ruby configurations\.


****  

|  Configuration and *Solution Stack Name*   |  AMI  |  Language  |  Package Manager  |  Application Server  |  Proxy Server  | 
| --- | --- | --- | --- | --- | --- | 
|   **Ruby 2\.4 with Puma version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.4 \(Puma\)*   |  2017\.09\.1  |  Ruby 2\.4\.3\-p205  |  RubyGems 2\.7\.3  |  Puma 2\.16\.0  |  nginx 1\.12\.1  | 
|   **Ruby 2\.4 with Passenger version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.4 \(Passenger Standalone\)*   |  2017\.09\.1  |  Ruby 2\.4\.3\-p205  |  RubyGems 2\.7\.3  |  Passenger 4\.0\.60  |  nginx 1\.12\.1  | 
|   **Ruby 2\.3 with Puma version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.3 \(Puma\)*   |  2017\.09\.1  |  Ruby 2\.3\.6\-p384  |  RubyGems 2\.7\.3  |  Puma 2\.16\.0  |  nginx 1\.12\.1  | 
|   **Ruby 2\.3 with Passenger version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.3 \(Passenger Standalone\)*   |  2017\.09\.1  |  Ruby 2\.3\.6\-p384  |  RubyGems 2\.7\.3  |  Passenger 4\.0\.60  |  nginx 1\.12\.1  | 
|   **Ruby 2\.2 with Puma version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.2 \(Puma\)*   |  2017\.09\.1  |  Ruby 2\.2\.9\-p480  |  RubyGems 2\.7\.3  |  Puma 2\.16\.0  |  nginx 1\.12\.1  | 
|   **Ruby 2\.2 with Passenger version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.2 \(Passenger Standalone\)*   |  2017\.09\.1  |  Ruby 2\.2\.9\-p480  |  RubyGems 2\.7\.3  |  Passenger 4\.0\.60  |  nginx 1\.12\.1  | 
|   **Ruby 2\.1 with Puma version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.1 \(Puma\)*   |  2017\.09\.1  |  Ruby 2\.1\.10\-p492  |  RubyGems 2\.6\.13  |  Puma 2\.16\.0  |  nginx 1\.12\.1  | 
|   **Ruby 2\.1 with Passenger version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.1 \(Passenger Standalone\)*   |  2017\.09\.1  |  Ruby 2\.1\.10\-p492  |  RubyGems 2\.6\.13  |  Passenger 4\.0\.60  |  nginx 1\.12\.1  | 
|   **Ruby 2\.0 with Puma version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.0 \(Puma\)*   |  2017\.09\.1  |  Ruby 2\.0\.0\-p648  |  RubyGems 2\.6\.13  |  Puma 2\.16\.0  |  nginx 1\.12\.1  | 
|   **Ruby 2\.0 with Passenger version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 2\.0 \(Passenger Standalone\)*   |  2017\.09\.1  |  Ruby 2\.0\.0\-p648  |  RubyGems 2\.6\.13  |  Passenger 4\.0\.60  |  nginx 1\.12\.1  | 
|   **Ruby 1\.9 with Passenger version 2\.6\.5**   *64bit Amazon Linux 2017\.09 v2\.6\.5 running Ruby 1\.9\.3*   |  2017\.09\.1  |  Ruby 1\.9\.3\-p551  |  RubyGems 2\.6\.13  |  Passenger 4\.0\.60  |  nginx 1\.12\.1  | 

For information about previous configurations, see \.