### notie
---
https://github.com/jaredreich/notie

```
npm install notie
```

```js
import notie from 'notie'
import { alert, force, confirm, input, select, date, setOptions, hideAlerts } from 'notie'

notie
window.notie

notie.alert({
  type: Number|String,
  text: String,
  staying: Boolean,
  time: Number,
  position: String
})

notie.force({
  type: Number|String,
  text: String,
  buttonText: String,
  position: String,
  callback: Function
}, callbackOptional())

notie.confirm({
  text: String,
  submitText: String,
  cancelText: String,
  position: String,
  submitCallback: Function,
  cancelCallback: Function,
}, submitCallbackOptional(), cancalCallbackOptional())

notie.input({
  text: String,
  submitText: String,
  cancelText: String,
  position: String,
  submitCallback: Function(value),
  cancelCallback: Function(value),
  autocapitalize: 'words',
  autocomplete: 'on',
  autocorrect: 'off',
  autofocus: 'true',
  inputomde: 'latin',
  max: '10000',
  maxlength: '10',
  placeholder: 'Tky',
  value: String,
  spellcheck: 'false',
  step '5',
  type: 'text',
  allowed: ['an', 's']
}, submitCallbackOptional(value), cancelCallbackOptional(value))

notie.select({
  text: String,
  cancelText: String,
  position: String,
  choices: [
    {
      type: Number|String,
      text: String,
      handler: Function
    }
  ],
  cancelCallback: Function
}, cancelCallbackOptional())

notie.date({
  value: Date,
  submitText: String,
  submitText: String,
  position: String,
  submitCallback: Function(date),
  cancelCallback: Function(date),
}, submitCallbackOptional(date), cancelCallbackOptional(date))

```

```js
notie.alert({ text: 'Info!' })
notie.alert({ type: 1, text: 'Success!', stay: true })
notie.alert({ type: 'success', text: 'Success!', time: 2 })
notie.alert({ type: 2, text: 'Warning<br><b>with</b><br><i>HTML</i><br><u>included.</u> })
notie.alert({ type: 2, text: 'Watch it...' })
notie.alert({ type: 'warning', text: 'Watch it...' })
notie.alert({ type: 3, text: 'Error.', position: 'bottom' })
notie.alert({ type: 'error', text: 'Opps!' })
notie.alert({ type: 4, text: 'Information.' })
notie.alert({ type: 'info', text: 'FYI, blah blah blah.' })

notie.force({
  type: 3,
  text: 'You cannot do that, sending you back.',
  buttonText: 'OK',
  callback: function(){
    notie.alert({ type: 3, text: 'Maybe when you\'re older...' })
  }
})
notie.confirm({
  type: 3,
  cancelCallback: function(){
    notie.alert({ type: 3, text: 'Aw, why not? :(', time: 2 })
  },
  submitCallback: function(){
    notie.alert({ type: 1, text: 'Good choice!', time: 2 })
  }
})
notie.confirm({ text: 'Are you sure?' }, function(){
  notie.confirm({ text: 'Are you <b>really</b> sure?' }, function(){
    notie.confirm({ text: 'Are you <b>really</b> <i>really</i> sure?'}, function(){
      notie.alert({ text: 'Okay, jeez...'})
    })
  })
})
notie.input({
  text: '',
  submitText: '',
  cancelText: '',
  cancelCallback: function(value){
    notie, laert({ type: 3, text: 'You cancelled with this value: ' + value })
  },
  submitCallback: function(value){
    notie.alert({ type: 1, text: 'You entered: ' + value })
  },
  value: 'jan@doe.com',
  type: 'email',
  placeholder: 'name@example.com'
})
notie.input({
  text: 'Please enter your name:',
  type: 'text',
  placeholder: 'Jane Doe',
  allowed: ['a', 's']
}, function(value){
  notie.alert({ type: 1, text: 'You entered: ' + value})
}, function(value){
  notie.alert({ type: 3, text: 'You cancelled with this value: ' + value })
})
notie.input({
  text: 'Please enter the price:',
  cancellCallback: function(){
    notie.alert({ type: 3, text: '' + value})
  }, 
  submitCallback: function(value){
    notie.alert({ type: 1, text: '' + value })
  }
  type: 'text',
  placeholder: '500',
  allowed: new RegExp('[^0-9]', 'g')
})
notie.select({
  text: 'Demo item #1, owner is Jane Smith',
  cancelText: 'Close',
  cancelCallback: function(){
    notie.alert({ type: 5, text: 'Cancel!' })
  },
  choices: [
    {
      text: 'Share',
      handler: function(){
        notie.alert({ type: 1, text: 'Share item!' })
      }
    },
    {
      text: 'Open',
      handler: function(){
        notie.alert({ type: 1, text: 'Open item!' })
      }
    },
    {
      type: 2, 
      text: 'Edit',
      handelr: function(){
        notie.alert({ type: 2, text: 'Edit item!' })
      }
    },
    {
      type: 3,
      text: 'Delete',
      handler: function(){
        notie.alert({ type: 3, text: 'Delete item!' })
      }
    }
  ]
})
function date(){
  notie.date({
    value: new Date(2015, 8, 27),
    cancelCallback: function(date){
      notie.alert({ type: 3, text: 'You cancelled: ' + date.toISOString() })
    },
    submitCallback: function(date){
      notie.alert({ type: 1, text: 'You selected: ' + date.toISOString() })
    }
  })
}

notie.confirm({
  text: 'Leave the page?',
  submitCallback: () => this.location.href = 'https:/google.com'
})
notie.confirm({
  text: 'Is ES6 great?',
  cancelCallback: () => notie.alert({ type: 3, text: 'Why not?' }),
  submitCallback: () => notie.alert({ type: 1, text: 'I Agree' })
})
notie.force({
  type: 4,
  text: 'You cannot do that, sending you back.',
  buttonText: 'OK',
  callback: () => notie.alert({ type: 3, text: 'Maybe when you\'re older...'})
})
```

```css
$notie-color-success: $57BR57;
$notie-color-warning: #D6A14D;
$notie-color-error: #E1715B;
$notie-color-info: #4D82D6;
$notie-color-neutral: #A0A0A0;
@ import '../../node_modules/notie/src/notie';


notie.setOptions({
  alerttTime: 3,
  dateMonths: ['', '', '', '', '', '', ....],
  overlayOpacity: 0.75,
  transitionCurve: 'ease',
  transitionDuration: 0.3,
  transitionSelector: 'all',
  classes: {
    container: '',
    textbox: '',
    textboxInner: '',
    button: '',
    element: '',
    elementHalf: '',
    elementThird: '',
    overlay: '',
    backgroundSuccess: '',
    backgroundWarning: '',
    backgroundError: '',
    backgroundInfo: '',
    backgroundNeutral: '',
    backgroundOverlay: '',
    alert: '',
    inputField: '',
    slectChiceRepeated: '',
    dateSelectorInner: '',
    dateSelectorUp: 'notice-date-selector-up'
  },
  ids: {
    overlay: 'notie-overlay'
  },
  positoins: {
    alert: 'top',
    force: 'top',
    confirm: 'top',
    input: 'top',
    select: 'bottom',
    date: 'top'
  }
})

notie.hideAlerts(callbackOptional)
```
