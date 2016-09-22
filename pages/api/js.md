---
title: Javascript Library
permalink: /api/js
---
# Javascript Library and API

***Should you read this?** This is all about the javascript library and API.  If you're using the embedded paywall or 
any other client-side features, then yes, yes you should read this.  If not, you don't NEED to read it - but you might still
enjoy it. I mean, people enjoy long technical documentation, right?*

## Configuration of the Access API Key

In order to use the Javascript library, you must have a public "Access API" key.  You can create that by following
[these instructions](https://wallit.desk.com/customer/portal/articles/2577381-creating-or-updating-your-access-api-key). 
Remember to add your domain in the "Allowed Origins" field otherwise the browser security will
restrict the Wallit javascript from executing.  If you have multiple paywalls for different portions of your site, you 
will need to use the corresponding Access API Key for that paywall.

## Adding the Javascript Library to Your Page

The javascript library should be added on each individual page that you want tracked and managed by Wallit.  (Even if a 
page is not a resource you might charge for, then add the Free pricing model to it.  This will make your analytics and 
reports the most accurate.)  If you're unsure if a page should have the Wallit javascript on it, you can contact us and 
we can help direct your efforts.  Adding this javascript library to your pages is not necessary if you're using server-side
protection only.

Insert the script `https://cdn.wallit.io/paywall.min.js` in the `<head>` of your page.  Immediately following it, add
the initialization and any other configuration options in another script block.  **It's important to add these to the head
element of your page.** We do some asynchronous requests that should be kicked off as soon as possible.  If you put this 
code further down in the body of the page, your user experience may suffer and the execution may not be predictable.

> When using some automated tools to analyze your page speed and performance, Wallit might be the target of a negative
marking. We understand - but we're not all that evil!  Every rule for performance has some exceptions, and proper protection
of content using Wallit is one of them. We care about performance and keep an eye on it; we don't want to slow down your site.

Enough of this talk! Show me the code!!

```html
<head>
  <title>Our Website</title>
  <script src="https://cdn.wallit.com/paywall.min.js"></script>
  <script type="text/javascript">
    wallit.paywall.init('b865156f-9e0d-48b6-a2a0-097456f689ec');
  </script>
</head>
```

The only exciting thing here is the call to `wallit.paywall.init()` - so we'll talk about that next.

## Javascript Library Initialization

All of the configuration options that you want to specify are passed in as a second parameter of the `init()` method call as
a standard javascript object.  For example:

```javascript
wallit.paywall.init('b865156f-9e0d-48b6-a2a0-097456f689ec', {
    "mobileMaxWidth": 300
});
```

**Important** While most of the configuration options for this paywall can be specified in the Manage UI, any options sent 
using the configuration parameter override them.  This is cool for you, dear developer - but don't forget about any people 
in your company that might be making changes to the Manage UI, and expecting things to change in the paywall. If you override 
them with the code, they might not get their desired results.  Because of this, we suggest applying your changes to the paywall
settings in the Manage UI solely - unless it's absolutely necessary to override them in the code.

So, let's take a look at all the key/value pairs of this configuration object!

### Javascript Library Initialization Options

The following table illustrates the options to the javascript configuration object for the second parameter of the `init()` method call.

| Key | Description | Requirements | Default Value |
| --- | ------------| -------------| --------------|
| resourceKey | The external key or resource key used to identify this resource in Wallit. | <= 50 characters, a-z, A-Z, 0-9, - allowed | The right-most 50 characters of the current URL.  Non-supported characters will be replaced with a dash (-). |

<hr>
<br><br><br>

<style>
    .option-description > div a {
        text-transform: inherit;
        border-radius: 0;
        box-shadow: none;
    }
    .option-description > div a.active {
        border-bottom: 4px solid #80deea;
        box-shadow: none;
    }
    .option-description > div a:hover:not(.active) {
        border-bottom: 4px solid #aaaaaa;
        box-shadow: none;
    }
    
    .option-description .row {
        margin-top: 1rem;
    }
    .option-description h6 {
        font-weight: bold;
    }
</style>

<div class="option-description card">
    <div>
        <a href="#" class="active btn blue-grey darken-2"><code>resourceKey</code></a>
        <a href="#" class="btn-flat">example</a>
    </div>
    <section class="card-content">
        <p>The external key or resource key used to identify this resource in Wallit.</p>
        <div class="row">
            <div class="col s12 m6">
                <ul class="collection with-header">
                  <li class="collection-header"><h6>Requirements</h6></li>
                    <li class="collection-item"><= 50 characters</li>
                <li class="collection-item">allowed characters: <code>a-z</code>, <code>A-Z</code>, <code>0-9</code>, <code>-</code></li>
              </ul>
            </div>
            <div class="col s12 m6">
            <ul class="collection with-header">
                              <li class="collection-header"><h6>Default Value</h6></li>
                                <li class="collection-item">The right-most 50 characters of the current URL.  Non-supported characters will be replaced with a dash (-).</li>
                          </ul>
            </div>
        </div>
    </section>
</div>