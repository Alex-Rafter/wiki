# UAT Deployment Beta Test 🚀

We are currently testing a new UAT deployment workflow.

## The problem ⚠️

We are not using UAT in an optimal way. Some problems are:  

- Testing is not done consistently on UAT
- Confusion (in FE / CS) about how Dev and UAT differ /what each is for
- Jobs being moved to the 'go live' step after Dev test only
- Stale UAT branches missing changes / problems with merging into UAT
- The way we are using UAT is slowing us down when it comes to getting jobs live

## The solution ✅

- Keep UAT for staging
- Auto-deploy to UAT when a PR is created, instead of manually deploying as a distinct ClickUp Stage
- Add a reminder to the PR body to check UAT before progressing
- If there are problems on UAT and the PR needs closing, that would trigger a git revert of that last merge commit to UAT keeping it still the same as live site

## Actions to set up Beta Testing 🛠️

After we have identified the dev and site that should be tested on we need to do the following: 

- Communication with CS
- Install the Beta Workflow

### Communication with CS 📢

- First and foremost we need to make sure CS are okay with us testing the new process and workflow on the site(s) we have identified
- This is important because we are not just changing the workflow but adjusting the testing process. 
- See Notes on Testing Process as this is the info we need to share with CS
  
### Install the Beta Workflows 💾

- Clone the repo
- From the project root run `npm run @alex-rafter/beta-uat-tester`
- You should now have : 
	- a new `deploy_uat.yml` workflow
	- an edited version to `deployment_caller.yml`
	- the edited `deployment_caller.yml` should point to a different version shared-deploy `@beta-uat` and have the key `uat-beta: true` set in the yml file

### Notes on Testing Process 📝
- All jobs for the test site should be put with the developer involved with the beta testing wherever possible. If this can't be done, it may be that the site is not a good candidate for early beta testing.
- Changes should be tested on DEV by CS
- After testing the can progress to check on live
- UAT will be used as a staging branch. Its will be primarily used by the FE Dev and potentially the reviewer for testing changes
- The changes will be auto-deployed to UAT when the FE Developer opens a new PR.