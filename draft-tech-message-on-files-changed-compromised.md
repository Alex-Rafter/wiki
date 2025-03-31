# tj-actions/changed-files Dependency Compromised

Hi Dave, Hi Steve 

One of the dependencies we use in our GitHub Actions workflows has been compromised. 

https://github.com/tj-actions/changed-files?tab=readme-ov-file#changed-files

Overview 

- This is popular dependency - its used in over 23000 repos workflows, and is listed on GitHub's Actions Marketplace: https://github.com/marketplace?query=%23+changed-files&type=actions
- The compromise attempts to exposure secrets in public logs. 
- Our repos are privates and so are our logs so it seems that this won't have affected us but please see what you think on that.
- We use it in one of our codebases : https://github.com/MBBluesky/shared-workflows/
- That is a reusable workflow that is called by most of our sites to handle automated build and deployment

There are 3 required actions + 1 suggestion listed on the repo: 

1. Review your workflows executed between March 14 and March 15.
2. Immediately update workflows referencing the problematic commit directly.
3. If you are using tagged versions (e.g., `v35`, `v44.5.1`), no action is required as these tags have been updated and are now safe to use.

4. Rotating any secrets that may have been exposed during this timeframe to ensure the continued security of your workflows.

Notes on Actions Needed :
1. Our logs persist for only 24 hours so I can't review the logs (see required actions below) but this also means they were removed quickly.
2. N/A - we use tagged release 
3. We already use tagged release 
4. I can regenerate the GitHub Personal Access Tokens but will need Tech support to review and regenerate keys for FTP held in secrets. Also, i am not sure whether regenerating the FTP_PASSWORD is sufficient or not or if we need other secrets updating also.
   
   
