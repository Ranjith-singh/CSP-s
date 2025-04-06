Budget :
    setting up budget for the amount utilization
    setting sqs and emails based on the threshold value of the budget
    setting action based on the threshold value like lower ec2 size etc

Billing :
    cloudWatch :
        setting up absolute or relative threshold value for which the sqs and emails will be sent
        create a topic through which sqs will be sent to all subscribers

MFA (multiFactorAuthentication) :
    setting up signin through authenticator codes
    can signin through a hardware device or codes sent to mobiles

Evolution of computing :
    General computing :
        uses xeon processors
        aws ec2
    graphical computing :
        50 times faster than regular cpu's
        aws inferentiare(inf1)
    quantum computing :
        100 million times faster then regular cpu
        rigetti 16q aspen-4

Aws global infrastructure :
    aws regions :
        32 regions around the world
        each region mostly has 3 AZ
        aws Availability Zones(Az) :
            each az has multiple data center
            az's are within 100 km range
            services are deployed in multiple az's to make fault tolerant
    Aws global network acts as a interconnection b/w aws global infrastructure
    edge locations are used for these
    use cases are aws global accelerator, aws s3 transfer accelerator for on ramps
    cloudfront off ramps

point of preference :
    intermediate location b/w regions and end users
    caching :
        edge location : most recently access data
        regional edge location : least recently access data
    aws az's are redundantly connected to tear 1 network
    cloudfront :
        content delivery networks service
    aws global accelerator
    aws s3 transfer

Direct connect :
    private/dedicated connect b/w your datacenter,office,co-location(space for rental) and Aws
    lower bandwidth 50-500 mbps
    high bandwidth 1-10 gbps

local zones :
    Data centers located near densely populated areas for low latency
    ex : multi media, machine learning

aws wavelength zones : 
    edge computing on 5g networks

data residency :
    the location where an organization or cloud resources reside
    aws outpost
    aws config
    IAM polices

aws for government :
    public sector :
        public goods and governmental services
    meeting there regulatory compliance programs
    aws has special regions for us regulations called gov cloud

gov cloud :
    csp for fedRAMP workloads
    federal risk and authorization management program (FedRAMP)
        rules to be followed by csp's

aws china :
    https://www.amazonaws.cn/en/about-aws/china

aws sustainability
aws ground station :
    control satellite communications
    download image from satellite to s3 buckets using ec2 AMI

aws outposts :
    placed inside the rack frame that provides aws services
    42 u (full rack)
    1u
    2u

solutions Architect :
    role in a technical organization provides technical solution using researching,
    documentation, experimentation.

    Availability
        no single point failure
        elastic load balancer
        s3 auto configure and ec2 doesn't auto configure
        rds and elastic beanstock select option
    Scalability
        vertical scaling
        horizontal scaling
    Elasticity
        automatic scaling
        auto scaling groups
    Fault Tolerance
        no single point failure
        fail-overs
        RDS multi-AZ
    Disaster Recovery
        cloudEndure disaster recovery
            recovery incase of IT data centre fails

Disaster Recovery :
    business continuity plan :
        business continuity in case of disaster
        RecoveryPointObjective(RPO) 
        RecoveryTimeObjective(RTO)
    disaster recovery options :
        backup & restore
        pilot Light :
            core services running
        warm standby :
            scaling down resources
        multi-site Active :
            copy of your original infrastructure

traditional architecture :
    starts from Ec2 instance :
        store parameters in parameters store and config
        covers the ec2 instance under auto scaling groups
    database :
        database creds in secrets manager
        data in rds
    s3 buckets :
        bootstrap data in s3 buckets
        application related data and information data
    build and deploy code :
        replace old environment with the new one
    Application load balancer :
        create web servers based on the load providers
    create a launch template for the ec2 instance
    AMI(Amazon machine image) is created automatically for the launch template
    AMI is build using the ssm automation document

Aws Api :
    Aws Api is Https
    each service has its own endpoint
    cloud watch :
        monitoring.us-east-1.amazon.com
    need to send authorization token with each http request
    we don't directly use aws api instead we use :
        aws management console
        aws sdk
        aws cli
    postman can be used to send diff requests

Aws Management Console :
    build and manage aws services through clicks

service console :
    service dashboard
    some are umbrella console contains multi services

Aws account ID :
    login
    support
    cross-account roles, polices and security

Aws Tools for powershell :
    interact with aws api with cmdlets like New-S3Bucket
    usage :
        shift to pwsh for powershell
        install the installer for aws tools
        specify the services for which you need aws tools

Amazon Resource Name (ARNs) :
    Uniquely specify a aws resource
    to address all the things in arn path specify *
    usage :
        i am polices to specify permissions to a resource inside a service

aws cli :
    interact to aws api's
    requires python library
    you can also use github/io in gitpod to interact with aws api's :
        we need to install aws in that
        we need to configure account info with access key
        specify multiple accounts in the configure file

note :
    when you need an example go to reference
    use nano instead of vi to specify options

aws sdk :
    programmatic way to manage aws services and write code for development through programming language like java, ruby etc
    cloud 9:
        provides an editor to work with aws resources
        usage :
            place all the installation in gemfile
            install through commands
            specify the resources you wanna work with
            use pry to work with resources configured in the code
            configure env's in the aws.config

aws cloud shell :
    managing aws resources
    region specific
    preinstalled tools like python, pip etc
    terminal : bash, powershell
    1 Gb storage

aws infrastructure as code(IAC) :
    we provide configuration scripts for the cloud infrastructure

    cloud formation :
        we provide scripts for infrastructure
        descriptive : we get what we provide
        usage :
            configure a template yml file :
                specify the version deployed
                under resources specify the configuration of resource like adding a s3 bucket
                under output specify the location of s3 created getatt : s3Name
            run the file
    
    cloud development kit(cdk) :
        we use programming language for infrastructure
        some of the auto configured beside what you provide
        it uses cloud formation behind the scene
        it is product of cloud formation
        usage :
            create a stack in cloud 9
            configure the programming language you wanna work with
            write the code like creating a sqs and sns with topic
            run cdk deploy to run your file and cdk destroy to destroy the resource created
            note : diff b/w aws cdk and sdk is cdk can specify the vm's to be used

aws toolkit for Vscode :
    configure aws tools plugin into your vscode
    aws explorer
    aws cdk explorer : view stacks created
    aws also provides extension for auto complete and run configuration

aws access key :
    access key is used work with aws api to access aws resources
    we can create one or more access keys for the user
    we keep these access keys generally in ~/.aws/configurer.yml file

Aws documentation :
    provides a technical way to interact with aws services
    for each service you ca get a github/html/txt iew

shared responsibility model :
    security responsibilities shared b/w user and aws
    aws responsible for the security of the cloud (hardware)
    user is responsible for the security in the cloud (software)
    ![alt text][SharedResponsibiltyModel]
    split based o service :
        on premise
        iaas
        paas : take care of only application and data
        saas : take care of everything : msword
    based on compute :
        iaas :
            ec2 bare metal instance :
                user :
                    host os configuration
                    hypervisor
                aws :
                    physical machine
            virtual machine ec2 :
                user : 
                    guest os
                    containers runtime: dockers
                aws :
                    hypervisor, host os and physical machine
            containers :
                user :
                    configuration, deployment and storage of containers
                aws :
                    os, hypervisor, containers runtime and physical machine
        paas :
            aws elastic beanstalk :
                user :
                    upload code
                    configuration of env and services
                aws :
                    os, containers, storage, servers
        saas :
            amazon workDocs :
                similar to ms word :
                    user :
                        content
                        management of files
                        shared access
        Faas (function as a service) :
            aws lambda :
                user :
                    upload code
                aws :
                    rest everything
        
computing services :
    elastic compute cloud (ec2):
        highly configurable server choose Ami that effects :
            processor
            ram
        Ami is a configuration for virtual machine
        launch a vm
        virtual machine (vm) :
            emulation of physical computer using software
            server virtualization : create, modify and destroy servers
            multiple vm's can be launched in a physical server
    types :
        amazon lightsail : 
            friendly version of ec2
            managed virtual server service (No Ami)
        containers :
        virtualizing a os to run multiple os instance.
        generally used in microservice architecture
        types :
            ECS(Elastic container service) :
                run and manage a docker image in the docker container
                Launches cluster of servers that run on ec2
                provide the number os servers to ec2 and a docker image
            ECR(Elastic container Registry) :
                repo of images
            EcS fargate : 
                serverless
                pay on demand
            EKS(K-kubernatives) :
                manage microservice based architecture
        serverless :
            when the underlying servers are managed by aws
            you don't configure the servers
            Aws Lambda :
                only write or upload code
    
high performance computing services :
    100's of servers with fast connection b/w them
    Nitro system : dedicated hardware and high performance tasks
        Nitro cards : vpc, ebs and instance storage and controller card
        nitro secirity chips : integrated into motherboard, protects hardware
        Nitro hypervisor :
            light wight hypervisor
            bare metal like performance
    Bare metal :
        No hypervisor
        M5 and R5
    Amazon parallel cluster :
        open source cluster management tool
    usage :
        pcluster install
        pcluster configure
        pcluster create [cluster name] :
            create multiple stacks in cloud formation
            each stack consist of multiple cluster of ec2/vpc etc
            qstat to run the cluster

edge computing :
    push your computing workloads outside your network to the destination network
    run on phones and Iot devices
hybrid computing :
    run workloads both on premise and csp
    Aws Outposts :
        physical rack os servers
        allows you to use aws Api for aws services
    aws wavelength :
        build and run application in a telecom datacenter
        low latency
        verizon and vodafone
        usage :
            register request for the telecom datacenter
    Vmware cloud on aws :
        Manage on premise vm's using vmware as virtual machines
    Aws Local zones :
        edge datacenters located outside aws region
    Sage maker
    cloud front :
        launch application in edge location
        cold start time is less compared aws lambda

cost and capacity of compute engines :
    ec2 spot, reserved and savings plan :
        commiting to a plan by paying up front or yaerly contracts
    aws Batch :
        batch computing workloads across all aws compute services
    aws compute optimizer :
        reduce cost and increase performance by using ml
    ec2 autoscaling groups :
        adds or removes ec2 servers to meet on demand traffic
    ELB(elastic load balancer) :
        route traffic from unhealthy instance to healthy instance
    aws elastic beanstalk :
        just deploy web-apps
    
types of storage :
    elastic block store :
        storage is evenly split into blocks
        single write at a time
        directly access through os of a vm
        Fc and iscsi protocol to access files
    elastic file storage :
        file stores data and metadata
        multiple connections through shared network
        multiple read and write
        file share among multiple users
        Nfs and Smb protocol to access files
    amazon simple storage service (S3) :
        file object stores data, metadata and unique key
        no file size limit
        multiple read/write
        Https and api protocol to access files

S3 :
    files are stored in the form of objects
    consist of key, value, metadata and versionId
    name has to be unique
    0 to 5 terabytes of file sizes can be stored
    types : Trade of for time, accessibility and durability :
        s3 standard
        s3 intelligent tiering :
            uses ml to determine appropriate storage class
        s3 standard-IA :
            less cost if accessed < 1/month
        s3 one-zone-IA :
            

























[SharedResponsibiltyModel]: sharedResponsibilityModel.png