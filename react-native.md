# [React Native](https://reactnative.dev/)

An open source framework for building Android and iOS applications with native capabilities using React and JavaScript.

Think of a [`<View>`](https://reactnative.dev/docs/view) component as a `<div>` tag. And a [`<Text>`](https://reactnative.dev/docs/text) component as a `<p>` tag. Except if you nest it it behaves like a `<span>`. There are more [(built-in) Core Components](https://reactnative.dev/docs/components-and-apis).

For inputting text use [`<TextInput>`](https://reactnative.dev/docs/textinput).

[`<ScrollView>`](https://reactnative.dev/docs/scrollview) is a generic scrolling container. All its elements will be rendered, even when not currently shown on the screen, so it's best to use them to present a small amount of things or a limited size.

[`<FlatList>`](https://reactnative.dev/docs/flatlist) displays a scrolling list of data. It works well for long lists of data, where the number of items might change over time. It only renders elements that are currently shown on the screen.

[`<SectionList>`](https://reactnative.dev/docs/sectionlist) displays a scrolling list of data broken into logical sections (e.g. with section headers).

For platform-specific sections of code you can use the [`Platform` module](https://reactnative.dev/docs/platform). For entire files, you can use [platform-specific file extensions](https://reactnative.dev/docs/platform-specific-code#platform-specific-extensions), e.g. `Component.ios.js` for iOS and `Component.android.js` for Android.

For platform-specific code, `native` means a phone, i.e. either iOS or Android. A native-specific extension like `.native.js` is also an option, just make sure you configure your Web bundler to ignore them.

The easiest way to setup an environment for development is with the [Expo CLI](https://expo.io/tools#cli):

```bash
npm install -g expo-cli # requires Node.js LTS or greater
expo init my-project
cd my-project
npm start
```

You can also use Expo directly in the browser (like CodeSandbox) with [Snack](https://snack.expo.io/). But as with all tools, there are some [limitations](https://docs.expo.io/introduction/why-not-expo/).

You can force state to be reset, with Fast Refresh, by adding `// @refresh reset` anywhere in the file you're editing.

React Native's documentation has a [great overview of testing](https://reactnative.dev/docs/testing-overview) components, React, and JavaScript in general.

Installing a package with native dependencies requires linking and rebuilding your project.

For iOS:

```bash
npx pod-install
npx react-native run-ios
```

Note: This uses the [pod-install](https://www.npmjs.com/package/pod-install) npm package to reduce common issues when doing `pod install`.

For Android:

```bash
npx react-native run-android
```

All of the core components have a prop named `style` for styling purposes. It can accept:

* A plain old JavaScript object, e.g. `{ backgroundColor: 'red' }`
* An array of styles, where the last element takes precedence.

You can also define styles with `StyleSheet.create`:

```javascript
import { StyleSheet, Text } from 'react-native';
...
const styles = StyleSheet.create({
  myText: {
    backgroundColor: 'red'
  }
});
...
export default function () {
  return <Text style={styles.myText}>Hello there</Text>
}
```

To set fixed dimensions on a component use the `width` and `height` properties in a style, e.g. `{ width: 50 }`

All dimensions are unitless, and represent density-independent pixels.

Use `flex` to have the component expand/shrink dynamically based on the available space.

Use `flex: 1` to fill all available space. The larger the number, the higher the ratio of space taken compared to other sibling components.

If a flex container has three children:

1. One with `flex: 1`
1. Another with `flex: 2`
1. Another with `flex: 3`

`1+2+3=6`, which means the first one will take `1/6` of the space. The second one `2/6`. And the third one `3/6`.

A component can only expand if its parent has dimensions greater than `0`, i.e. if the parent has either a fixed `width` and `height` or `flex`.

[`flexDirection`](https://reactnative.dev/docs/layout-props#flexdirection) controls the direction of the flow. The default value in React Native is `column`.

[`justifyContent`](https://reactnative.dev/docs/layout-props#justifycontent) describes how children will align along the main axis. Default value is `flex-start`.

[`alignItems`](https://reactnative.dev/docs/layout-props#alignitems) describes how children will align along the cross axis. Default value is `stretch`.

[`alignSelf`](https://reactnative.dev/docs/layout-props#alignself) overrides `alignItems` on an specific child.

[`alignContent`](https://reactnative.dev/docs/layout-props#aligncontent) defines the distribution of lines along the cross axis, when items wrap to multiple lines with `flexWrap`.

[`flexWrap`](https://reactnative.dev/docs/layout-props#flexwrap) controls what happens when children overflow the size of the container along the main axis.

[`flexGrow`](https://reactnative.dev/docs/layout-props#flexgrow) describes how space between children should be distributed in a container along the main axis.

[`flexShrink`](https://reactnative.dev/docs/layout-props#flexshrink) describes how to shrink children (along the main axis) in the case in which the total size of the children overflows the size of the container.

[`flexBasis`](https://reactnative.dev/docs/layout-props#flexbasis) is an axis-independent way of providing the default size of an item along the main axis.

[`width`](https://reactnative.dev/docs/layout-props#width) and [`height`](https://reactnative.dev/docs/layout-props#height) properties can take:

* `auto` (default), i.e. calculated by React Native
* absolute pixel measurements, e.g. `100` for 100px
* percentages, e.g. `80%`

[`position`](https://reactnative.dev/docs/layout-props#position) can be `relative` or `absolute` only. And `relative` is the default.

The [`<Image>`](https://reactnative.dev/docs/image) component is a unified way of managing images and other media assets.

To reference a static image you can do:

```jsx
<Image source={require('./my-image.png')} />
```

The bundler will look for `my-image.png` on the same folder as the component that required it, and image dimensions will be added automatically.

It will also look for `my-image.ios.png` and `my-image.android.png` and pick the correct file for the platform.

It will also look for `my-image@2x.png` and `my-image@3x.png` and pick the correct file corresponding to the device's screen density.

The import name cannot be dynamic, and has to be known statically.

Any other way of including an image requires you specify image dimensions manually.

Other resources can be required in this fashion. See the full list [here](https://github.com/facebook/metro/blob/master/packages/metro-config/src/defaults/defaults.js).

You may also include images via Xcode asset catalogs:

```jsx
<Image
  source={{ uri: 'app_icon' }}
  style={{ width: 40, height: 40 }}
/>
```

Or in the Android assets folder:

```jsx
<Image
  source={{ uri: 'asset:/app_icon.png' }}
  style={{ width: 40, height: 40 }}
/>
```

If you want avoid bundling your images you may request them via network:

```jsx
<Image
  source={{ uri: 'https://placehold.it/100x100' }} // HTTP request
  style={{ width: 100, height: 100 }}
/>

<Image
  source={{ uri: 'data:image/png;base64,...' }} // base64 encoded
  style={{ width: 100, height: 100 }}
/>
```

Use the [`<ImageBackground>`](https://reactnative.dev/docs/imagebackground) component to use an image as a background image, similar to the `background-image` CSS property:

```jsx
<ImageBackground source={...} style={{ width: '100%', height: '100%' }}>
  <Text>Text with background</Text>
</ImageBackground>
```

The [`PlatformColor`](https://reactnative.dev/docs/platformcolor) function lets you reference the platform's color system. While the [`DynamicColorIOS`](https://reactnative.dev/docs/dynamiccolorios) function allows you to specify which colors should be used in light or Dark Mode (iOS specific).

Colors can be represented as:

* `rgb` and `rgba` hexadecimal: `#f0f`, `#ff00ff`, `#f0ff`, `#ff00ff00`
* `rgb` and `rgba` functional: `rgb(255, 0, 255)`, `rgba(255, 0, 255, 1.0)`
* `hsl` and `hsla`: `hsl(360, 100%, 100%)`, `hsla(360, 100%, 100%, 1.0)`
* color ints: `0xff00ff00`
* named colors: `red`, `blue`, [etc.](https://www.w3.org/TR/css-color-3/#svg-color)

"Touchable" components can capture tapping gestures, and can display feedback when a gesture is recognized. You can use [`<TouchableHighlight>`](https://reactnative.dev/docs/touchablehighlight), [`<TouchableNativeFeedback>`](https://reactnative.dev/docs/touchablenativefeedback), [`<TouchableOpacity>`](https://reactnative.dev/docs/touchableopacity), [`<TouchableWithoutFeedback>`](https://reactnative.dev/docs/touchablewithoutfeedback).

A more extensive and future-proof way to handle touch-based input is with the [`<Pressable>`](https://reactnative.dev/docs/pressable) Core Component. It provides handlers for various stages of press interactions:

* [`onPress`](https://reactnative.dev/docs/pressable#onpress)
* [`onPressIn`](https://reactnative.dev/docs/pressable#onpressin)
* [`onLongPress`](https://reactnative.dev/docs/pressable#onlongpress)
* [`onPressOut`](https://reactnative.dev/docs/pressable#onpressout)

As well as an optional `HitRec` (if `hitSlop` is set) to define where a press can register, and a `PressRect` (via `pressRetentionOffset`) to allow the press to move beyond the element and its `HitRect` while maintaining activation and being eligible for a "press".

Use the [React Navigation](https://reactnavigation.org/) or [React Native Navigation](https://wix.github.io/react-native-navigation/) (advanced) packages to manage the presentation of, and transition between, multiple screens.

There are two animation systems: the [Animated API](https://reactnative.dev/docs/animated), and the [LayoutAnimation API](https://reactnative.dev/docs/layoutanimation)

https://reactnative.dev/docs/accessibility

## Links

* [(Built-in) Core Components](https://reactnative.dev/docs/components-and-apis)
* [React Native Directory – Community-contributed components](https://reactnative.directory/)
* [Expo (Tool) – Documentation](https://docs.expo.io/)
* [Yoga (Playground) – Flexbox implementation used in React Native](https://yogalayout.com/playground)
* [Material Design – Color usage](https://material.io/design/color/color-usage.html)
* [Apple's Human Interface Guidelines – Color](https://developer.apple.com/design/human-interface-guidelines/ios/visual-design/color/)
* [X11 colors – React Native's named colors](https://www.w3.org/TR/css-color-3/#svg-color)
* [React Navigation (package) – Routing and navigation for React Native](https://reactnavigation.org/)
* [React Native Navigation (package) – A complete native navigation solution for React Native](https://wix.github.io/react-native-navigation/)
