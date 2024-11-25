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

#### Questions 
1. How to increase the Build speed?
2. How to minimize the Build Image size? Because buildpacks image sizes are in general large. 
3. How to make Build process reliable?
4. What are the various options? 
