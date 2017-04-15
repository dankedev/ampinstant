[logo]: https://raw.githubusercontent.com/dankedev/ampinstant/master/logo.svg "Logo Title Text 2"

#Facebook Comments for Google AMP (un-official)

The comments plugin lets people comment on content on your site using their Facebook account. People can choose to share their comment activity with their friends (and friends of their friends) on Facebook as well. The comments plugin also includes built-in moderation tools and social relevance ranking.

But...

Actually Facebook not yet support AMP. You can implemented the Facebook Comment by follow this step.

---
##Before you start
* If you haven't done so already, you'll want to familiarize yourself with Google's [What Is AMP](https://www.ampproject.org/docs/get_started/about-amp.html)? and [Create Your First AMP Page](https://www.ampproject.org/docs/get_started/create.html).
* Make Sure You have Facebook Account :p. And Make an Faebook APP. Read the [Quickstart Guide](https://developers.facebook.com/docs/) For more informations
* Make sure you can host the installation code on two different domains.


## How to install

1. Create and host the following Universal Code file on a different domain than where you intend to load Facebook Comments for AMP. This will be the URL that you will provide to the src attribute in step 3 below.
```html
<div id="fbkomentar" class="fb-comments" data-href="" data-width="100%" data-numposts="5"></div>
<div id="fb-root"></div>
<script>
    function getQueryVariable(variable) {
        var query = window.location.search.substring(1);
        var vars = query.split("&");
        for (var i=0;i<vars.length;i++) {
            var pair = vars[i].split("=");
            if(pair[0] == variable){return pair[1];}
        }
        return(false);
    }
    function AMPinstantData() {
        document.getElementById("fbkomentar").setAttribute('data-href',getQueryVariable('url') );
    }
    window.onload = AMPinstantData;

    (function(d, s, id) {
    var js, fjs = d.getElementsByTagName(s)[0];
    if (d.getElementById(id)) return;
    js = d.createElement(s); js.id = id;
    js.src = '//connect.facebook.net/en_US/sdk.js#xfbml=1&version=v2.8&appId=' + getQueryVariable("appid");
    fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>
```

2. Refer to the `amp-iframe` documentation and add the required `amp-iframe` script to your document's <head>. :
```html
<script async custom-element="amp-iframe" src="https://cdn.ampproject.org/v0/amp-iframe-0.1.js"></script>
```
3. Place the following `<amp-iframe>` element anywhere within the `<body>` of your AMP page. It will likely make sense to place it at the end of your article content, where ever you would your audience should engage further after reading.

```html
<amp-iframe width=600 height=140
            layout="responsive"
            sandbox="allow-scripts allow-same-origin allow-modals allow-popups allow-forms"
            resizable
            src="https://example.com/amp?appid={YOUR_FACEBOOK_APP_ID}&url={YOUR_CURRENT_URL}">
</amp-iframe>
```
4. Replace `{YOUR_FACEBOOK_APP_ID}` with your Facebook App Id that you have registered before. and `[YOUR_CURRENT_URL`] with current URL that will be commented. If your are using @WordPress you can use `<?php echo get_the_permalink();?>`