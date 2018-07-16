# Gifted Chat

## Features

- Fully customizable components
- Composer actions (to attach photos, etc.)
- Load earlier messages
- Copy messages to clipboard
- Touchable 
- Avatar as user's initials
- Localized dates
- Multiline TextInput
- InputToolbar avoiding keyboard
- Redux support


## Installation

- Using [npm](https://www.npmjs.com/#getting-started): `npm install react-native-gifted-chat --save`
- Using [Yarn](https://yarnpkg.com/): `yarn add react-native-gifted-chat`

## Example

```jsx
import { GiftedChat } from 'react-native-gifted-chat';

class Example extends React.Component {

  state = {
    messages: [],
  };

  componentWillMount() {
    this.setState({
      messages: [
        {
          _id: 1,
          text: 'Hello developer',
          createdAt: new Date(),
          user: {
            _id: 2,
            name: 'React Native',
            avatar: 'https://facebook.github.io/react/img/logo_og.png',
          },
        },
      ],
    });
  }

  onSend(messages = []) {
    this.setState((previousState) => ({
      messages: GiftedChat.append(previousState.messages, messages),
    }));
  }

  render() {
    return (
      <GiftedChat
        messages={this.state.messages}
        onSend={(messages) => this.onSend(messages)}
        user={{
          _id: 1,
        }}
      />
    );
  }

}
```


## Message object

e.g.

```js
{
  _id: 1,
  text: 'My message',
  createdAt: new Date(Date.UTC(2016, 5, 11, 17, 20, 0)),
  user: {
    _id: 2,
    name: 'React Native',
    avatar: 'https://facebook.github.io/react/img/logo_og.png',
  },
  image: 'https://facebook.github.io/react/img/logo_og.png',
  // Any additional custom parameters are passed through
}
```


## Notes for local development

You can use [`wml`](https://github.com/wix/wml) to keep the example app in sync
with any changes you make to the library during development. Steps:

1. Install it: `npm install -g wml`
2. Configure it: `wml add . example/node_modules/react-native-gifted-chat` from the root directory
3. `cd example`
4. `npm start`
5. `wml start` in another terminal window (doesn't matter where)

Note that it's important for `wml start` to come **after** `npm start`, or you'll get `Can't find entry file index.js` errors.
If you have any issues, you can clear your watches using `watchman watch-del-all` and try again.


