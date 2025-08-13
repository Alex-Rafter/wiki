

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
Natigate to used-car-details_print.aspx and pass the stock id as query string param value
eg used-car-details_print.aspx?Stock_ID={STOCKIDHERE}
Next, open dev tools
Toggle the Device Toolbar and select the new custom device PDF Portrait

You should now be able to style the page as you would any other web page and see those changes affect the page


Next, open dev tools
Click on the sources tab
Click on 'Page'
Navigate to the /css/print.css
Right click on the file and click 