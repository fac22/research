

## NODE ARCHITECTURE 🏭

---

### What is the event loop?

---

The Event Loop is one of the most important aspects to understand about `Node.js`

---

The Event loop means that `Node.js` can be:

---

1 - Asynchronous (multiple things can happen at the same time)

<iframe src="https://giphy.com/embed/DYqtZumx2mClizlZZ2" width="250" height="250" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

---

2 - Non-blocking I/O (code that doesn't block other code from running)

<iframe src="https://giphy.com/embed/vzE7csLWN3uRW" width="400" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

---

The event-loop keeps track of whats currently happening and what needs to happen next.

---

🌍 World without the Event Loop:

![](https://i.imgur.com/9CnQ2MS.png)

---

<iframe src="https://giphy.com/embed/13dZpchxFzWjfi" height="300"  frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

Washing, Hoovering and Cooking are all **blocking** the next thing from happening

---

🌍 World with the Event Loop:

![](https://i.imgur.com/7gC48zS.png)

---

A bit like reading two books at once 📚:

![](https://i.imgur.com/xBdxt7L.jpg)

---

### Why should we prefer asynchronous code?

---

- Timeouts are rubbish, no one likes waiting

<iframe src="https://giphy.com/embed/3o7bu3XilJ5BOiSGic" width="200" height="200" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

---

`Node.js` is `asynchronous`, so it doesn't 'block'

---

Blocking code can lead to `timeouts` or appearing as if the page has frozen, which isn't cool.

![](https://i.imgur.com/YLlCyng.png)


---

### How does Node use callbacks to manage asynchronous code?!

---

Callbacks are functions called when a given task completes, which means that other code can run in the meantime.

---

You might remember them from Execute Program tbh.

---

In practice this means that in a web server with thousands (or hundreds of thousands) of requests, you can continue working rather than having to wait for them to finish.

---

This is (obviously) a good thing!

---

It is imperative that you follow the proper error conventions when defining a callback, for consistent code *but also* so that other Node.js users can make sense of your code.

---



### What are the error conventions?

---

Here are the aforementioned error conventions for `asychronous` functions in Node:

---

If there is an error, it will return it as the first argument of the functions callback.

---

If there's no error, the first argument comes back as `null` and the rest of the callback gets returned.

---

```
  // Function
  var isTrue = function(value, callback) {
      if (value === true) {
        callback(null, "Value was true.");
      }else {
        callback(new Error("Value is not true!"));
      }
  }  
  
  
  var callback = function (error, retval) {
      if (error) {
        console.log(error);
        return;
      }
      console.log(retval);
  }
  
  isTrue(false, callback); -> gives only the error - "Value is not true"
  isTrue(true, callback); -> gives null as the first argument and then returns "Value was true"
```



