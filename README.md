This fork uses different parsing logic that strips characters `'`, `"`, `;`, `)`, `]`, `<`, `>`, `,` from the end of URLs found by parsing raw HTML pages.

It changes the ULRs found in
```html
<body>

<script type="text/JavaScript">

setTimeout(function(){
    location.href = 'https://example.com/app-1.1.1-a.apk';
}, 1000);

</script>

Download hasn't started?
<a href="https://example.com/app-1.1.1-a.apk"> Click here to get latest apk </a>
(This link leads to https://example.com/app-1.1.1-a.apk)

</body>
```
from 
`https://example.com/app-1.1.1-a.apk';`, `https://example.com/app-1.1.1-a.apk">`, and `https://example.com/app-1.1.1-a.apk)` to `https://example.com/app-1.1.1-a.apk`.

The removed characters could be parts of valid URLs, but I need to strip them for my use case.
