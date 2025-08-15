

# Print Details Notes


The current set up is actually fine mostly
But wont be for new world
We can use a new bsk component. I have created one quickly to test.
Then we have full control FE. 
But the current set up is actually fine mostly, and you can create a workflow which is quite fast and allows you to design in the browser with nly needing periodic testing with via the print detauils button


Workflow for faster web design when working print details

In Chrome
Create 2 custom device sizes for the device toolbar
PDF Portrait - dimensions w 905 x h 1280
PDF Landscape - dimensions w 1280 x h 905

Create a second print details page. 
By default we have : used-car-details_print.aspx
create a second used-car-details_landscape-print.aspx

Create a second print stylesheet
By default we have : css/print.css
Create a second css/print-landscape.css

For Styling Portrait Print Details
Find a current item of stock and copy the stock id
Navigate to used-car-details_print.aspx and pass the stock id as query string param value
eg `used-car-details_print.aspx?Stock_ID={STOCKIDHERE}`
Next, open dev tools
Toggle the Device Toolbar and select the new custom device PDF Portrait

You should now be able to style the page as you would any other web page, working to the approximate dimensions of a PDF document only needing periodic testing oif the final document with via the print details button


Next, open dev tools
Click on the sources tab
Click on 'Page'
Navigate to the /css/print.css
Right click on the file and click 


----

## Notes for Tech 

Disclaimer
Overview
Research
Solution
Trade offs
Next steps

Bit of an overview: 

We had two jobs in for quoting that were  brought to FE Review. Both relate to creating landscape orientation print details pages with very different designs from what we currently have. In FE we have had difficulties making significant styling changes to the current print details pages, and its led to us essentially sticking to / very close to the current boilerplate version in most cases (which is looking at bit tired now).

Off the back of that, been looking at what options we have to make writing styles for print  details / PDF a bit easier.

I experimented with a client side solution using a small client side lib https://github.com/crabbly/Print.js/  with a new bsk component that abstracts away the code needed to handle printing a template page. The component exposes a couple of options set via attributes on the custom element: 
- the relative url of the print details template page
- the relative url of the print details stylesheet
- the selector to use for targeting which bit of the document you want to print (`html`, `#main`, `.print-section`, etc)

From the Dev who works a print details task, the set up is essentially the same as now: a print details page with its own print stylesheet.

But the main benefits are: 
- Its much easier to write styles that are consistent between dev tools device emulation (emulating a PDF in this case) and the final output.
- That means we can use create more interesting and modern designs for print details pages. 
- Its much quicker to work any of these jobs that come in.
- FE can better understand the print dependency's API, and this opens up new options for us in

Using this way 

It also gives us access the library API so we have a few more opions open to us without needing to put tech jobs in
It seems to suit our use-case of needimng 

doesn't load the pdf viewer, moves directly to the print dialog. 
this is simpler and makes it quite a bit easier to ensure teh styles 

	the additional step of loading into the pdf viewer 

--

current BE?
https://www.html-to-pdf.net/html-to-pdf-converter.aspx

