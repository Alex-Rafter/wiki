

# Clean AutoEdge Setup

The pattern below is not meant as an alternative to our AutoEdge install docs! This is a pattern to use when setting up AutoEdge to minimise parasol controls and markup.

## The problem

Setting up AutoEdge can get complex quickly. When we have multiple parasol content switcher controls, this often leads to a lot of markup on the page / in the include. When we work with multiple parasol content switcher controls in this way, it also often requires us to duplicate parts of the template.

## The Solution

Limit Parasol Content Switcher and Parasol Content Controls to one set per page type  (eg homepage, ucd, etc). Use this one Parasol Content Switcher, and the one set of Parasol Content Controls, to set all dynamic values : Session variables, cms references, cog control properties; and styles for hiding / showing, and ordering content. 

## The Benefits

The benefits of the pattern below are that AutoEdge parasol content switcher and parasol content controls are kept to a specific include for each per page type (eg homepage, ucd, etc). This helps keep the codebase clean, and the set up uniform across the site. By using the same pattern across builds its makes our AutoEdge setups consistent and easier to maintain. 

Between session variables and styles set we can control things like : 
	- the cms content that is rendered for each segment 
	- the order of sections on a page
	- showing / hiding sections for specific segments
	- setting different static queries used with Tiny Search for different segments
## The Setup

- Limit Parasol Content Switcher and Parasol Content Controls to one set per page (eg homepage, franchise homepage, ucd, etc). Set these page level controls up an include separate from the page they are used on. 
### Example 

```html
<!doctype html>
<html lang="en" class="no-js">
<head runat="server">
  <!-- normal <head> content here... -->
  <!--#include file="/inc/modules/autoedge/group-home.aspx" -->
</head>
<body v-cloak class="page">
  <!-- normal <body> content here... -->
</body>
</html>
```

- The includes should exist in their own folder, always in the same location, nested under the `inc/modules` directory.
### Example 

```text
inc/
|-- modules
|   |-- autoedge
|   |   |-- commercial-home.aspx
|   |   |-- group-home.aspx
|   |   `-- leisure-home.aspx
```


- Use Session variables and inline vb to dynamically set cms content (eg banner folder references).

### Example 

#### ❌ Statically Set CMS Banner Folder

```html
<script runat="server">

  ReadOnly _cogCmsHomeBanners As List(Of CogCmsBanner) = CmsBannersService.GetBannersByFolderNodeId(56008)

</script>
```

#### ✅ Dynamic CMS Banner Folder from Session Variable

```html

<%

  Dim _cogCmsHomeBanners As List(Of CogCmsBanner) = CmsBannersService.GetBannersByFolderName(Session("HeroFolderName"))

%>

```


- Override Session variables from inside the Parasol Content Controls. This allows us to set segment-specific values that will, for example, allos us to point to different banner folders for different parasol segments.
### Example 

```html

<!-- Set Session variables with default value -->
<%
session("HeroFolderName") = "Hero Banners - Group"
%>

<COG:ParasolContentSwitcher runat="server">
  <!-- Overrides session variables with Segment specific values -->
  <COG:ParasolContent runat="server" SegmentId="293">
    <!-- Parasol Segment 293: New Leisure -->
    <%
    session("HeroFolderName") = "Hero Banners - Group - New Leisure Segment"
    %>
  </COG:ParasolContent>

</COG:ParasolContentSwitcher>

```


- For the direct parent of all sections on a page, set the display type to flex. 
  
### Example

```html

<!-- the parent of all page sections that span 100% of the width uses a display flex -->

<main class="d-flex flex-column">

	<!-- the page sections that span 100% of the width are ordered with flex order 
	which is dyanmically set within the parasol content controls for each segment 
	-->
	<section class="ae-hero"></section>
	<section class="ae-brands"></section>
	<section class="ae-search"></section>
	<section class="ae-featured"></section>
	
</main>

```

- Use an inline style tag to set segment specific-styles, including the flex order of the various sections on the page (as these often need to be re-ordered for different segments).

### Example

```html

<!-- Default segment with default flex order or content sections -->
<COG:ParasolContentSwitcher runat="server">

  <COG:ParasolContent runat="server" >
    <style>
        .ae-hero { order: 1; }
        .ae-brands { order: 2; }
        .ae-search { order: 3; }
        .ae-featured { order: 4; }
    </style>
    
  </COG:ParasolContent>
  <!-- An Example Segment using SegmentId property -->
  <!-- Sets Segment specific flex order or content sections -->
  <COG:ParasolContent runat="server" SegmentId="293">
    <!-- Parasol Segment 293: New Leisure -->
    <style>
        .ae-hero { order: 1; }
        .ae-brands { display: none; }
        .ae-search { order: 3; }
        .ae-featured { order: 2; }
    </style>
  </COG:ParasolContent>

</COG:ParasolContentSwitcher>

```


## Example Include


```html

<!-- Set session variables with defaults values -->
<%
session("TsDefaultTitle") = ""
session("TsStaticQuery") = ""
session("TsVehicleType") = ""
session("TsSearchUrl") = "/home"
session("TsRedirectPage") = ""

session("HeroFolderName") = "Hero Banners - Group"
session("FeaturedActive") = "0"
session("ServiceBG") = "bg-primary"
session("ServiceLink") = "/aftersales/"
%>


<!-- Default segment with default flex order or content sections -->
<COG:ParasolContentSwitcher runat="server">
  <COG:ParasolContent runat="server" >
    <style>
        .ae-hero { order: 1; }
        .ae-brands { order: 2; }
        .ae-search { order: 3; }
        .ae-featured { order: 4; }
        .ae-grid { order: 5; }
        .ae-reviews { order: 6; }
        .ae-why-choose { order: 7; }
        .ae-contact { order: 8; }
        .ae-service { display: none; }
        .ae-new-commercial { display: none; }
        .ae-new-leisure { display: none; }
    </style>
    
  </COG:ParasolContent>

  <!-- An Example Segment using SegmentId property -->
  <!-- Overrides session variables with Segment specific values, where needed -->
  <!-- Sets Segment specific flex order or content sections -->
  <COG:ParasolContent runat="server" SegmentId="293">
    <!-- Parasol Segment 293: New Leisure -->
    <%
    session("HeroFolderName") = "Hero Banners - Group - New Leisure Segment"
    session("FeaturedActive") = "0"
    %>

    <style>
        .ae-hero { order: 1; }
        .ae-brands { order: 2; }
        .ae-search { order: 3; }
        .ae-new-leisure { order: 4; }
        .ae-grid { order: 5; }
        .ae-featured { order: 6; }
        .ae-reviews { order: 7; }
        .ae-why-choose { order: 8; }
        .ae-contact { order: 9; }
        .ae-service { display: none; }
        .ae-new-commercial { display: none; }
    </style>
  </COG:ParasolContent>


</COG:ParasolContentSwitcher>

<!-- An debug script logging out session variable autoedgeSegment and ParasolTracking.VisitorPrimarySegment to the dev tools console -->
<script>
  console.log("You are viewing: <%= Session("autoedgeSegment") %>")
  console.log("VisitorPrimarySegment: <%=ParasolTracking.VisitorPrimarySegment %>")
</script>



```


