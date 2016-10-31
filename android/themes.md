# Themes

## Full-screen Immersive Activity

Step 1: Extend AppCompat Activity
Step 2: In styles.xml, define a new theme

```xml
<style name="themeNoActionBar" parent="@style/Theme.AppCompat.Light">
    <item name="windowNoTitle">true</item>
    <item name="windowActionBar">false</item>
    <item name="android:windowFullscreen">true</item>
    <item name="android:windowContentOverlay">@null</item>
</style>
```

Step 3: In AndroidManifest.xml, apply the theme to activity

```xml
<activity
    ...
    android:theme="@style/themeNoActionBar">
</activity>
```