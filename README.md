docker day 8
------------

* Observability
* Open Telemetry
* Jaeger Overview
* Jaeger Hotrod
* The future of containers
* Open container technology topics
* Class Review and Questions

observability
-------------

What is Observability?
In software, observability typically refers to telemetry produced by services and is often divided into three major verticals:

* Tracing, aka distributed tracing, provides insight into the full lifecycles, aka traces, of requests to the system, allowing you to pinpoint failures
and performance issues.

* Metrics provide quantitative information about processes running inside the system, including counters, gauges, and histograms.

* Logging provides insight into application-specific messages emitted by processes.
These verticals are tightly interconnected. Metrics can be used to pinpoint, for example, a subset of misbehaving traces. Logs associated with those
traces could help to find the root cause of this behavior. And then new metrics can be configured, based on this discovery, to catch this issue earlier next time. Other verticals exist (continuous profiling, production debugging, etc.), however traces, metrics, and logs are the three most well adopted across the
industry.

open telemetry
--------------

OpenTelemetry provides the libraries, agents, and other components that you need to capture telemetry from your services so that you can better
observe, manage, and debug them. Specifically, OpenTelemetry captures metrics, distributed traces, resource metadata, and logs (logging support is
incubating now) from your backend and client applications and then sends this data to backends like Prometheus, Jaeger, Zipkin, and others for
processing. OpenTelemetry is composed of the following:

* One API and SDK per language, which include the interfaces and implementations that define and create distributed traces and metrics,
manage sampling and context propagation, etc.

* Language-specific integrations for popular web frameworks, storage clients, RPC libraries, etc. that (when enabled) automatically capture
relevant traces and metrics and handle context propagation
* Automatic instrumentation agents that can collect telemetry from some applications without requiring code changes
* Language-specific exporters that allow SDKs to send captured traces and metrics to any supported backends
* The OpenTelemetry Collector, which can collect data from OpenTelemetry SDKs and other sources, and then export this telemetry to any
supported backend
OpenTelemetry is a CNCF Sandbox member, formed through a merger of the OpenTracing and OpenCensus projects.

Links:
* [Tracing vs Metrics](https://opentelemetry.io/docs/#metrics)

jeager overview
---------------

Jaeger, inspired by Dapper and OpenZipkin, is a distributed tracing system released as open source by Uber Technologies.
It is used for monitoring and troubleshooting microservices-based distributed systems, including:

* Distributed context propagation
* Distributed transaction monitoring
* Root cause analysis
* Service dependency analysis
* Performance / latency optimization

Uber published a blog post, [Evolving Distributed Tracing at Uber](https://eng.uber.com/distributed-tracing/), where they explain the history and reasons for the architectural choices made in Jaeger. Yuri Shkuro, creator of Jaeger, also published a book [Mastering Distributed Tracing](https://www.shkuro.com/books/2019-mastering-distributed-tracing/) that covers in-depth many aspects of Jaeger design and operation, as well as distributed tracing in general.

jaeger-hotrod
-------------

* Checkout this repo
* Deploy and HotRod using docker compose or kubernetes
* Navigate to the [official guide](https://medium.com/opentracing/take-opentracing-for-a-hotrod-ride-f6e3141f7941)

future of containers
--------------------

Containers offer numerous benefits over older IT models such as virtual machines. Containers make it
easy to integrate into DevOps. Containers also standardize the deployment and runtime model for
applications and services in production (and test/staging). Containers are an enabling technology for
microservice architecture and DevOps.

While there are definitely higher level abstractions that can replace containers like AWS Lambda
(FAAS) these services come with many restrictions and are usually locked to a single cloud. Which
leads to a very important point: Kubernetes and containers are a cloud abstraction layer.
Embracing this abstraction makes your stack a lot more portable and adds flexibility along with
building a much needed future-ready architecture.

containers vs paas
------------------

Platform as a Service and Functions as a Service have become very popular ways to build and deploy software, especially in public clouds such as AWS. Sometimes FaaS is also referred to as "serverless" computing, because your code only uses resources while running, and otherwise doesn't consume
server resources; hence being "serverless". The thing to keep in mind is that PaaS and FaaS are both really examples of container-based computing. Your cloud vendor creates a container that
includes an OS and various other platform-level dependencies such as the .NET Framework, nodejs, Python, the JDK, etc. You install your code into that pre-built environment and it runs. This is true whether you are using PaaS to host a web site, or FaaS to host a function written in C#, JavaScript, or Java. Think along a spectrum. On one end are virtual machines, on the other is PaaS/FaaS, and in the middle are Docker containers.

aws containerization services
-----------------------------

`AWS ECS` is a fully managed container orchestration service. It was an early containerization system that predated Kubernetes. Because of this the API is distinct and not comptable with the Kube API.

`AWS EKS` runs upstream Kubernetes and is certified Kubernetes conformant for a predictable experience. You can easily migrate any standard Kubernetes application to EKS without needing to refactor your code.

`AWS Fargate` is a serverless compute engine for containers that works with both Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS).

Fargate makes it easy for you to focus on building your applications. Fargate removes the need to provision and manage servers, lets you specify and pay for resources per application, and improves security through application isolation by design. Fargate allocates the right amount of compute, eliminating the need to choose instances and scale cluster capacity. You only pay for the resources
required to run your containers, so there is no over-provisioning and paying for additional servers. Fargate runs each task or pod in its own kernel providing the tasks and pods their own isolated compute environment. This enables your application to have workload isolation and improved security by
design. This is why customers such as Vanguard, Accenture, Foursquare, and Ancestry have chosen to run their mission critical applications on Fargate.

`AWS Lambda` - upload your code and run it without thinking about servers. To help you with that, you can now package and deploy Lambda functions as container images of up to 10 GB in size.

* [AWS Fargate](https://aws.amazon.com/fargate/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&fargate-blogs.sort-by=item.additionalFields.createdDate&fargate-blogs.sort-order=desc)
* [AWS ECS](https://aws.amazon.com/ecs/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&ecs-blogs.sort-by=item.additionalFields.createdDate&ecs-blogs.sort-order=desc)
* [AWS EKS](https://aws.amazon.com/eks/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&eks-blogs.sort-by=item.additionalFields.createdDate&eks-blogs.sort-order=desc)
* [AWS Labmda annouces support for containers](https://aws.amazon.com/blogs/aws/new-for-aws-lambda-container-image-support/)
* [AWS Labmda is winning](https://acloudguru.com/blog/engineering/aws-lambda-is-winning-but-first-it-had-to-die)


custom silicon and containers
-----------------------------

* [AWS Graviton](https://aws.amazon.com/ec2/graviton/)
* [AWS Graviton Overview](https://www.zdnet.com/article/aws-graviton2-what-it-means-for-arm-in-the-data-center-cloud-enterprise-aws/)
* [Google TPU](https://cloud.google.com/ai-platform/training/docs/using-containers)
* [Nvidia Docker](https://docs.nvidia.com/deeplearning/frameworks/user-guide/index.html)

firecracker microvms
--------------------

Firecracker enables you to deploy workloads in lightweight virtual machines, called microVMs, which provide enhanced security and workload isolation over traditional VMs, while enabling the speed and resource efficiency of containers. Firecracker was developed at Amazon Web Services to improve the customer experience of services like AWS Lambda and AWS Fargate .

* [Firecracker](https://firecracker-microvm.github.io/)

unikernels
----------

Unikernels are specialised, single-address-space machine images constructed by using library
operating systems. Unikernels shrink the attack surface and resource footprint of cloud services. They are built by compiling high-level languages directly into specialised machine images that run directly on a hypervisor, such as Xen, or on bare metal. Since hypervisors power most public cloud computing
infrastructure such as Amazon EC2, this lets your services run more cheaply, more securely and with
finer control than with a full software stack. Unikernels provide many benefits compared to a traditional OS, including improved security, smaller footprints, more optimisation and faster boot times.

* [Unikernels](https://techbeacon.com/enterprise-it/containers-20-why-unikernels-will-rock-cloud)

class conclusion
----------------

You have reached the end of the docker 2 class. In review you should have a firm grasp of:

* What a container is
* Why you would want to use one
* How to build a container using best practices
* How to use docker docker desktop
* How to create a CI/CD setup for your container images
* How to use docker desktop as a local kubernetes development cluster
* The general future direction of containers