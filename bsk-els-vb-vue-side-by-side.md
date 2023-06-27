# VB and Vue Template Syntax Side by Side


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


## If Statement

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

## If Else Statement

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

## Conditional CSS Class Rendering Example 1

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

## Conditional CSS Class Rendering Example 2

### VB

```html
<%
    Dim cssClass As String = ""
    If _cogCmsHomeBanners.Count > 0 Then
        cssClass = "has-banners"
    Else
        cssClass = "no-banners"
    End If
%>
<button class="<%= cssClass %>">Click Me</button>
```

### VB With If Operator Shorthand


```html
<button class="<%= If(_cogCmsHomeBanners.Count > 0, "has-banners", "no-banners") %>">Click Me</button>
```

### Vue

```html

<button :class="`banners.length > 0 ? 'has-banners' : 'no-banners'`">Click Me</button>

```


## Iterating over an array

### VB

```html
<% For i = 0 To students.Length %>
<div>
    <p>
        <%= students(index - 1) %>
    </p>
</div>
<% Next %>
```

### Vue

```html
<div v-for="i in students.length" :key="i">
  <p>{{ students[i - 1] }}</p>
</div>
```

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
<div v-for="banner in banners" :key="index">
  <p>{{ banner.BannerText }}</p>
</div>

```

## Toggle a Class on Click

### ASPX

```html
<button id="demo">Click Me</button>
<script>
    // JS would likely in src/js for bundling etc but added in script tag for demo purposes
    const button = document.querySelector('#demo');
    button.addEventListener('click', function() {
        this.classList.toggle('active');
    });

</script>
```

### Vue

```html
<button
:class="{ active: isActive }"
@click="isActive = !isActive">Click Me
</button>
```

## Hide and Show an Element on an Event (Click)

### ASPX

```html
<button id="demo">Click Me</button>
<script>
    // JS would likely in src/js for bundling etc but added in script tag for demo purposes
    const button = document.querySelector('#demo');
    button.addEventListener('click', function() {
        this.classList.toggle('d-none');
    });

</script>
```

### Vue

```html
<button
:class="{ 'd-none' : isActive }"
@click="isActive = !isActive">Click Me
</button>
```