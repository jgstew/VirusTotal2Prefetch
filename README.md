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

### Size

`document.querySelector("body > vt-virustotal-app").shadowRoot.querySelector("#authChecker > file-view").shadowRoot.querySelector("#details").shadowRoot.querySelector("div > vt-ui-expandable:nth-child(1) > span > vt-ui-key-val-table").shadowRoot.querySelector("div > div > div:nth-child(7) > div > a:nth-child(2)").textContent.split('(')[1].split('bytes')[0].trim()`

### URL in Comment?

`document.querySelector("body > vt-virustotal-app").shadowRoot.querySelector("#authChecker > file-view").shadowRoot.querySelector("#report").shadowRoot.querySelector("#community > vt-ui-main-generic-report-community-tab").shadowRoot.querySelector("vt-ui-expandable:nth-child(2) > span > vt-ui-comments-list").shadowRoot.querySelector("vt-ui-comment").shadowRoot.querySelector("#body").textContent.trim()`

**Apply RegEx:**  https://stackoverflow.com/questions/3809401/what-is-a-good-regular-expression-to-match-a-url

`document.querySelector("body > vt-virustotal-app").shadowRoot.querySelector("#authChecker > file-view").shadowRoot.querySelector("#report").shadowRoot.querySelector("#community > vt-ui-main-generic-report-community-tab").shadowRoot.querySelector("vt-ui-expandable:nth-child(2) > span > vt-ui-comments-list").shadowRoot.querySelector("vt-ui-comment").shadowRoot.querySelector("#body").textContent.match(/(https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*))/)[0] || "http_PUT_URL_HERE_"`

this should be improved to handle multiple comments with multiple URLs

### Put it all together:

`'prefetch ' +  + ' sha1:' +  + ' size:' +  + ' ' +  + ' sha256:' +`
