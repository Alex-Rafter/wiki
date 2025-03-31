## LLM Prompt Template

**Instruction**  
You are to output a html partial made up of one script tag. The script tag should have the type attribite type="application/json". 
The text content of the script tag should be made up of json. The json istelf will be made up of statically written json syntax and propety names etc. But the values will be made up of inline VB Te,plate expressions. The specifc template expressions to output will be based on the Literals you are provided with in the input data section of this prompt. 

**Context or Background** 
I am creating interim API endpoints within an ASP.NET back-end. The current set up returns html not json. I am creating includes / partials / templates that each contain one script tag. These will be included inside an aspx page that returns html. Thus, the page will return a barebone html document but within that page there will be the script tag or tags, that contain dynamically generated json, which contain server rendered data from the backend platform literals.

**Example**  
Below is an example of the format that the output should conform to. It contains both the literals and then the script tag in which they are used to server render json as text content.

```html

<asp:Literal ID="Stock_ID" runat="server" visible="false" />
<asp:Literal ID="DealerID" runat="server" visible="false" />
<asp:Literal ID="DiscountPrice" runat="server" visible="false" />
<asp:Literal ID="Price" runat="server" visible="false" />
<asp:Literal ID="Saving" runat="server" visible="false" />
<asp:Literal ID="Manufacturer" runat="server" visible="false" />
<asp:Literal ID="Model" runat="server" visible="false" />
<asp:Literal ID="Version" runat="server" visible="false" />
<asp:Literal ID="Colour" runat="server" visible="false" />
<asp:Literal ID="Mileage" runat="server" visible="false" />
<asp:Literal ID="FuelType" runat="server" visible="false" />
<asp:Literal ID="RegYear" runat="server" visible="false" />
<asp:Literal ID="RegNumber" runat="server" visible="false" />
<asp:Literal ID="RegPlate" runat="server" visible="false" />
<asp:Literal ID="Transmission" runat="server" visible="false" />
<asp:Literal ID="BodyType" runat="server" visible="false" />
<asp:Literal ID="Doors" runat="server" visible="false" />
<asp:Literal ID="Seats" runat="server" visible="false" />
<asp:Literal ID="Images_2" runat="server" visible="false" />
<asp:Literal ID="COGUsedURL" runat="server" visible="false" />
<asp:Literal ID="Options" runat="server" visible="false" />
<asp:Literal ID="MPG" runat="server" visible="false" />
<asp:Literal ID="TaxCost" runat="server" visible="false" />
<asp:Literal ID="CO2" runat="server" visible="false" />
<asp:Literal runat="server" ID="IsReserved" Visible="false"/>
<asp:Literal runat="server" ID="IsExDemoCar" Visible="false"/>
<asp:Literal runat="server" ID="ManagersSpecial" Visible="false"/>
<asp:Literal runat="server" ID="FranchiseApproved" Visible="false"/>
<asp:Literal runat="server" ID="IsVan" Visible="false"/>
<asp:Literal runat="server" ID="VAT" Visible="false"/>
<asp:Literal runat="server" ID="VideoURL" Visible="false"/>
<asp:Image ID="Images" runat="server" Width="300" Visible="false" />
<%
    Dim ImageThumb = ""
    If Images.ImageUrl.Contains("noimage") Then
        ' Do nothing as no image found '
    Else
        Dim imageUri As New Uri(Images.ImageUrl)
        Dim imageUrl = imageUri.Query
        Dim newquery = HttpUtility.ParseQueryString(imageUrl)
        newquery.Set("quality", "85")
        ImageThumb = imageUri.OriginalString.Substring(0, imageUri.OriginalString.IndexOf("?")) + "?" + newquery.ToString
    End If
%>
<!--#include file="/inc/modules/template-logic/dynamic-path.aspx" -->
<!--#include file="/inc/modules/petite/shortlist-plus/props-object.aspx" -->
<% Dim hf As New CogHelperFunctions %>
<% Dim hasVideo = If(VideoURL.Text <> "~", "true", "false") %>

<script bsk-data-response="list" type="application/json">
    {
        "identifiers": {
            "stockID": <%=hf.ToJson(Stock_ID.Text)%>,
            "dealerID": <%=hf.ToJson(DealerID.Text)%>,
            "manufacturer": <%=hf.ToJson(Manufacturer.Text)%>,
            "model": <%=hf.ToJson(Model.Text)%>,
            "version": <%=hf.ToJson(Version.Text)%>,
            "url": <%=hf.ToJson(dynamicPath(Session("brand"), COGUsedURL.Text))%>
        },
        "pricing": {
            "price": <%=hf.ToJson(Price.Text)%>,
            "monthly": <%=hf.ToJson(250)%>,
            "discountPrice": <%=hf.ToJson(DiscountPrice.Text)%>,
            "saving": <%=hf.ToJson(Saving.Text)%>
        },
        "registration": {
            "regYear": <%=hf.ToJson(RegYear.Text)%>,
            "regNumber": <%=hf.ToJson(RegNumber.Text)%>,
            "regPlate": <%=hf.ToJson(RegPlate.Text)%>
        },
        "body": {
            "colour": <%=hf.ToJson(Colour.Text)%>,
            "bodyType": <%=hf.ToJson(BodyType.Text)%>,
            "doors": <%=hf.ToJson(Doors.Text)%>,
            "seats": <%=hf.ToJson(Seats.Text)%>
        },
        "features": {
            "mpg": <%=hf.ToJson(MPG.Text)%>,
            "taxCost": <%=hf.ToJson(TaxCost.Text)%>,
            "co2": <%=hf.ToJson(CO2.Text)%>,
            "options": <%=hf.ToJson(Options.Text)%>,
            "mileage": <%=hf.ToJson(Mileage.Text)%>,
            "fuelType": <%=hf.ToJson(FuelType.Text)%>,
            "transmission": <%=hf.ToJson(Transmission.Text)%>
        },
        "images": {
            "imgSrc": <%= hf.ToJson(ImageThumb) %>,
            "thumb": <%= hf.ToJson(ImageThumb) %>,
            "all": <%=hf.ToJson(Images_2.Text)%>,
            "count": <%=hf.ToJson(Images_2.Text.Split(",").Count)%>
        },
        "video" : {
            "hasVideo": <%=hf.ToJson(hasVideo, False)%>
        },
        "status": {
            "isReserved": <%=hf.ToJson(IsReserved.Text)%>,
            "isExDemoCar": <%=hf.ToJson(IsExDemoCar.Text)%>,
            "managersSpecial": <%=hf.ToJson(ManagersSpecial.Text)%>,
            "franchiseApproved": <%=hf.ToJson(FranchiseApproved.Text)%>,
            "isVan": <%=hf.ToJson(IsVan.Text)%>
        }
    }
</script>


```
**Desired Format or Output Style**  
Codeblock formatted as html
One script tag 
JSON syntax with ASP.NET inline template expressions

Here is the format to work to. You should copy this, adding the literals provided below 
`<% Dim hf As New CogHelperFunctions %>`
And replace  `[[LLM CONTENT SHOULD GO HERE]]` with the json text content 
```html

<%@ Page Language="VB" AutoEventWireup="false" EnableEventValidation="false" CodeFile="~/COG/COGPageLoader/COGPageLoader.vb" Inherits="COGPageLoader" %>

<% Dim hf As New CogHelperFunctions %>

<form id="form1" runat="server">

     <script bsk-data-response="details" type="application/json">
        [[LLM CONTENT SHOULD GO HERE]]
     </script>


</form>

```

**Persona or Role for the Model**  
You are an expert web developer

**Constraints or Rules**  
Limit introductory text etc. Focus on producing the code output unless otherwise prompted for more information 

**Input Data**  
Below are the literals for you to work with: 

```html

<COG:WebsiteInfoLiteral runat="server" ID="Website_Name" DataField="WebsiteName" />
<COG:WebsiteInfoLiteral runat="server" ID="Website_Url" DataField="WebsiteURL" />
<COG:COGDynamicNumberOfResults_V1 ID="COGDynamicNumberOfResults_V1" runat="server"/>
 
```


