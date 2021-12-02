## Monitoring a Live Streaming Workflow with Amazon CloudWatch

### Overview
An important part of any video workflow is being able to monitor the status and health of the software services and their tasks in order to detect and correct problems before they jeopardize the workflow. This is especially true when streaming live video where there are no “do-overs” and the cost of an issue or outage can be huge in terms of revenue, fines or damage to reputation.

In this lab you will use Amazon CloudWatch to monitor certain aspects of a live streaming video workflow.

During the lab setup, an AWS CloudFormation template will create a live streaming workflow, depicted below.

![AWS Lambda Lab](/LAB001/Monitoring%20a%20Live%20Streaming%20Workflow%20with%20Amazon%20CloudWatch/aws_live_streaming_monitoring_lab.png)

1. AWS CloudFormation creates an AWS Elemental MediaLive channel, which takes a high-resolution input stream.

2. MediaLive compresses that input into multiple lower-resolution versions that are suitable for streaming over the internet.

3. MediaLive feeds into AWS Elemental MediaPackage, which will temporarily cache the video and then package it and serve it up to viewers upon request.

4. You will then configure Amazon CloudWatch to monitor the workflow at key points.

Note in actual practice, to serve hundreds, thousands, or millions of simultaneous viewers, the packaged video streams need to be fanned out through large distribution networks. This is called the content delivery network (CDN), such as Amazon CloudFront CDN. To save time, for the purposes of this lab, you will not be creating a CloudFront distribution.

### Key Metrics to Measure In A Live Workflow
The following are examples of key metrics to monitor in a live streaming workflow.

* Changes in the status of a MediaLive channel: In some workflows, channels run for very long durations (even 24x7), and it is important to know if one of these had been inadvertently stopped. Status states include starting, running, stopping, and idle.

* Issues or potential issues in a channel: MediaLive generates alerts when certain conditions occur in a channel, including loss of video input, loss of audio input, and output below realtime, among others. It would be vital to know if any one of these occurs as early as possible.

* Input to MediaLive: For the AWS Media Services, this is the beginning of the workflow and it is vital to flag any disruptions or failures at the input stage as early as possible.

* MediaLive output to MediaPackage: It is important to get warnings of changes (such as drops in MediaLive output) so you can intervene before it’s too late.

* Input to MediaPackage (referred to as ingress): It isn’t sufficient only to monitor MediaLive’s output—you also need to verify that MediaPackage is actually receiving an input, and at what rate.

* MediaPackage output (referred to as egress): This is another vital area to monitor—it is the stage where the AWS Media Services pass the content to the next downstream system such as a CDN.

### Topics Covered
By the end of this lab, you will be able to:

* Create notifications based on MediaLive alerts and channel status changes
* Create metrics to measure MediaLive input and output
* Create metrics to measure MediaPackage input and output
* Build a dashboard to view those metrics
* Manipulate the workflow and observe the results in CloudWatch

### Tasks I Completed Through This Lab
* Created an Amazon SNS topic and CloudWatch event to send email notifications about MediaLive events and status
* Built a dashboard to monitor the following metrics:
    * Network input into MediaLive
    * Network output from MediaLive
    * Ingress into MediaPackage
    * Egress from MediaPackage
* Set up alarms and notifications based on metrics from MediaPackage
* Tested the monitoring by changing conditions in the live stream