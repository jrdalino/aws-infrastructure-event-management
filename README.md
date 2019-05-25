# AWS Infrastructure Event Management

## Section 1: Event Details and Sucess Criteria
Enter event details here.

Success criteria:
- Success criteria 1
- Success criteria 2
- Success criteria 3

## Section 2: Calendar
Start and End Time (include time zone)
- Start: MMM DD, YYYY HH:MM AM/PM GMT +8 (Day)
- End: MMM DD, YYYY HH:MM AM/PM GMT +8 (Day)

## Section 3: Contacts
Please list all contacts that will be involved in the event:
- Group
- Name
- Phone
- Role
- Email

## Section 4: Conference Bridge Information
Enter conference details here.

## Section 5: Endpoints to Monitor
Please provide URL and credentials for any websites, portals or monitoring systems that we will need to access during the event:

## Section 6: AWS Resources

### Global Infrastucture (1 table per account for clarity)
- CloudFront distribution (ID or CNAME)
- Route 53 hosted zone/s
- Simple Email Service (SES) Domain
- Other

### Regional Infrastructure (1 table per account and per region for clarity)
- AWS Account
- AWS Regions
- Instance ID's
- ELB Name
- Autoscaling Group
- S3 Bucket Names
- VPC ID
- DynamoDB Hostnames
- RDS Hostnames
- Elasticache
- Cloudformation Stacks

## Section 7: ELB Prewarming
- AWS Support Case Id: 1234567890
- Use Case
- Region
- ELB
- ELB AZ's
- Backend Instances > Is it currently scaled?
- Backend Instances > If no, when would it be scaled?
- Backend Instances > Are they running persistent connections? (Keep alive?)
- SSL > % of Traffic that is SSL: 100%
- Traffic Increase > Start Date
- Traffic Increase > End Date
- Traffic Increase > Duration of Increase
- Traffic Increase > If several days, is there an exact time for the load increase?
- Traffic Increase > If several days, is there an exact time for the load decrease?
- Traffic Increase > Get Requests/Sec (XXX/sec on avg, peak XXX rps)
- Rate of Increase > Traffic is expected to increase: 22 times (22x) normal traffic
- Data > Average size (KB) of each GET request: X KB
- Data > Average size (KB) of each GET response: X KB

## Section 8: Event Timeline/Checklist

### Initiate

#### Step 1: Schedule an IEM Kickoff call
- Type of Event:
- Key dates:
- Support Requirements of the event
- List of Business-Critical Workloads and AWS Service dependencies:
- Potential Capacity requirements
- Subjects requiring expert level review:
- Last Well Architected Review

#### Step 2: Open AWS Support Case for IEM
- Partner: AWS Account ID of highest utilization involved account, then select Account Name
- Subject: IEM Alert - <Customer Name> - <Event Name>  Please use this naming convention exactly
- Case Body: Requesting proactive support for IEM. <Attach IEM Runbook>

#### Step 3: Broadcast IEM Alert to Stakeholders
#### Step 4: Update Architecture Diagrams

### Plan

#### Step 5: Architecture review sessions with SA
#### Step 6: Work on this IEM Planning Workbook
#### Step 7: Create an Internal Event Wiki Page
#### Step 8: Check Trusted Advisor
#### Step 9: Check Service Limits
#### Step 10: Capacity Planning
#### Step 11: Load Testing
#### Step 12: Create Directory of SME's
#### Step 13: Step 13: Determine Event Readiness - Use the Event Readiness Scorecard to guide this conversation.
- AWS Service Readiness (Availability and Capacity)
- Operational Readiness (Stability)
- Security Readiness (DDoS Prep, Trusted Advisor checks)

#### Step 14: Pre-Event Readiness Check (one week prior to event)
- Drive open action items to completion

#### Step 15: Escalations Matrix

### Execute

#### Step 16: Attend War rooms, join Slack chat rooms, and conference calls with customer as planned
#### Step 17: Monitor Infrastructure Dashboards
#### Step 18: Send Regular Updates to Stakeholders
#### Step 19: Active Event Escalations

### Review

#### Step 20: Scale down resources to normal operating levels
#### Step 21: Review event metrics
#### Step 22: Review action items or failures with customer and close the loop
#### Step 23: Resolve the IEM Alert Support Case and Set the Reason Code and Category-Type
#### Step 24: IEM Survey Request
#### Step 25: Create IEM Success Story

## Section 9: Architecture Diagram
- https://www.draw.io/

## Section 10: Trusted Advisor Review
- https://console.aws.amazon.com/trustedadvisor/home?region=ap-southeast-1#/dashboard

## Section 11: Service Limits
- https://console.aws.amazon.com/trustedadvisor/home?region=ap-southeast-1#/category/service-limits

## Section 12: Well Operated Checklist
The questions below are intended to be answered by technical staff responsible for the successful outcome of the IEM event.

### Monitoring
- What internal tools are being used for monitoring during the event that AWS needs access to?
- What metrics are crucial to be informed about during the event?
- ELB: Latency, ELB 5XX,4XX, Backend 5XX,4XX, Backend connection errors, Surge Queue, Healthy host count
- EC2: CPU, Network In, Network Packets In, IOPS, Disk Latencies
- ElastiCache Memcached: GetHits, GetMisses, BytesUsedForCacheItems, Evictions, FreeableMemory, CPUUtilization, NetworkBytesIn, NetworkBytesOut
- RDS: Read and Write query throughput and performance, Replication and reliability, Resource utilization, Connections

### Security
- When was the last rotation of credentials performed on resources specific to this event? 
- How will the environment be accessed during the event? 
- How will the environment be accessed during component/system failure? 

### Resilience
- What risks exist to the stability of the application during the event?
- Is there a single point of failure? (Eg. Single AZ) 
- Where is content stored and is it resilient?
- What is the impact of any lost content/data/systems?
- What service restoration plans are in place?
- Has RDS/Auto Scaling/ELB been deployed across multiple AZs?
- In the case of outage or performance  degradation is failover an automatic or manual process?  
- EBS Snapshots performed?
- RDS Instances and other storage services recently backed up?

### Performance
- Is there an infrastructure stress point in the design? (Eg. network bandwidth on instance)
- Is there an application stress point in the design? (Eg. single row on database)
- What load testing will be performed on the platform? 
- Is there a CDN being utilized for this event?
- Has logging been enabled on key resources to identify potential areas of performance for a repeat event? (output to S3 or other?)
- Have alarms been set for various performance breaches? (Eg. Cloudwatch or other customer based tool, where is the output going to?)

### Service Limits
- Which AWS services will be used that may need increased limits for this event?
- Are there any autoscaling groups that have a scaling policy that will start more instances than the limit for the region?
- Will EBS storage needs throughout the event be greater than the maximum allowable volume capacity per region limit?
- Will emails be sent from EC2 instances and at what rate? 
- Has the application been sized for the correct amount of Provisioned IOPS and is there a chance this may need to be raised throughout the event?
- Will spot instances be used and if so could this service limit be triggered?
- Will additional S3 buckets be created throughout the event and if so will the 100 bucket hard limit per account be breached?
- If SES is being used for the sending of email, what is the maximum number of emails expected to be sent over a 24 hour period?

## Section 13: Load Testing Results
Enter Load Testing Results here.

## Section 14: Scenario Planning

### Primary Plan
- Description of primary plan
- What events will trigger a move to the secondary plan?
- Who needs to be notified about moving between plans?
- How will these resources be notified?
- How can we verify success?

### Secondary or Rollback Plan
- Description of secondary plan
- What events will trigger a complete rollback?
- Who needs to be notified about this?
- How will these resources be notified?
- How can we verify success?

## Section 15: Event Readiness Scorecard

### Availability: Architecture
- GREEN: Single Points of Failure eliminated at all tiers
- YELLOW: At risk for failure in one or more tiers
- RED: No failover components or plans

### Stability: Case Management
- GREEN: No languishing cases or open tickets to service teams that would impact system stability
- YELLOW: Risk - Customer has opened several recurring cases recently that indicate a trend that could impact system stability during the event
- RED: Issue - Customer has one or more open cases that is not resolved; open tickets with Service Team is not progressing; this will impact system stability during the event if not resolved.

### Scalability: Capacity (EC2 and Other Critical AWS Services)
- GREEN: Service limits increased; Service team validated capacity is available in desired Region/AZ or Capacity is provisioned
- YELLOW: Risk - Capacity signals unknown or Capacity requested but not verified by Service Team
- RED: Issue - Capacity will not available; Service limits cannot be increased

### Scalability: Capacity (Load Balancing ALB, NLB, CLB Pre-warm)
- GREEN: Pre-warms requested or completed; Pre-warm check performed by ELB Service Team
- YELLOW: Risk - Pre-warms not requested; ELB configuration not verified; risk of not scaling to expected levels or delays in scaling eminent
- RED: Issue - ELBs undersized or not correctly configured, back-ends not configured; system will not scale to expected levels during event

### Scalability: Capacity (Load Test)
- GREEN: Completed load testing - all systems capable of expected load during event
- YELLOW: Risk - Load testing not completed or levels not satisfactory; risk of not scaling to expected levels during event
- RED: Issue - Load testing failed; system will not scale to expected levels during event

### Security: Trusted Advisor
- GREEN: TA Security Checks all Green or determined will not impact event (Attention on MFA on Root, CloudTrail Logging, Exposed Access Keys, Security Groups - Ports Unrestricted)
- YELLOW: Risk - One or more Security Checks appear as Yellow: Investigation recommended
- RED: Issue - One or more Security Checks appear as Red: Action recommended (Capture Action for Reporting)

### Security: DDOS Protection
- GREEN: Customer is following minimum DDoS Protection (BP1, BP3, BP6, & BP7 - ref: https://d0.awsstatic.com/whitepapers/Security/DDoS_White_Paper.pdf
- YELLOW: Risk - Customer is not substantially following the best practices for DDoS-resiliency and is operating with an elevated degree of risk
- RED: Issue - Application is poorly designed and deployed and is NOT prepared to withstand common DoS/DDoS attacks

## Section 16: Action Items / Risk / Issue Tracker
- Description
- Status : Red | Yellow | Green
- Reason :
- Owner: 
- Remarks: 

## Section 17: Recommendations
Enter recommendations here.

## Section 18: Post IEM Analysis
Enter Post IEM Analysis here.

## Appendix A: References
Enter References here.

## Appendix B: AWS Service Usage for the last 12 months
Enter AWS Service Usage for the 12 months.
