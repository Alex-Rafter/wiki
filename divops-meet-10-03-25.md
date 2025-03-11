# DivOps Meet

Items: 
- purpose of meet
	- UAT initially 
	- opps to get others involved
		- Broader with SPOF 
	- stopping siloed working on CI/CD
- PR Process work review 
- UAT workflow Beta Test 
	- report on what we've started testing
	- feedback on it
- Shared deploy 
	- report on where its at 
	- ideas / opps for feed in on 'middleman'
	- troubleshooting and first line of defence idea
- Bash /shell basics training opp
- Internal tools notes 

End of meet 
- who can move Beta testing forward? 
agnew? - who does ads? Umf
Max: Anc, Days, Carco, JustAudi - 

Next : Ancaster, Days
Additional tags for CU jobs - new deployment workflow
CS need to tag the job as new workflow
Speak with Simmi on that

- anyone interested in Bash basics 
- SPOF any particulars anyone wants to take up 

Actions
scheduled clean up of uat for new UAT worfklow
no status code testing as yet
speak with Simmi/ CS on tags and roll out with Max's sites
seniors : shared-deploy training specifically - basics 
seniors : shared-deploy training specifically - in depth? Pt 2
troubleshooting deploy errs + flowchart 
better summary in shared-deploy where it fails
basic shell training - need to do this first?
maintenance on bp - should be briefed and shared
arrange next meet - with Barbs

will split out beta testing the new uat workflow - 
- need an installer steps for beta test roll out
- adding to sites will be team activity 
- support for Max will be seniors in pod

High-level
DevOps - shared by getting all seniors installing new UAT workflow
Shared-deploy - just Callum first
All : shell / Node basics 
UAT workflow testing : Max and Natalia as a next step


---------------------
UAT Notes
---------------------

Original msg 
https://mbbluesky.slack.com/archives/C02CF91FN9Z/p1739525099461029

Just a quick update on the beta test of UAT deploy at PR open, and git revert on PR closed.

  

I think we have a really nice workflow now with this.

This def helps keep UAT up to date with all changes where these were getting missed before at times; and it reduces the extra clickup step as the time-save we wanted.

A couple of things :

  

- There is a way to keep UAT history much much closer to main at all times - which i think would help improve UAT's role as a true staging branch.  Would like to discuss the idea for this and get feedback.

- There are lots of options to build in some automated testing on the staging branch - eg the workflow firing off a bunch of requests to key pages on UAT after deploy, and checking status codes, to make sure pages aren't erroring after the changes etc. Status of the tests could then be added to the PR body as a mini report for dev / reviewer.

- There is a question to answer about how this new worfklow would work at build as we may want to deploy to uat on push still or there are a few other options too.
