# Alerts
 
## Summary

The Alerts component presents important feedback or information to users either
in response to their actions or upon page load.

## Getting started

To view the demo:

* git clone

  `https://github.com/Pearson-Higher-Ed/alerts.git`
* install the dependencies:

  `npm i` <br />
  `npm run copy-utils` <br />
  `npm run build`
* start the server:

  `npm start`
* view in the browser:

  `http://localhost:8081/demo/`

## Triggering an Alert

To trigger an alert, dispatch the `triggerAlert` event with valid `alertType`,
`alertTitle`, `alertMessage` and a unique `id` for each instance of the alert.
Valid `alertType`'s are currently strings of 'Success', 'Error' and 'Information'. `alertTitle` and `alertMessage` accept strings.

For example:

```js

  document.body.dispatchEvent(new CustomEvent('triggerAlert', {
      "detail":{
        "alertList":[{
          "id"          : new Date().getTime(),
          "alertType"   : "Success",
          "alertTitle"  : "Your title",
          "alertMessage": "your alert message here"
        }]
      }
  }));

```

Dispatch `clearAlert` to clear the array of events.

For example:

```js

  document.body.dispatchEvent(new CustomEvent('clearAlert'));

```

## Polyfills

The Alerts Component works on an evented API which uses `CustomEvent`.  Dispatch an event of
`triggerAlert` with the `alertType` and `alertMessage` to display an alert.

Due to the use of `CustomEvent`, a polyfill is needed to support IE:

```
<script src="https://cdn.polyfill.io/v2/polyfill.js?features=CustomEvent</script>
```

In addition, this component uses React Intl which relies on the <a href="http://www.ecma-international.org/ecma-402/1.0/">ECMAScript Internationalization API</a>.
This API was not supported in the Safari browser until version 10. If you're supporting
an older version of Safari, this polyfill is needed, with mentions for each
language you are supporting (example below supports English, French):

```
<script src="https://cdn.polyfill.io/v2/polyfill.js?features=Intl.~locale.en,Intl.~locale.fr"></script>
```

The demo's HTML page combines these:

```
<script src="https://cdn.polyfill.io/v2/polyfill.js?features=CustomEvent,Intl.~locale.en,Intl.~locale.fr"></script>
```

Add whichever polyfills you need to the page rendering this component.

## Next Step

If you are a contributor to this component's development, see guidance on [contributing](README.contribute.md).
