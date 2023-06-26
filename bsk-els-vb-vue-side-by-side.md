# VB and Vue Template Syntax Side by Side

## Iterating over a collection

### VB

```html
<% For Each banner In _cogCmsHomeBanners %>
<div>
    <p>
        <%=banner.BannerText %>
    </p>
</div>
<% Next %>
```

### Vue

```html
<div v-for="(banner, index) in banners" :key="index">
  <p>{{ banner.BannerText }}</p>
</div>

```


## Conditional Rendering Example 1 

### VB

```html
<% If _cogCmsHomeBanners.Count > 0 Then %>
<div>
    <p>
        <%=banner.BannerText %>
    </p>
</div>
<% End If %>
```

### Vue

```html

<div v-if="banners.length > 0">
  <p>{{ banner.BannerText }}</p>
</div>
    
```

## Conditional Rendering Example 2 

### VB

```html
<% If _cogCmsHomeBanners.Count > 0 Then %>
<div>
    <p>
        <%=banner.BannerText %>
    </p>
</div>
<% Else %>
<div>
    <p>
        No banners
    </p>
</div>

<% End If %>
```

### Vue

```html

<div v-if="banners.length > 0">
  <p>{{ banner.BannerText }}</p>
</div>
<div v-else>
  <p>No banners</p>
</div>
    
```

## Conditional Rendering Example 3

### VB

```html
<% 
    Dim cssClass As String = ""
    If _cogCmsHomeBanners.Count > 0 Then
        cssClass = "has-banners"
    End If
%>
<button class="<%= cssClass %>">Click Me</button>
```

### Vue

```html

<button :class="{'has-banners': banners.length > 0}">Click Me</button>
       
```

## Checking for Null / Falsy Values

### VB

```html

 <% If Not String.IsNullOrEmpty(banner.BannerText) Then %>
<div>
    <p>
        <%=banner.BannerText %>
    </p>
</div>
<% End If %>
```

### Vue

```html

<div v-if="banner.BannerText">
  <p>{{ banner.BannerText }}</p>
</div>
        
```

## Rendering Data

### VB

```html

<div>
    <p>
        <%=banner.BannerText %>
    </p>
</div>

```

### Vue

```html

<div>
  <p>{{ banner.BannerText }}</p>
</div>

```
