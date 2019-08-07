# VirusTotal2Prefetch
Based upon this: https://github.com/jgstew/tools/tree/master/JS/VirusTotal2Prefetch

The idea is to take the results of a file analysis on VirusTotal and turn it into a BigFix Prefetch using JavaScript to scrape the page. (to be used in a bookmarklet or similar)



### SHA1

Found using the Chrome Dev Tools "Copy JS Path" option:

`document.querySelector("body > vt-virustotal-app").shadowRoot.querySelector("#authChecker > file-view").shadowRoot.querySelector("#details").shadowRoot.querySelector("div > vt-ui-expandable:nth-child(1) > span > vt-ui-key-val-table").shadowRoot.querySelector("div > div > div:nth-child(2) > div > a:nth-child(2)").text.trim()`

### SHA256

`document.querySelector("body > vt-virustotal-app").shadowRoot.querySelector("#authChecker > file-view").shadowRoot.querySelector("#details").shadowRoot.querySelector("div > vt-ui-expandable:nth-child(1) > span > vt-ui-key-val-table").shadowRoot.querySelector("div > div > div:nth-child(3) > div > a:nth-child(2)").text.trim()`


### Filename

`document.querySelector("body > vt-virustotal-app").shadowRoot.querySelector("#authChecker > file-view").shadowRoot.querySelector("#details").shadowRoot.querySelector("div > vt-ui-expandable:nth-child(5) > span > vt-ui-simple-expandable-list").shadowRoot.querySelector("ul > li > span:nth-child(3)").textContent.trim()`
