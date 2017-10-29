<p align="center">
  <br>
  <img width="200" height="200" src="./awesome-storage-logo.png" alt="logo of awesome-web-storage repository">
  <br>
  <br>
</p>

## awesome-web-storage [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

> Everything you need to know about Client-side Storage.

### Table of Contents

- [Introduction](#introduction)
- [Browser Support](#browser-support)
- [Cookies](#cookies)
    - [Pros](#pros)
    - [Cons](#cons)
    - [API](#api)
    - [Useful resources](#resources---more-on-cookies)
- [LocalStorage](#localstorage)
    - [Pros](#pros-1)
    - [Cons](#cons-1)
    - [API](#api-1)
    - [Useful resources](#resources---more-on-localstorage)
- [SessionStorage](#sessionstorage)
    - [Pros](#pros-2)
    - [Cons](#cons-2)
    - [API](#api-2)
    - [Useful resources](#resources---more-on-sessionstorage)
- [Comparison Table](comparison-table)
- [PostMessage](#worth-mentioning-api-for-tackling-cross-origin-restriction)
    - [Pros](#pros-3)
    - [Cons](#cons-3)
    - [API](#api-3)
    - [Security concerns](#security-concerns)
    - [Useful resources](#resources---more-on-postmessage)
- [FAQs](#faqs)
- [Contributing](#contributing-guidelines)
- [License](#license)

### Introduction

#### What is Web Storage

**Web storage**, sometimes known as *DOM storage (Document Object Model storage)*, provides web application software methods and protocols used for storing data in a web browser.

Web storage is being standardized by the [World Wide Web Consortium (W3C)](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium). It was originally part of the [HTML5](https://en.wikipedia.org/wiki/HTML5) specification, but is now in a separate specification.

Modern websites and web applications these days are becoming smarter than before and to achieve such smartness, the data storage system plays a very crucial role. Be it storing visitors' data & settings or any kind of information, web-storage is a breakthrough in the history of web applications. It offers a very basic need of storing persistent data in the browser itself which has literally spurred up its application from game-changing novelty to must-have features.

Usually, this kind of data doesn't need a well-organized backend database. The purpose of the data varies as per the website/webapp requirements. Different pages of the same website need to share data among themselves to behave alike and perfectly. This sharing of data among windows/tabs is very common these days and most of the sites or web apps use it for various jobs like User Authentication, Personalization (showing different views to a new visitor and on subsequent visits), Tracking user behavior, etc.

Before HTML5, storing application level data was possible only using cookies. Cookies can store up to 4KB of data, including the bytes consumed by the cookie name. This domain-specific data is sent along with every browser request. With the advent of HTML5, it's much easier now to store structured data on the client-side securely and faster than ever. HTML5 introduced the concept of Web Storage. Web storage can be viewed simplistically as an improvement on cookies, providing much greater storage capacity. HTML5 introduces two such web storage mechanisms: LocalStorage and SessionStorage. There are so many limitations in using cookies which can now be overcome using web storage.

There's no term as "Perfectly Secured Persistent Storage" available in the browsers as any type of storage system( persistent or non-persistent) can be manually tweaked by the end-user(assuming she knows a bit of geeky stuff :P).

#### Web Storage concepts and usage

The two mechanisms within Web Storage are as follows:

1. `sessionStorage` maintains a separate storage area for each given origin that's available for the duration of the page session (as long as the browser is open, including page reloads and restores).
2. `localStorage` does the same thing, but persists even when the browser is closed and reopened.

#### Web Storage interfaces

**[Storage](https://developer.mozilla.org/en-US/docs/Web/API/Storage)**
> Allows you to set, retrieve and remove data for a specific domain and storage type (session or local.)

**[Window](https://developer.mozilla.org/en-US/docs/Web/API/Window)**
> The Web Storage API extends the `Window` object with two new properties — `Window.sessionStorage` and `Window.localStorage` — which provide access to the current domain's session and local Storage objects respectively, and a `Window.onstorage` event handler that fires when a storage area changes (e.g. a new item is stored.)

**[StorageEvent](https://developer.mozilla.org/en-US/docs/Web/API/StorageEvent)**
> The storage event is fired on a document's Window object when a storage area changes.

### Browser Support

| [<img src="media/edge.png" alt="IE / Edge" width="16px" height="16px" />](https://caniuse.com/#search=storage)</br> IE / Edge | [<img src="media/firefox.png" alt="Firefox" width="16px" height="16px" />](https://caniuse.com/#search=storage)</br> Firefox | [<img src="media/chrome.png" alt="Chrome" width="16px" height="16px" />](https://caniuse.com/#search=storage)</br> Chrome | [<img src="media/safari.png" alt="Safari" width="16px" height="16px" />](https://caniuse.com/#search=storage)</br> Safari | [<img src="media/opera.png" alt="Opera" width="16px" height="16px" />](https://caniuse.com/#search=storage)</br> Opera |
| :---: | :---: | :---: | :---: | :---: |
| [IE8+, Edge12+](https://caniuse.com/#search=storage) | [3.5+](https://caniuse.com/#search=storage) | [4+](https://caniuse.com/#search=storage) | [4+](https://caniuse.com/#search=storage) | [11.5+](https://caniuse.com/#search=storage)

### Different Storage APIs

Following are various storage techniques which HTML5 storage provides. Each technique has its own pros and cons.

#### [Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)

> An `HTTP cookie` (web cookie, browser cookie) is a small piece of data that a server sends to the user's web browser. The browser may store it and send it back with the next request to the same server. Typically, it's used to tell if two requests came from the same browser — keeping a user logged-in, for example. It remembers stateful information for the [stateless](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#HTTP_is_stateless_but_not_sessionless) HTTP protocol.

##### Pros:

* Session Management - Easy to use with logins, shopping carts, game scores, or anything else the server should remember

##### Cons:

* The 4K limit is for the entire cookie, including name, value, expiry date etc. To support most browsers, keep the name under 4000 bytes, and the overall cookie size under 4093 bytes.

* The data is sent back to the server for every HTTP request (HTML, images, JavaScript, CSS, etc) - increasing the amount of traffic between client and server.

* Typically, the following are allowed:

    * 300 cookies in total
    * 4096 bytes per cookie
    * 20 cookies per domain
    * 81920 bytes per domain(Given 20 cookies of max size 4096 = 81920 bytes.)

##### API

1. `Read`

    *Reading all cookies accessible from the domain*

    ```js
    var allCookies = document.cookie;
    ```

2. `Write`

    *Writing a new cookie on a domain*

    ```js
    document.cookie = newCookie;
    ```

    As mentioned in the [mdn docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/cookie), any of the following cookie attribute values can optionally follow the key-value pair, specifying the cookie to set/update, and preceded by a semi-colon separator:

    * `;path=path` - (e.g., '/', '/mydir') If not specified, defaults to the current path of the current document location.

    * `;domain=domain` - (e.g., 'example.com' or 'subdomain.example.com').

    * `;max-age=max-age-in-seconds` - (e.g., 60\*60\*24\*365 or 31536000 for a year)

    * `;expires=date-in-GMTString-format` - If not specified it will expire at the end of a session.

    * `;secure` - Cookie to only be transmitted over secure protocol as `https`. Before `Chrome 52`, this flag could appear with cookies from `http` domains.


##### Resources - more on cookies

- Blogs
    - [Types of cookies Google uses](https://www.google.com/policies/technologies/types/)
    - [Securing cookies](https://www.owasp.org/index.php/Session_Management_Cheat_Sheet#Cookies)
    - [HTTP Cookies explained](https://www.nczonline.net/blog/2009/05/05/http-cookies-explained/)
- Libraries
    - [js-cookie](https://github.com/js-cookie/js-cookie)
    - [Cookies](https://github.com/ScottHamper/Cookies)
    - [AngularJS Cookies](https://github.com/ivpusic/angular-cookie)
    - [ReactJs Cookies](https://github.com/reactivestack/cookies)
    - [Vuejs Cookies](https://github.com/alfhen/vue-cookie)
- Browser Extensions
    - [EditThisCookie](http://www.editthiscookie.com/)(For Chrome) - Open source Chrome extension which does it all!
    - [Cookies](https://chrome.google.com/webstore/detail/cookies/iphcomljdfghbkdcfndaijbokpgddeno?hl=en)(For Chrome) - A powerful and easy-to-use Cookie Editor.
    - [Cookie Inspector](https://chrome.google.com/webstore/detail/cookie-inspector/jgbbilmfbammlbbhmmgaagdkbkepnijn?hl=en)(For Chrome) - Edit and create cookies right in the Developer Tools.
    - [EditThisCookie](https://addons.mozilla.org/en-US/firefox/addon/editthiscookieaddon/)(For Firefox)
    - [Cookies Manager+](https://addons.mozilla.org/en-US/firefox/addon/cookies-manager-plus/) - To view, edit and create new cookies.
    - [Vanilla Cookie Manager](https://chrome.google.com/webstore/detail/vanilla-cookie-manager/gieohaicffldbmiilohhggbidhephnjj?hl=en)(For Chrome) - A Cookie Whitelist Manager that helps protect your privacy. Automatically removes unwanted cookies.

#### [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

> The read-only `localStorage` property allows you to access a `Storage` object for the `Document`'s origin; the stored data is saved across browser sessions. `localStorage` is similar to `sessionStorage`, except that while data stored in `localStorage` has no expiration time, data stored in `sessionStorage` gets cleared when the page session ends — that is, when the page is closed.

##### Pros:

* If you look at the Mozilla source code it can be seen that 5120KB (5MB which equals 2.5 Million characters on Chrome) is the default storage size for an entire domain. This gives you considerably more space to work with than a typical 4KB cookie.

* The data is not sent back to the server for every HTTP request (HTML, images, JavaScript, CSS, etc) - reducing the amount of traffic between client and server.

* The data stored in localStorage persists until explicitly deleted. Changes made are saved and available for all current and future visits to the site.

* Structured data can be stored but it has to be stringified before storing.

* Simple API to save, update, and delete data.

##### Cons:

* It works on same-origin policy. So, data stored will only be available on the same origin.

* It stores everything as a string.

##### API

1. `setItem`

    | setItem | Description |
    | --- | --- |
    | method      | localStorage.setItem(key, value) |
    | params      | key(String/Number),<br>value(Number/String),<br>though it accepts other types, the value is always stored as a string, so, stringifying data before storing is preferred and the best way to avoid errors while reading |
    | description | adds the key to the storage with the value, or update the key's value if it already exists. |
    | example     | localStorage.setItem('test', document.getElementById('js-btn').value); |

2. `getItem`

    | getItem | Description |
    | -- | -- |
    | method | localStorage.getItem(key) |
    | params | key(String/Number) |
    | description | returns the value of the key passed. |
    | example | localStorage.getItem('test') |

3. `removeItem`

    | removeItem | Description |
    | -- | -- |
    | method | localStorage.removeItem(key) |
    | params | key(String/Number) |
    | description | removes the key from the storage. |
    | example | localStorage.removeItem('test') |

4. `clear`

    | clear | Description |
    | -- | -- |
    | method | localStorage.clear() |
    | params | None |
    | description | empties all the keys out of the storage. |
    | example | localStorage.clear() |

5. `key`

    | key | Description |
    | -- | -- |
    | method | localStorage.key(n) |
    | params | n(a Number) |
    | description | returns the name of the nth key in the storage. |
    | example | localStorage.key(0) |

6. `length`

    | length | Description |
    | -- | -- |
    | property | localStorage.length |
    | description | returns the length of all the keys |
    | example | localStorage.length |

##### Resources - more on localStorage

- Blogs
    - [Storing Data on The Client with LocalStorage](http://blog.teamtreehouse.com/storing-data-on-the-client-with-localstorage)
    - [Storing data in the browser with the HTML5 localStorage API](https://toddmotto.com/storing-data-in-the-browser-with-the-html5-local-storage-api/)
    - [Basket.js: A JavaScript loader with localStorage-based script caching](http://badassjs.com/post/40850339601/basketjs-a-javascript-loader-with)
- Libraries
    - [angular-local-storage](https://github.com/grevory/angular-local-storage) - An AngularJS module that gives access to the browsers local storage with cookie fallback.
    - [react-native-localstorage](https://github.com/sunnylqm/react-native-storage) - Local storage wrapper for both react-native and browser.
    - [vue-local-storage](https://github.com/pinguinjkeke/vue-local-storage) - Vue.js localStorage plugin with types support.
    - [localForage](https://github.com/localForage/localForage) - Offline storage, improved. Wraps IndexedDB, WebSQL, or localStorage using a simple but powerful API.
    - [basket.js](https://github.com/addyosmani/basket.js) - A script and resource loader for caching & loading files with localStorage.
    - [secure-ls](https://github.com/softvar/secure-ls) - Secure localStorage data with high level of encryption and data compression.
- Browser Extensions
    - [HTML5 Storage Manager All in One](https://chrome.google.com/webstore/detail/html5-storage-manager-all/giompennnhheakjcnobejbnjgbbkmdnd?hl=en) - Complete Storage Manager Extension Ever!

#### [sessionStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage)

> The `sessionStorage` property allows you to access a session `Storage` object for the current origin. sessionStorage is similar to `Window.localStorage`, the only difference is while data stored in localStorage has no expiration set, data stored in sessionStorage gets cleared when the page session ends. A page session lasts for as long as the browser is open and survives over page reloads and restores. **Opening a page in a new tab or window will cause a new session to be initiated**, which differs from how session cookies work.

##### Pros:

* [Same as localStorage](#api-1)

* Data can only be saved per window (or tab in browsers like Chrome and Firefox). Data saved is available for the current page, as well as for the future visits to the site on the same window. Once the window is closed, the storage is deleted.

##### Cons:

* The data is available only inside the window/tab in which it was set.

* The data is non-persistent i.e. it will be lost once the window/tab is closed.

* Like `localStorage`, it also works on same-origin policy. So, data stored on one protocol/domain/port will not be available for different protocol/domain/port.

##### API

1. `setItem`

    | setItem | Description |
    | --- | --- |
    | method      | sessionStorage.setItem(key, value) |
    | params      | key(String/Number),<br>value(Number/String),<br>though it accepts other types, the value is always stored as a string, so, stringifying data before storing is preferred and the best way to avoid errors while reading |
    | description | adds the key to the storage with the value, or update the key's value if it already exists. |
    | example     | sessionStorage.setItem('test', document.getElementById('js-btn').value); |

2. `getItem`

    | getItem | Description |
    | -- | -- |
    | method | sessionStorage.getItem(key) |
    | params | key(String/Number) |
    | description | returns the value of the key passed. |
    | example | sessionStorage.getItem('test') |

3. `removeItem`

    | removeItem | Description |
    | -- | -- |
    | method | sessionStorage.removeItem(key) |
    | params | key(String/Number) |
    | description | removes the key from the storage. |
    | example | sessionStorage.removeItem('test') |

4. `clear`

    | clear | Description |
    | -- | -- |
    | method | sessionStorage.clear() |
    | params | None |
    | description | empties all the keys out of the storage. |
    | example | sessionStorage.clear() |

5. `key`

    | key | Description |
    | -- | -- |
    | method | sessionStorage.key(n) |
    | params | n(a Number) |
    | description | returns the name of the nth key in the storage. |
    | example | sessionStorage.key(0) |

6. `length`

    | length | Description |
    | -- | -- |
    | property | sessionStorage.length |
    | description | returns the length of all the keys |
    | example | sessionStorage.length |

##### Resources - more on sessionStorage

- Blogs
    - [Introduction to sessionStorage](https://www.nczonline.net/blog/2009/07/21/introduction-to-sessionstorage/)
    - [Web Storage API: Local Storage & Session Storage](https://www.codebyamir.com/blog/web-storage-api-localstorage-sessionstorage)
    - [Sharing sessionStorage between tabs for secure multi-tab authentication](https://blog.guya.net/2015/06/12/sharing-sessionstorage-between-tabs-for-secure-multi-tab-authentication/)
- Libraries
    - [sessionstorage](https://github.com/unshiftio/sessionstorage) - sessionStorage API which gracefully degrades to window.name & cookies when not available.
    - [ngStorage](https://github.com/gsklee/ngStorage) - localStorage and sessionStorage done right for AngularJS.
    - [react-webstorage](https://github.com/sterpe/react-webstorage) - Use webStorage or a webStorage polyfill as a React store
- Browser Extensions
    - [HTML5 Storage Manager All in One](https://chrome.google.com/webstore/detail/html5-storage-manager-all/giompennnhheakjcnobejbnjgbbkmdnd?hl=en) - Complete Storage Manager Extension Ever!

<hr>

### Comparison Table


| Web Storage                       |       cookies          |       localStorage          |       sessionStorage        |
| --                                | :---:                  | :---:                       | :---:                       |
| **Size limit**                    |  Max 4kb (~2K chars)   |      Max 5mb (~2M chars)    |     Max 5mb (~2M chars)     |
| **Data Storage**                  |       FileSytem        |         FileSytem           |         FileSytem           |
| **Payload**                       |    In every HTTP req   |          Nothing            |          Nothing            |
| **API**                           |         Fair           |          Simple             |          Simple             |
| **Persistent**                    |         Yes            |           Yes               |            No               |
| **Data Format**                   |        String          |          String             |          String             |
| **Same-origin**                   |         Yes            |           Yes               |           Yes               |
| **Cross-origin**                  |         No             |           No                |           No                |
| **Browser Sipport**               |         All            | [IE8+, Edge12+, Firefox3.5+, Safari4+, Opera11.5+](https://caniuse.com/#search=storage) | [IE8+, Edge12+, Firefox3.5+, Safari4+, Opera11.5+](https://caniuse.com/#search=storage) |
| **Size limits info**              | [limit](http://browsercookielimits.squawky.net/) | [limit](https://arty.name/localstorage.html) | [limit](https://stackoverflow.com/questions/15840976/how-large-is-html5-session-storage)


#### Worth mentioning API for tackling cross-origin restriction

[postMessage](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage)

> One very interesting API, PostMessage is not a web-storage technique but it's the most efficient and reliable way of communicating between `cross-origin` browser windows/tabs. Along with web-storage APIs, it overcomes the web-storage restrictions of cross-origin.

##### Pros:

* Safely enables cross-origin policy communication.

* As a data point, the WebKit implementation (used by Safari and Chrome) doesn't currently enforce any limits (other than those imposed by running out of memory).

##### Cons:

* Need to open a window from the current window and only then can communicate as long as you keep the windows open.

* Security concerns - Sending strings via postMessage is that you will pick up other postMessage events published by other JavaScript plugins, so be sure to implement a targetOrigin and a sanity check for the data being passed on to the messages listener.

##### API:

```js
otherWindow.postMessage(message, targetOrigin, [transfer]);
```

*otherWindow* - A reference to another window; such a reference may be obtained, for example, using the `contentWindow` property of an `iframe` element, the object returned by [window.open](https://developer.mozilla.org/en-US/docs/Web/API/Window/open), or by named or numeric index on [Window.frames](https://developer.mozilla.org/en-US/docs/Web/API/Window/frames), if you're trying to start the communication from iframe to [parent](https://developer.mozilla.org/en-US/docs/Web/API/Window/parent) window then parent is also a valid reference

*message* - Data to be sent to the other window. The data is serialized using the [structured clone algorithm](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm). This means you can pass a broad variety of data objects safely to the destination window without having to serialize them yourself. [1]

*targetOrigin* - Specifies what the origin of `otherWindow` must be for the event to be dispatched, either as the literal string `"*"` (indicating no preference) or as a URI. If at the time the event is scheduled to be dispatched the scheme, hostname, or port of otherWindow's document does not match that provided in `targetOrigin`, the event will not be dispatched; only if all three match will the event be dispatched. This mechanism provides control over where messages are sent; for example, if `postMessage()` was used to transmit a password, it would be absolutely critical that this argument be a URI whose origin is the same as the intended receiver of the message containing the password, to prevent interception of the password by a malicious third party. **Always provide a specific targetOrigin, not `*`, if you know where the other window's document should be located. Failing to provide a specific target discloses the data you send to any interested malicious site.**

*transfer(Optional)* -  Is a sequence of [Transferable](https://developer.mozilla.org/en-US/docs/Web/API/Transferable) objects that are transferred with the message. The ownership of these objects is given to the destination side and they are no longer usable on the sending side.

##### Security concerns

**If you do not expect to receive messages from other sites, do not add any event listeners for `message` events**. This is a completely foolproof way to avoid security problems.

If you do expect to receive messages from other sites, **always verify the sender's identity** using the `origin` and possibly `source` properties. Any window (including, for example, `http://evil.example.com)` can send a message to any other window, and you have no guarantees that an unknown sender will not send malicious messages. Having verified identity, however, you still should **always verify the syntax of the received message**. Otherwise, a security hole in the site you trusted to send only trusted messages could then open a cross-site scripting hole in your site.

**Always specify an exact target origin, not `*`, when you use postMessage to send data to other windows.** A malicious site can change the location of the window without your knowledge, and therefore it can intercept the data sent using `postMessage`.

##### Resources - more on postMessage:

- Blogs
	- [HTML5's window.postMessage API](https://davidwalsh.name/window-postmessage)
	- [Cross-Domain Messaging With postMessage](http://blog.teamtreehouse.com/cross-domain-messaging-with-postmessage)
	- [The pitfalls of postMessage](https://labs.detectify.com/2016/12/08/the-pitfalls-of-postmessage/)
	- [XSS and App Security through HTML5's PostMessage()](https://community.saas.hpe.com/t5/Protect-Your-Assets/XSS-and-App-Security-through-HTML5-s-PostMessage/ba-p/266645#.WfRDnBNL_GI)
- Libraries
	- [postmate](https://github.com/dollarshaveclub/postmate) - A powerful, simple, promise-based postMessage library.
	- [across-tabs](https://github.com/wingify/across-tabs) - Easy communication between cross-origin browser tabs.
- Browser Extensions
	- [postMessage debugger](https://chrome.google.com/webstore/detail/postmessage-debugger/kjfjellokbmlooidpiaolkpmghbladpi?hl=en) - This extension prints messages sent with postMessage to the console.

### FAQs

1. How to store data that works Cross-Origin too?

    > A combination of `postMessage and localStorage / sessionStorage`

    Using postMessage to communicate between multiple tabs and at the same time using localStorage/sessionStorage in all the newly opened tabs/windows to persist data being passed. Data will be persisted as long as the tabs/windows remain open in case of sessionStorage and in the case of localStorage unless the data is deleted by the system or manually flushing it using dev tools. So, even if the opener tab/window gets closed, the opened tabs/windows will have the entire data even after getting refreshed.

    - [across-tabs](https://github.com/wingify/across-tabs/) - Easy communication between cross-origin browser tabs

### Contributing Guidelines

Please ensure your pull request adheres to the following guidelines:

- Search previous suggestions before making a new one, as yours may be a duplicate.
- Make sure the list is useful before submitting. That implies it has enough content and every item has a good succinct description.
- Make an individual pull request for each suggestion.
- Use [title-casing](http://titlecapitalization.com) (AP style).
- Use the following format: `[List Name](link)`
- Link additions should be added to the bottom of the relevant category.
- New categories or improvements to the existing categorization are welcome.
- Check your spelling and grammar.
- Make sure your text editor is set to remove trailing whitespace.
- The pull request and commit should have a useful title.
- The body of your commit message should contain a link to the repository.

### LICENSE

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Varun Malhotra](http://varunmalhotra.xyz) has waived all copyright and related or neighboring rights to this work.
