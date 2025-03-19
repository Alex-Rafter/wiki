
# Bluebook As API

It would be very useful to be able to access the data currently formatted as html on 

https://bluebook.dev.cogplatform.co.uk/websites/dev
https://bluebook.dev.cogplatform.co.uk/websites/live
https://bluebook.dev.cogplatform.co.uk/websites/platforms
 
As JSON via an API endpoint.

Have discussed this idea briefly in passing when in meets with Dave and Steve.

Why?
- Data could be useable from within workflows eg to grab server and server dir information, instead of these values being statically set in github actions workflow yml.
- We can more easily check for and report on sites with missing data we in FE have responsibilty for updating eg GH repo links. 
- We can run checks when working locally to see if the version of vanilla being used matches that listed in bluebook.
These are just a few of the ideas. I think it could open up quite a few more opps for automation.

Ideally, would be good if we can have endpoints for :
- Return all data - eg all site data listed under bluebook dev
- Return data matching query - eg query by gh repo, site url, server directory, server (WEB1, WEB2, etc) - could return single or multiple results depending on query
- Return latest vanilla version (and sites this is used on)

Ideally data returned would be 
- Data currently on shown on details view 
	(eg https://bluebook.dev.cogplatform.co.uk/websites/view/3945) 
- Plus the GH repo data shown on list view 
	(eg https://bluebook.dev.cogplatform.co.uk/websites/dev)

We may not need all enq types etc v often so perhaps the payload could be redcued by just including that for the endpoint 'Return data matching query' but not endpoint 'Return data matching query'

It would be great if we could look at a way to work together where we initially use a v1.0, and then can feedback on any extra data that would be useful to access vie the endpoints, and iterate in this way, as i think its likely other use-cases will surface once we move over / have this option to  access site data via an api.

