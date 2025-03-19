
# Bluebook As API


It would be very useful to be able to access the data currently formatted as html on 

https://bluebook.dev.cogplatform.co.uk/websites/dev
https://bluebook.dev.cogplatform.co.uk/websites/live
https://bluebook.dev.cogplatform.co.uk/websites/platforms
 
As JSON via an API endpoint.

Have discussed this idea briefly in passing when in meets with Dave and Steve.

Why?
- Data could be useable from within workflows eg to grab server and server dir information, instead of these values being statically set in github actions workflow yml.
- We can more easily check for and report on missing data that we in FE have responsibility for updating eg missing GH repo links.
- We can run checks when working locally to see if the version of vanilla being used matches that listed in bluebook.
- We are likely to be able to leverage this data in more automated / configurable site development workflows (ie 300 project style development)
  
These are just a few of the ideas initial ideas and problems a bluebook api would solve. I think it could open up quite a few more opps for automation down the road.

Ideally, would be good if we can have endpoints for :
- Return all data - eg all site data listed under bluebook dev
- Return data matching query - eg query by webid, gh repo, url, server directory, server (WEB1, WEB2, etc) - could return single or multiple results depending on query
- Return latest vanilla version (and sites this is used on)

Ideally data returned would be 
- Data currently on shown on details view 
	(eg https://bluebook.dev.cogplatform.co.uk/websites/view/3945) 
- Plus the GH repo data shown on list view 
	(eg https://bluebook.dev.cogplatform.co.uk/websites/dev)

*We may not need all enq types etc v often so perhaps the payload could be reduced by just including that for the endpoint 'Return data matching query' but not endpoint 'Return data matching query'*

It would be great if we could scope the work so that we initially use a v1.0, and feedback on extra data that it would be useful to access / parametrs to query by; and iterate together in this way. As I think its likely other use-cases will surface once start to use this.

