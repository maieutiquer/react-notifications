# React Notifications

[<img src="./screenshot.png" style="width: 100%;" />](http://vn38minhtran.github.io/react-notifications)

## Installation

```
npm install --save react-notifications
```

## Usage

### Note

**Use only one 'NotificationContainer' component in the app.**

### CSS

#### Webpack:
```js
import 'react-notifications/lib/notifications.css';
```

#### Other
```html
<link rel="stylesheet" type="text/css" href="path/to/notifications.css">
```

### JS

```js
import React from 'react';
import {NotificationContainer, NotificationManager} from 'react-notifications';

class Example extends React.Component {
  createNotification = (type) => {
    return () => {
      switch (type) {
        case 'info':
          NotificationManager.info('Info message');
          break;
        case 'success':
          NotificationManager.success('Success message', 'Title here');
          break;
        case 'warning':
          NotificationManager.warning('Warning message', 'Close after 3000ms', 3000);
          break;
        case 'error':
          NotificationManager.error('Error message', 'Click me!', 5000, () => {
            alert('callback');
          });
          break;
      }
    };
  };

  render() {
    return (
      <div>
        <button className='btn btn-info'
          onClick={this.createNotification('info')}>Info
        </button>
        <hr/>
        <button className='btn btn-success'
          onClick={this.createNotification('success')}>Success
        </button>
        <hr/>
        <button className='btn btn-warning'
          onClick={this.createNotification('warning')}>Warning
        </button>
        <hr/>
        <button className='btn btn-danger'
          onClick={this.createNotification('error')}>Error
        </button>

        <NotificationContainer/>
      </div>
    );
  }
}

export default Example;
```

## NotificationContainer Props

| Name | Type | Default | Required |
|------|------|---------|----------|
| enterTimeout | number | 400 | false |
| leaveTimeout | number | 400 | false |

## NotificationManager API

- NotificationManager.info(message, title, timeOut, callback, priority);
- NotificationManager.success(message, title, timeOut, callback, priority);
- NotificationManager.warning(message, title, timeOut, callback, priority);
- NotificationManager.error(message, title, timeOut, callback, priority);

| message | string | The message string
| title | string | The title string
| timeOut | integer | The popup timeout in milliseconds
| callback | function | A function that gets fired when the popup is clicked
| priority | boolean | If true, the message gets inserted at the top

## Example
View [demo](http://vn38minhtran.github.io/react-notifications) or example folder.