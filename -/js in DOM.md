get text from some table

``` js
[...document.querySelectorAll(".lib-item-var-name")]
.filter(item=>item.innerText.toLowerCase().includes('myalphaweb'))
.map(item => item.innerText)
```

``` bash
"myAlphaWeb_Dev_AzWebDevn"
"myAlphaWeb_Dev_WebDev2n"
"myAlphaWeb_Dev_WebDev3n"
"myAlphaWeb_Dev_WebDev4n"
"myAlphaWeb_Dev_WebDevEDG"
"myAlphaWeb_Dev_WebDevn"
```