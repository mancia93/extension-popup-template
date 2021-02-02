chrome extension template that opens a small popup window when button is clicked


to recieve messages use
```
chrome.runtime.onMessage.addListener((request, sender, sendResponse) => {
  request.message === "give me pictures, please" &&
    getImages().then(sortImages().then(sendImages().then(initialize())));
});
```

to send messages use
```
chrome.runtime.sendMessage({from:"content",message:JSON.stringify(imagesToSend)});
};
```
or
```
chrome.tabs.query({currentWindow: true, active: true}, function (tabs){
        var activeTab = tabs[0];
        chrome.tabs.sendMessage(activeTab.id, {"message": "start"});
       });
 ```