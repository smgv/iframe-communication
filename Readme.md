## Data transfer between parent window and iframe window

With Javascript we can transfer data between context i.e. Parent window and Iframe window vice versa. If we open the window in new tab data communication can be done using postMessage() API i.e. cross data communication and data transfer.

## Sending Data from Parent to Iframe

we call `iframe.contentWindow.postMessage(message, targetOrigin)` from parent and we add `message` eventListener in Iframe to receive the message using `event.data` in callback function of addEventListener

### Parent Script

```
<script>
const message = "Hello! From Parent Window"
const iframeEl = const iframe = document.querySelector("iframe");
iframeEl.contentWindow.postMessage(message, '*')
</script>
```

### Iframe Script

```
<script>
window.addEventListener("message", function (event) {
    console.log('Message From Parent', event.data)
})
</script>
```

## Sending Data from Iframe to Parent

we call `window.parent.postMessage(message, targetOrigin)` from iframe and we add `message` eventListener in Parent to receive the message using `event.data` in callback function of addEventListener

### Iframe Script

```
<script>
const message = "Hello! From Iframe Window"
window.parent.postMessage(message, '*')
</script>
```

### Parent Script

```
<script>
window.addEventListener("message", function (event) {
    console.log('Message From Iframe', event.data)
})
</script>
```
