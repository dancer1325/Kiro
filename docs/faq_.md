# Frequently Asked Questions - Kiro

Source: https://kiro.dev/faq/

---

# Common questions
## What is Kiro?
Kiro is an agentic AI with an [IDE](/docs/) and [CLI](/docs/cli/) that helps you go from prototype to production with spec-driven development
* From simple to complex tasks, Kiro works alongside you to turn prompts into detailed specs, then into working code, docs, and testsâso what you build is exactly what you want and ready to share with your team
* Kiroâs agents help you solve challenging problems and automate tasks like generating documentation and unit tests
* With Kiro, you can build beyond prototypes while being in the driverâs seat every step of the way.

## What is spec-driven development? How is it different from vibe coding?
Developing with specs keeps the fun of vibe coding, but fixes some of its limitations: vibe coding can require too much guidance on complex tasks or when building on top of large codebases, and it can misinterpret context
* When implementing a task with vibe coding, itâs difficult to keep track of all the decisions that were made along the way, and document them for your team
* By using specs, Kiro works alongside you to define requirements, system design, and tasks to be implemented before writing any code
* This approach explicitly documents the reasoning and implementation decisions, so Kiro can implement more complex tasks in fewer shots.

## How can I get started with Kiro?
Kiro works as a standalone agentic [IDE](/docs/) or [CLI](/docs/cli)
* [Download](/downloads/) the installer for your operating system, and log in with GitHub, Google, AWS Builder ID, or AWS IAM Identity Center
* You do not need an AWS account to use Kiro
* For more, see [documentation](/docs).

## What programming languages does Kiro support?
Kiro supports a variety of programming languages that developers use in their day to day work
* This list includes, but is not limited to Python, Java, JavaScript, TypeScript, C#, Go, Rust, PHP, Ruby, Kotlin, C, C++, shell scripting, SQL, Scala, JSON, YAML, and HCL.

# What languages can I ask questions in?
Kiro is currently optimized for English language conversations and interactions
* Support for additional languages is coming soon.

##Can I import settings from my existing IDE?
Kiro is based on Code OSS, so you can [import your VS Code settings, themes, and Open VSX compatible plugins](/docs/guides/migrating-from-vscode/) in the Kiro onboarding flow.

# Pricing & Plans
## How does Kiro pricing work?
Kiro offers flexible pricing tiers designed around how developers use Kiro
* New users can start with the perpetual Kiro Free tier, which includes 50 credits
* You can upgrade to paid tiers ranging from Pro ($20/month), Pro+ ($40/month), to Power ($200/month) for increased capacity
* Paid tiers include flexible overages available at $0.04 per additional credit
* Kiro prices shown do not include applicable taxes or duties (such as VAT or sales tax) unless explicitly noted
* Note that if you have a Japanese billing address, Japanese Consumption Tax will apply to your Kiro usage
* The amount of tax collected depends on many factors, including, but not limited to, your Tax Registration Number (âTRNâ or Tax ID), and billing address.

## What models does Kiro use under the hood?
By default, your prompts are processed by Auto an agent that uses a mix of different frontier models such as Sonnet 4 combined with specialized models that are experts in specific tasks, intent detection, caching, and other techniques to give you a better balance of quality, latency, and costs
* You can also choose to have your prompts processed exclusively by Sonnet 4.

## How does the free trial work?
The first time you get access to Kiro, you will receive 500 bonus credits usable within 30 days, whatever plan you sign up for, including Kiro Free.

## What is a credit?
A credit is a unit of work in response to user prompts
* Simple prompts can consume less than 1 credit
* More complex prompts, such as executing a spec task, typically cost more than 1 credit
* Additionally, different models consume credits at different rates, with a prompt executed via Sonnet 4 costing more credits than executing it with Auto
* For example, a given task that consumes X credits to execute in Auto, will cost you 1.3X credits to execute via Sonnet 4
* Credits are metered to the second decimal point, so the least number of credits a task can consume is 0.01 credits.

## What can I use credits for?
Any prompt you ask Kiro to execute, whether in vibe mode or spec mode, as well as spec refinement, task execution, and agent hook execution, will consume credits.

## How can I track my credit usage?
You can see the monthly credit limits for your plan, the number of credits used, and credits remaining in your subscription dashboard accessible in the Kiro IDE
* Credit usage is updated at least every 5 minutes.

## Can I pay for additional credits?
Yes, on paid plans, you can enable overage to continue using Kiro past your monthly limits
* Additional credits are $0.04 each, billed at month-end based on actual over-cap usage
* For example, if you're on the Pro tier and use 1,100 credits (100 over your limit), you'll be charged an additional $4 on your next bill
* Overage is disabled by default and must be enabled in Settings before it applies
* Once you turn overages on, and for as long as you remain on a paid plan, overages stay on
* Once you downgrade to the Kiro Free tier, overages will be disabled, and you need to turn them back on when you are back on a paid plan.

## Can I share my Kiro subscription with my team?
No, subscriptions and usage limits are calculated per individual user
* For team usage, each developer needs their own subscription
* Team billing and management features are coming soon.

## What happens if I don't use all my monthly credits?
Usage limits reset at the start of each billing month
* Unused credits do not roll over to the next month.

## What payment methods do you accept?
We accept all major credit cards.

## What countries or regions are supported for individual plans?
Currently, you can purchase a Kiro paid plan with a billing address in Argentina, Australia, Austria, Bangladesh, Belgium, Brazil, Bulgaria, Canada, Chile, China, Colombia, Czech Republic, France, Germany, Hong Kong SAR, India, Indonesia, Israel, Italy, Japan, Malaysia, Mexico, Morocco, Nepal, Netherlands, New Zealand, Norway, Philippines, Poland, Portugal, Romania, Singapore, South Africa, South Korea, Spain, Sweden, Switzerland, Thailand, United Arab Emirates, United Kingdom, and the United States of America
* More countries or regions will be added soon.

# Enterprise
## How can my teams get started with Kiro?
Organizations can [get started with Kiro](/docs/enterprise/getting-started/) using their AWS IAM credentials.

## Do you provide an output indemnity for Kiro subscribers?
Yes, we provide an output indemnity for paid Kiro subscribers
* See Section 50.10 of the [Service Terms](https://aws.amazon.com/service-terms/) for more details.

## Can I control telemetry sharing (usage data, performance metrics) for Kiro at the organization level?
We do not collect telemetry from Kiro Pro, Pro+, or Power users that access Kiro through AWS IAM Identity Center
* However, enterprise admins can configure Kiro to collect user activity reports for the users in your organization.

## Which regions does Kiro support?
The Kiro CLI and IDE are [available](/docs/enterprise/supported-regions/) in the US East (N
* Virginia) and Europe (Frankfurt) AWS Regions when logging in via IAM Identity Center.

## Does Kiro use my content to train any models?
We do not use content from Kiro Pro, Pro+, or Power users that access Kiro through AWS IAM Identity Center
* If you have an Amazon Q Developer Pro subscription and access Kiro through your AWS account with the Amazon Q Developer Pro subscription, then Kiro will not use your content for service improvement
* We may use certain content from Kiro Free Tier and Kiro individual subscribers (those that access Kiro through a social login provider or AWS Builder ID) for service improvement
* You can opt out of content collection at any time using the opt-out mechanism described in our [documentation](/docs/privacy-and-security/data-protection/#opt-out-of-data-sharing)
* For more information, see [Service Improvement](/docs/privacy-and-security/data-protection/#service-improvement).

## I am an Amazon Q Developer Pro customer using Kiro
* Will Kiro use my content for service improvement?
No
* Amazon Q Developer Pro customers who use Kiro will retain their Q Developer Pro benefits by logging into Kiro with the same credentials used for Amazon Q Developer Pro
* Kiro will not collect their content for service improvement.

# Availability
## Which regions does Kiro support?
The Kiro CLI and IDE are [available](/docs/enterprise/supported-regions/) in the US East (N
* Virginia) and Europe (Frankfurt) AWS Regions when logging in via IAM Identity Center.

## What countries or regions are supported for individual plans?
Currently, you can purchase a Kiro paid plan with a billing address in Argentina, Australia, Austria, Bangladesh, Belgium, Brazil, Bulgaria, Canada, Chile, China, Colombia, Czech Republic, France, Germany, Hong Kong SAR, India, Indonesia, Israel, Italy, Japan, Malaysia, Mexico, Morocco, Nepal, Netherlands, New Zealand, Norway, Philippines, Poland, Portugal, Romania, Singapore, South Africa, South Korea, Spain, Sweden, Switzerland, Thailand, United Arab Emirates, United Kingdom, and the United States of America
* More countries or regions will be added soon.

## Which countries or regions support Kiro startup credits?
Kiro credits are supported in most countries globally where AWS billing is available
* Startups in Argentina, Brazil, Cuba, France, Germany, Iran, Italy, Mexico, North Korea, Region of Crimea, Russia, Sudan, Syria, and Spain are not eligible for this program.

# Privacy
## Can I control telemetry sharing (usage data, performance metrics) for Kiro at the organization level?
We do not collect telemetry from Kiro Pro, Pro+, or Power users that access Kiro through AWS IAM Identity Center
* However, enterprise admins can configure Kiro to collect user activity reports for the users in your organization.

## Does Kiro use my content to train any models?
We do not use content from Kiro Pro, Pro+, or Power users that access Kiro through AWS IAM Identity Center
* If you have an Amazon Q Developer Pro subscription and access Kiro through your AWS account with the Amazon Q Developer Pro subscription, then Kiro will not use your content for service improvement
* We may use certain content from Kiro Free Tier and Kiro individual subscribers (those that access Kiro through a social login provider or AWS Builder ID) for service improvement
* You can opt out of content collection at any time using the opt-out mechanism described in our [documentation](/docs/privacy-and-security/data-protection/#opt-out-of-data-sharing)
* For more information, see [Service Improvement](/docs/privacy-and-security/data-protection/#service-improvement).