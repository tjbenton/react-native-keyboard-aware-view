# react-native-keyboard-aware-view
A simple React Native View component that resizes composite children views inside itself when the keyboard appears. You can implement your own ScrollView, ListView, Multiple Views etc... inside the View and set your own view to 'flex: 1'. 

![Demo screen](https://dl.dropboxusercontent.com/u/11386030/out.gif)

### Note: this view only affects iOS. Although still parsable in Android environment, it is treated as an ordinary <View> with "flex: 1" bootstrapped.

Tested: it only affects iOS since Android version of React Native lacks support of this callback, by v0.17:

    DeviceEventEmitter.addListener('keyboardWillShow', this.onKeyboardWillShow.bind(this))
    DeviceEventEmitter.addListener('keyboardWillHide', this.onKeyboardWillHide.bind(this))

I believe this callback feature will not be landed in the future Android version of React Native. But anyway, Android version has its very own native handling for the keyboards without coding, so this lack is somehow acceptable.


## Installation
You can install this component through ``npm``:

```shell
npm i react-native-keyboard-aware-view --save
```

## Usage
Import ``react-native-keyboard-aware-view`` and wrap your content inside
it:

```js
import { KeyboardAwareView } from 'react-native-keyboard-aware-view'
```

### Animated keyboard aware view:
```usage
<KeyboardAwareView animated={true}>
	...
</KeyboardAwareView>
```

### Instant (non-animated) keyboard aware view:
```usage
<KeyboardAwareView animated={false}>
	...
</KeyboardAwareView>
```

### An Example snippet from one of my projects:
```jsx
  render() {
    return (
        <View style={{flex: 1}}>
          <KeyboardAwareView animated={true}>
            <View style={[styles.bg]}>
              <ScrollView
                  ref={(view) => {this.scrollView = view; }}
                  style={[{flex: 1, alignSelf: 'stretch'}, this.props.style]}
                  keyboardShouldPersistTaps={true}
                  automaticallyAdjustContentInsets={false}
                  onScroll={this.onScroll.bind(this)}
                  scrollEventThrottle={200}
                  onLayout={(e) => {var {x, y, width, height} = e.nativeEvent.layout; console.log(height); }}>
                <View style={{height: 34}} />
                <CTextInput scrollView={this.getScrollView()} placeholder="登記名稱"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電郵"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電話"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="登記名稱"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電郵"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電話"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="登記名稱"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電郵"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電話"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="登記名稱"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電郵"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電話"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="登記名稱"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電郵"/>
                <CTextInput scrollView={this.getScrollView()} placeholder="電話"/>
                <View style={{height: 46}} />
                <Text>或以Facebook登記</Text>
                <Image source={GLOBAL.IMAGE.icon_facebook} style={{width: 50, height: 50}} />
              </ScrollView>
            </View>
            <TouchableOpacity style={{height: 50, backgroundColor: 'transparent', alignItems: 'center', justifyContent: 'center', alignSelf: 'stretch'}}>

              <Text style={{fontSize: 20, color: '#FFFFFF'}}>提交</Text>
              <CTextInput scrollView={this.getScrollView()} placeholder="電話"/>
            </TouchableOpacity>
          </KeyboardAwareView>
        </View>
    );
  }
```


### A Easier Example:
```jsx
  render() {
    return (
        <View style={{flex: 1}}>
          <KeyboardAwareView animated={true}>
            <View style={{flex: 1}}>
              <ScrollView style={{flex: 1}}>
	              <Text style={{fontSize: 20, color: '#FFFFFF'}}>A</Text>
	              <Text style={{fontSize: 20, color: '#FFFFFF'}}>B</Text>
	              <Text style={{fontSize: 20, color: '#FFFFFF'}}>C</Text>
	              <Text style={{fontSize: 20, color: '#FFFFFF'}}>D</Text>
              </ScrollView>
            </View>
            <TouchableOpacity style={{height: 50, backgroundColor: 'transparent', alignItems: 'center', justifyContent: 'center', alignSelf: 'stretch'}}>
              <Text style={{fontSize: 20, color: '#FFFFFF'}}>Submit</Text>
            </TouchableOpacity>
          </KeyboardAwareView>
        </View>
    );
  }
```


## License

MIT.
