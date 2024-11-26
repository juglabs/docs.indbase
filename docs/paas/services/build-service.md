# Build Service

## Different Build Options

### Buildpacks
Today 25-11-2024, tried buildpacks - Software that transforms the application source code into runnable artifacts by analyzing the code and determining the best way to build it. 

You need to select the optimum "builder" to build the image - available options include Paketo Buildpacks, Google Cloud buildpacks, Heroku Buildpacks, Cloud Foundry etc. 

**Paketo Buildpacks** led to error realted to Node.js version. Even with error, it took some **5 minutes** to build and throw error. 

Then used **Google Cloud Buildpacks** - it worked ust fine with around **6 minutes** time from build command to successful image build. 6 minutes is quite a lot in todays time. 
(Guess it obviously depends on the Server configs - the case above being Macbook Air with M2 processor) 

We are talking of the order of seconds. Your end to end deployment - from selecting Git Repo to deployment- should be done say within 2 minutes. That marks a significant improvement in the 
customer user experience vis-a-vis verce, netlify, heroku etc. Fly.io comes close. The aim is to beat all of them. World Class should mean that. You should be the best in the business.

|**Builder**      |Base OS|Supported languages|Use case                    |
|-----------------|-------|-------------------|----------------------------|
|Paketo Buildpacks|Ubuntu |Wide variety       |General Purpose, ligthweight|
|Google Cloud Bldp|Debain | Java, Node, Go etc| Optimized for GCP          |
|Heroku Buildpacks|Ubuntu |Heroku supp lang   | Heroku apps, simplicity    |
|Cloud Foundry    |Ubuntu |Java, PHP, Go etc  | Clodu Foundry compatibility|
|Red Hat UBI Bldp | RHEL  | Enterprise grade  | Openshift, enterprise env  |

Interestingly, Fly.io does little differently. They do images but not Docker! They unwrap image layer by layer while running container- something of that sort?

Fly.io's build service works like this:

1. First it checks if there is a Dockerfile along with the code, so that image can be built right away without the help of Buildpacks
2. If no Dockerfile present, Buildpacks takes over and auto scans the code, detect language and framework, download the dependencies, build image 
3. If readily built image is provided, then its used to deploy the application.

In the interest of time and to avoid depending on external software like Buildpacks to build the application, it's wiser to write your own auto scan code -> prepare Dockerfile -> Build image. 

And it's not that complicated. Just scan for the relevant config files like **package.json (react), gemfile(Ruby), index.js or app.js(react), requirements.txt (Python), composer.json(for PHP/Laravel/Symfony), pom.xml or build.gradle (Java), packages.config (.NET)** etc

#### Questions 
1. How to increase the Build speed?
2. How to minimize the Build Image size? Because buildpacks image sizes are in general large. 
3. How to make Build process reliable?
4. What are the various options?
5. How to manage secrets during image build?
6. How to add Volumes, Databases, Storage to the app? 
