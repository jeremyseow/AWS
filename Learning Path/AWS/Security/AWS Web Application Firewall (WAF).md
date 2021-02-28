# AWS Web Application Firewall (WAF)

- A web application firewall that helps protect web applications from attacks by allowing you to configure rules that allow, block, or monitor (count) web requests based on conditions that you define

#### Components

- Conditions
	- Allow you to specify what elements of the incoming HTTP or HTTPS request you want WAF to be monitoring for
		- Cross-site scripting
		- Geo match
			- Allows you to specify which countries and geographic locations that you would like AWS WAF to filter on
			- If you are using the Geo restriction functionality within CloudFront to block a certain country from accessing your web application then the traffic from that country will not reach AWS WAF
				- If you want to use the Geo Match function within WAF, then you must first disable the Geo restriction settings within your associated CloudFront distribution
		- IP addresses
			- Allows you to specify a single IP address or a range of IP addresses that you want to either allow or block as you configure the WAF rules
			- This can be used in conjunction with the Geo Match condition for granular access
		- Size constraints
			- Allows you to block traffic based on the size of parts of the request
				- Header
				- HTTP Method
				- Query String
				- Single query parameter
				- All query parameters
				- Uniform Resource Identifier (URI)
				- Body
		- SQL injection
		- String and Regex Matching
			- Allows you to identify web requests based on strings that are contained within the request itself
				- For example a string within the request header
		
- Rules
	- Allows you to compile 1 or more of these conditions into a list which acts as a rule ==where each condition is ANDed to form the complete rule==
		- For example, if you had 3 conditions listed within a rule and an incoming request met only 2 of those conditions, it would not be a match to the rule
		- The request will then continue to be processed by the associated Web ACL to see if it meets any other rule
	- 2 types of rules
		- Regular rule
		- Rate based rule
			- Counts the number of requests that are being received from a particular IP address over a time period of 5 minutes
			- When you select a rate-based rule option, you will be asked to enter the maximum number of requests from a single IP within a 5 minute time frame
			- When the count limit is reached, all other requests from that same IP address is then blocked. If the request rate falls back below the rate limit specified the traffic is then allowed to pass through and is no longer blocked
			- ==Must be set to a value above 2000==
				- Any request under this limit is considered a Regular rule
				- You must also specify if the rule is associated to CloudFront or an application load balancer, and if so, in which region
- Web access control lists (Web ACLs)
	- Within the Web ACL, an action is applied to each rule, these actions can either be 
		- Allow
		- Block
		- Count
			- Counts the number of requests that meet the conditions within that rule
	- If an incoming request does not meet any rule within the Web ACL then the request takes the action associated to a default action specified which can either be Allow or Block
	- These rules is that they are ==executed in the order that they are listed== within a Web ACL
		- Recommended to order as:
			- WhiteListed Ips as Allow
			- BlackListed IP addresses as Block
			- Any Bad Signatures also as Block

#### Benefits

- High level of security compliance
	- Payment Card Industry Data Security Standard (PCI DSS) 3.2 certified

- Easier to implement, manage, and lower administration time needed to deploy AWS WAF compared to a standard WAF solution

- Mitigates vulnerability risks as close to the perimeter of your network environment as possible
	- Reduces the chances of other infrastructure and systems being compromised

#### How it works

- With CloudFront
	-  Although ==logically AWS WAF is in front of CloudFront, the request will be received by the CloudFront distribution first, and then it's immediately forwarded to your associated WAF Web ACL to either block or allow the request.== So before it's even traversed your CloudFront environment and network, you have the ability to detect, analyze, and either block or allow the incoming request. If the traffic is dropped, no more processing occurs, which saves valuable bandwidth across your internal network and prevents other internal systems potentially becoming compromised

#### Guide
- https://tutorialsdojo.com/aws-waf/