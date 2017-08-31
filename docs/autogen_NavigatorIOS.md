---
id: navigatorios
title: NavigatorIOS
sidebar: api
category: Components
permalink: docs/navigatorios.html
---
<div><div><p><code>NavigatorIOS</code> is a wrapper around
<a href="https://developer.apple.com/library/ios/documentation/UIKit/Reference/UINavigationController_Class/" target="_blank"><code>UINavigationController</code></a>,
enabling you to implement a navigation stack. It works exactly the same as it
would on a native app using <code>UINavigationController</code>, providing the same
animations and behavior from UIKIt.</p><p>As the name implies, it is only available on iOS. Take a look at
<a href="https://reactnavigation.org/" target="_blank"><code>React Navigation</code></a> for a cross-platform
solution in JavaScript, or check out either of these components for native
solutions: <a href="http://airbnb.io/native-navigation/" target="_blank">native-navigation</a>,
<a href="https://github.com/wix/react-native-navigation" target="_blank">react-native-navigation</a>.</p><p>To set up the navigator, provide the <code>initialRoute</code> prop with a route
object. A route object is used to describe each scene that your app
navigates to. <code>initialRoute</code> represents the first route in your navigator.</p><div class="prism language-javascript"><span class="token keyword">import</span> React<span class="token punctuation">,</span> <span class="token punctuation">{</span> Component<span class="token punctuation">,</span> PropTypes <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'react'</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> <span class="token punctuation">{</span> NavigatorIOS<span class="token punctuation">,</span> Text <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">'react-native'</span><span class="token punctuation">;</span>

<span class="token keyword">export</span> <span class="token keyword">default</span> <span class="token keyword">class</span> <span class="token class-name">NavigatorIOSApp</span> <span class="token keyword">extends</span> <span class="token class-name">Component</span> <span class="token punctuation">{</span>
  <span class="token function">render</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token punctuation">(</span>
      <span class="token operator">&lt;</span>NavigatorIOS
        initialRoute<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">{</span>
          component<span class="token punctuation">:</span> MyScene<span class="token punctuation">,</span>
          title<span class="token punctuation">:</span> <span class="token string">'My Initial Scene'</span><span class="token punctuation">,</span>
        <span class="token punctuation">}</span><span class="token punctuation">}</span>
        style<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">{</span>flex<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">}</span><span class="token punctuation">}</span>
      <span class="token operator">/</span><span class="token operator">&gt;</span>
    <span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>

<span class="token keyword">class</span> <span class="token class-name">MyScene</span> <span class="token keyword">extends</span> <span class="token class-name">Component</span> <span class="token punctuation">{</span>
  <span class="token keyword">static</span> propTypes <span class="token operator">=</span> <span class="token punctuation">{</span>
    title<span class="token punctuation">:</span> PropTypes<span class="token punctuation">.</span>string<span class="token punctuation">.</span>isRequired<span class="token punctuation">,</span>
    navigator<span class="token punctuation">:</span> PropTypes<span class="token punctuation">.</span>object<span class="token punctuation">.</span>isRequired<span class="token punctuation">,</span>
  <span class="token punctuation">}</span>

  _onForward <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>navigator<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
      title<span class="token punctuation">:</span> <span class="token string">'Scene '</span> <span class="token operator">+</span> nextIndex<span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">render</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token punctuation">(</span>
      <span class="token operator">&lt;</span>View<span class="token operator">&gt;</span>
        <span class="token operator">&lt;</span>Text<span class="token operator">&gt;</span>Current Scene<span class="token punctuation">:</span> <span class="token punctuation">{</span> <span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>title <span class="token punctuation">}</span><span class="token operator">&lt;</span><span class="token operator">/</span>Text<span class="token operator">&gt;</span>
        <span class="token operator">&lt;</span>TouchableHighlight onPress<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>_onForward<span class="token punctuation">}</span><span class="token operator">&gt;</span>
          <span class="token operator">&lt;</span>Text<span class="token operator">&gt;</span>Tap me to load the next scene<span class="token operator">&lt;</span><span class="token operator">/</span>Text<span class="token operator">&gt;</span>
        <span class="token operator">&lt;</span><span class="token operator">/</span>TouchableHighlight<span class="token operator">&gt;</span>
      <span class="token operator">&lt;</span><span class="token operator">/</span>View<span class="token operator">&gt;</span>
    <span class="token punctuation">)</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span></div><p>In this code, the navigator renders the component specified in initialRoute,
which in this case is <code>MyScene</code>. This component will receive a <code>route</code> prop
and a <code>navigator</code> prop representing the navigator. The navigator's navigation
bar will render the title for the current scene, "My Initial Scene".</p><p>You can optionally pass in a <code>passProps</code> property to your <code>initialRoute</code>.
<code>NavigatorIOS</code> passes this in as props to the rendered component:</p><div class="prism language-javascript">initialRoute<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">{</span>
  component<span class="token punctuation">:</span> MyScene<span class="token punctuation">,</span>
  title<span class="token punctuation">:</span> <span class="token string">'My Initial Scene'</span><span class="token punctuation">,</span>
  passProps<span class="token punctuation">:</span> <span class="token punctuation">{</span> myProp<span class="token punctuation">:</span> <span class="token string">'foo'</span> <span class="token punctuation">}</span>
<span class="token punctuation">}</span><span class="token punctuation">}</span></div><p>You can then access the props passed in via <code>{this.props.myProp}</code>.</p><h4><a class="anchor" name="handling-navigation"></a>Handling Navigation <a class="hash-link" href="docs/navigatorios.html#handling-navigation">#</a></h4><p>To trigger navigation functionality such as pushing or popping a view, you
have access to a <code>navigator</code> object. The object is passed in as a prop to any
component that is rendered by <code>NavigatorIOS</code>. You can then call the
relevant methods to perform the navigation action you need:</p><div class="prism language-javascript"><span class="token keyword">class</span> <span class="token class-name">MyView</span> <span class="token keyword">extends</span> <span class="token class-name">Component</span> <span class="token punctuation">{</span>
  <span class="token function">_handleBackPress</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>navigator<span class="token punctuation">.</span><span class="token function">pop</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">_handleNextPress</span><span class="token punctuation">(</span>nextRoute<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>navigator<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span>nextRoute<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">render</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">const</span> nextRoute <span class="token operator">=</span> <span class="token punctuation">{</span>
      component<span class="token punctuation">:</span> MyView<span class="token punctuation">,</span>
      title<span class="token punctuation">:</span> <span class="token string">'Bar That'</span><span class="token punctuation">,</span>
      passProps<span class="token punctuation">:</span> <span class="token punctuation">{</span> myProp<span class="token punctuation">:</span> <span class="token string">'bar'</span> <span class="token punctuation">}</span>
    <span class="token punctuation">}</span><span class="token punctuation">;</span>
    <span class="token keyword">return</span><span class="token punctuation">(</span>
      <span class="token operator">&lt;</span>TouchableHighlight onPress<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token function">_handleNextPress</span><span class="token punctuation">(</span>nextRoute<span class="token punctuation">)</span><span class="token punctuation">}</span><span class="token operator">&gt;</span>
        <span class="token operator">&lt;</span>Text style<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">{</span>marginTop<span class="token punctuation">:</span> <span class="token number">200</span><span class="token punctuation">,</span> alignSelf<span class="token punctuation">:</span> <span class="token string">'center'</span><span class="token punctuation">}</span><span class="token punctuation">}</span><span class="token operator">&gt;</span>
          See you on the other nav <span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>myProp<span class="token punctuation">}</span><span class="token operator">!</span>
        <span class="token operator">&lt;</span><span class="token operator">/</span>Text<span class="token operator">&gt;</span>
      <span class="token operator">&lt;</span><span class="token operator">/</span>TouchableHighlight<span class="token operator">&gt;</span>
    <span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span></div><p>You can also trigger navigator functionality from the <code>NavigatorIOS</code>
component:</p><div class="prism language-javascript"><span class="token keyword">class</span> <span class="token class-name">NavvyIOS</span> <span class="token keyword">extends</span> <span class="token class-name">Component</span> <span class="token punctuation">{</span>
  <span class="token function">_handleNavigationRequest</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">this</span><span class="token punctuation">.</span>refs<span class="token punctuation">.</span>nav<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
      component<span class="token punctuation">:</span> MyView<span class="token punctuation">,</span>
      title<span class="token punctuation">:</span> <span class="token string">'Genius'</span><span class="token punctuation">,</span>
      passProps<span class="token punctuation">:</span> <span class="token punctuation">{</span> myProp<span class="token punctuation">:</span> <span class="token string">'genius'</span> <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token function">render</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token punctuation">(</span>
      <span class="token operator">&lt;</span>NavigatorIOS
        ref<span class="token operator">=</span><span class="token string">'nav'</span>
        initialRoute<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">{</span>
          component<span class="token punctuation">:</span> MyView<span class="token punctuation">,</span>
          title<span class="token punctuation">:</span> <span class="token string">'Foo This'</span><span class="token punctuation">,</span>
          passProps<span class="token punctuation">:</span> <span class="token punctuation">{</span> myProp<span class="token punctuation">:</span> <span class="token string">'foo'</span> <span class="token punctuation">}</span><span class="token punctuation">,</span>
          rightButtonTitle<span class="token punctuation">:</span> <span class="token string">'Add'</span><span class="token punctuation">,</span>
          onRightButtonPress<span class="token punctuation">:</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token function">_handleNavigationRequest</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
        <span class="token punctuation">}</span><span class="token punctuation">}</span>
        style<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">{</span>flex<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">}</span><span class="token punctuation">}</span>
      <span class="token operator">/</span><span class="token operator">&gt;</span>
    <span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span></div><p>The code above adds a <code>_handleNavigationRequest</code> private method that is
invoked from the <code>NavigatorIOS</code> component when the right navigation bar item
is pressed. To get access to the navigator functionality, a reference to it
is saved in the <code>ref</code> prop and later referenced to push a new scene into the
navigation stack.</p><h4><a class="anchor" name="navigation-bar-configuration"></a>Navigation Bar Configuration <a class="hash-link" href="docs/navigatorios.html#navigation-bar-configuration">#</a></h4><p>Props passed to <code>NavigatorIOS</code> will set the default configuration
for the navigation bar. Props passed as properties to a route object will set
the configuration for that route's navigation bar, overriding any props
passed to the <code>NavigatorIOS</code> component.</p><div class="prism language-javascript"><span class="token function">_handleNavigationRequest</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">this</span><span class="token punctuation">.</span>refs<span class="token punctuation">.</span>nav<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
   <span class="token comment" spellcheck="true"> //...
</span>    passProps<span class="token punctuation">:</span> <span class="token punctuation">{</span> myProp<span class="token punctuation">:</span> <span class="token string">'genius'</span> <span class="token punctuation">}</span><span class="token punctuation">,</span>
    barTintColor<span class="token punctuation">:</span> <span class="token string">'#996699'</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token function">render</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">return</span> <span class="token punctuation">(</span>
    <span class="token operator">&lt;</span>NavigatorIOS
     <span class="token comment" spellcheck="true"> //...
</span>      style<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">{</span>flex<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">}</span><span class="token punctuation">}</span>
      barTintColor<span class="token operator">=</span><span class="token string">'#ffffcc'</span>
    <span class="token operator">/</span><span class="token operator">&gt;</span>
  <span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span></div><p>In the example above the navigation bar color is changed when the new route
is pushed.</p></div><h3><a class="anchor" name="props"></a>Props <a class="hash-link" href="docs/navigatorios.html#props">#</a></h3><div class="props"><div class="prop"><h4 class="propTitle"><a class="anchor" name="bartintcolor"></a>barTintColor?: <span class="propType">string</span> <a class="hash-link" href="docs/navigatorios.html#bartintcolor">#</a></h4><div><p>The default background color of the navigation bar.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="initialroute"></a>initialRoute: <span class="propType"><span>{<span><span><span>component: function</span>, </span><span><span>title: string</span>, </span><span><span>titleImage: Image.propTypes.source</span>, </span><span><span>passProps: object</span>, </span><span><span>backButtonIcon: Image.propTypes.source</span>, </span><span><span>backButtonTitle: string</span>, </span><span><span>leftButtonIcon: Image.propTypes.source</span>, </span><span><span>leftButtonTitle: string</span>, </span><span><span>leftButtonSystemIcon: Object.keys(SystemIcons)</span>, </span><span><span>onLeftButtonPress: function</span>, </span><span><span>rightButtonIcon: Image.propTypes.source</span>, </span><span><span>rightButtonTitle: string</span>, </span><span><span>rightButtonSystemIcon: Object.keys(SystemIcons)</span>, </span><span><span>onRightButtonPress: function</span>, </span><span><span>wrapperStyle: ViewPropTypes.style</span>, </span><span><span>navigationBarHidden: bool</span>, </span><span><span>shadowHidden: bool</span>, </span><span><span>tintColor: string</span>, </span><span><span>barTintColor: string</span>, </span><span><span>titleTextColor: string</span>, </span><span>translucent: bool</span></span>}</span></span> <a class="hash-link" href="docs/navigatorios.html#initialroute">#</a></h4><div><p>NavigatorIOS uses <code>route</code> objects to identify child views, their props,
and navigation bar configuration. Navigation operations such as push
operations expect routes to look like this the <code>initialRoute</code>.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="interactivepopgestureenabled"></a>interactivePopGestureEnabled?: <span class="propType">bool</span> <a class="hash-link" href="docs/navigatorios.html#interactivepopgestureenabled">#</a></h4><div><p>Boolean value that indicates whether the interactive pop gesture is
enabled. This is useful for enabling/disabling the back swipe navigation
gesture.</p><p>If this prop is not provided, the default behavior is for the back swipe
gesture to be enabled when the navigation bar is shown and disabled when
the navigation bar is hidden. Once you've provided the
<code>interactivePopGestureEnabled</code> prop, you can never restore the default
behavior.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="itemwrapperstyle"></a>itemWrapperStyle?: <span class="propType">ViewPropTypes.style</span> <a class="hash-link" href="docs/navigatorios.html#itemwrapperstyle">#</a></h4><div><p>The default wrapper style for components in the navigator.
A common use case is to set the <code>backgroundColor</code> for every scene.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="navigationbarhidden"></a>navigationBarHidden?: <span class="propType">bool</span> <a class="hash-link" href="docs/navigatorios.html#navigationbarhidden">#</a></h4><div><p>Boolean value that indicates whether the navigation bar is hidden
by default.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="shadowhidden"></a>shadowHidden?: <span class="propType">bool</span> <a class="hash-link" href="docs/navigatorios.html#shadowhidden">#</a></h4><div><p>Boolean value that indicates whether to hide the 1px hairline shadow
by default.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="tintcolor"></a>tintColor?: <span class="propType">string</span> <a class="hash-link" href="docs/navigatorios.html#tintcolor">#</a></h4><div><p>The default color used for the buttons in the navigation bar.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="titletextcolor"></a>titleTextColor?: <span class="propType">string</span> <a class="hash-link" href="docs/navigatorios.html#titletextcolor">#</a></h4><div><p>The default text color of the navigation bar title.</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="translucent"></a>translucent?: <span class="propType">bool</span> <a class="hash-link" href="docs/navigatorios.html#translucent">#</a></h4><div><p>Boolean value that indicates whether the navigation bar is
translucent by default</p></div></div></div><span><h3><a class="anchor" name="methods"></a>Methods <a class="hash-link" href="docs/navigatorios.html#methods">#</a></h3><div class="props"><div class="prop"><h4 class="methodTitle"><a class="anchor" name="push"></a>push<span class="methodType">(route: object)</span> <a class="hash-link" href="docs/navigatorios.html#push">#</a></h4><div><p>Navigate forward to a new route.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>route<br><br><div><span>object</span></div></td><td class="description"><div><p>The new route to navigate to.</p></div></td></tr></tbody></table></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="popn"></a>popN<span class="methodType">(n: number)</span> <a class="hash-link" href="docs/navigatorios.html#popn">#</a></h4><div><p>Go back N scenes at once. When N=1, behavior matches <code>pop()</code>.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>n<br><br><div><span>number</span></div></td><td class="description"><div><p>The number of scenes to pop.</p></div></td></tr></tbody></table></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="pop"></a>pop<span class="methodType">()</span> <a class="hash-link" href="docs/navigatorios.html#pop">#</a></h4><div><p>Pop back to the previous scene.</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="replaceatindex"></a>replaceAtIndex<span class="methodType">(route: object, index: number)</span> <a class="hash-link" href="docs/navigatorios.html#replaceatindex">#</a></h4><div><p>Replace a route in the navigation stack.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>route<br><br><div><span>object</span></div></td><td class="description"><div><p>The new route that will replace the specified one.</p></div></td></tr><tr><td>index<br><br><div><span>number</span></div></td><td class="description"><div><p>The route into the stack that should be replaced.
   If it is negative, it counts from the back of the stack.</p></div></td></tr></tbody></table></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="replace"></a>replace<span class="methodType">(route: object)</span> <a class="hash-link" href="docs/navigatorios.html#replace">#</a></h4><div><p>Replace the route for the current scene and immediately
load the view for the new route.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>route<br><br><div><span>object</span></div></td><td class="description"><div><p>The new route to navigate to.</p></div></td></tr></tbody></table></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="replaceprevious"></a>replacePrevious<span class="methodType">(route: object)</span> <a class="hash-link" href="docs/navigatorios.html#replaceprevious">#</a></h4><div><p>Replace the route/view for the previous scene.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>route<br><br><div><span>object</span></div></td><td class="description"><div><p>The new route to will replace the previous scene.</p></div></td></tr></tbody></table></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="poptotop"></a>popToTop<span class="methodType">()</span> <a class="hash-link" href="docs/navigatorios.html#poptotop">#</a></h4><div><p>Go back to the topmost item in the navigation stack.</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="poptoroute"></a>popToRoute<span class="methodType">(route: object)</span> <a class="hash-link" href="docs/navigatorios.html#poptoroute">#</a></h4><div><p>Go back to the item for a particular route object.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>route<br><br><div><span>object</span></div></td><td class="description"><div><p>The new route to navigate to.</p></div></td></tr></tbody></table></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="replacepreviousandpop"></a>replacePreviousAndPop<span class="methodType">(route: object)</span> <a class="hash-link" href="docs/navigatorios.html#replacepreviousandpop">#</a></h4><div><p>Replaces the previous route/view and transitions back to it.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>route<br><br><div><span>object</span></div></td><td class="description"><div><p>The new route that replaces the previous scene.</p></div></td></tr></tbody></table></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="resetto"></a>resetTo<span class="methodType">(route: object)</span> <a class="hash-link" href="docs/navigatorios.html#resetto">#</a></h4><div><p>Replaces the top item and pop to it.</p></div><div><strong>Parameters:</strong><table class="params"><thead><tr><th>Name and Type</th><th>Description</th></tr></thead><tbody><tr><td>route<br><br><div><span>object</span></div></td><td class="description"><div><p>The new route that will replace the topmost item.</p></div></td></tr></tbody></table></div></div></div></span></div>