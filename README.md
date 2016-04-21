# Vungle's Windows SDK

## Getting Started
To get up and running with Vungle, you'll need to [Create an Account With Vungle](https://v.vungle.com/dashboard) and [Add an Application to the Vungle Dashboard](https://support.vungle.com/hc/en-us/articles/210468678)

Once you've created an account you can follow our [Getting Started for Windows Guide](https://support.vungle.com/hc/en-us/articles/211339368-Get-started-with-Vungle-Windows-SDK) to complete the integration. Remember to get the Vungle App ID from the Vungle dashboard.

### Requirements
* Visual Studio 2014, Windows 10.0 or later

## Release Notes

### VERSION 1.1.6
* Added support for Windows 8.1

### VERSION 1.0.18
* Removed assets from the manifest resources table for passing the WACK tests.

### VERSION 1.0.17
* Initial release

### Integration
NOTE: This document contains examples written in C#. View code for more examples. Sample apps shows how to integrate the Vungle Windows SDK into an Windows 10 Universal Application or Windows 8.1 Application or Windows Phone 8.1 Application. There are three groups of the samples:  

1. Windows Universal Apps:
  1. CS_sample
  2. CPP_sample
  3. DirectX_XAML_sample
  4. VB_sample
2. Windows 8.1 Apps:
  1. CPP_sample_Windows8.1
  2. CS_sample_Windows8.1
3. Windows Phone 8.1 Apps:
  1. CPP_sample_WP8.1
  2. CS_sample_WP8.1  

Each of the groups uses a special Vungle SDK adjusted for this type of the apps.

- In Visual Studio 2015 create new project using some template (depends on the type of your application and the language
you want to use)
- Download the Vungle Windows SDK
- Add reference for the project to the Windows SDK file that has been downloaded
- Import VungleSDK namespace. For example:
```c#
using VungleSDK;
```
- Obtain a VungleAd instance. For example:
```c#
VungleAd sdkInstance;
...
sdkInstance = AdFactory.GetInstance("vungleTest");
```
- Create event handler for OnAdPlayableChanged event. For example:
```c#
//Event handler for OnAdPlayableChanged event
private async void SdkInstance_OnAdPlayableChanged(object sender, AdPlayableEventArgs e)
{
  //Run asynchronously on the UI thread
  await this.Dispatcher.RunAsync(CoreDispatcherPriority.Normal,
  new DispatchedHandler(() => someMethod()));
}
```
- Register this event handler for OnAdPlayableChanged event. For example:
```c#
sdkInstance.OnAdPlayableChanged += SdkInstance_OnAdPlayableChanged;
```
- Play the ad with the options you prefer. For example:
```c#
private async void CustomConfigButton_Click(object sender, RoutedEventArgs e)
{
  await sdkInstance.PlayAdAsync(new AdConfig { Incentivized = true , SoundEnabled = false});
}
```

NOTE: Make sure that your project has "internetClient" capability in the package.appxmanifest file:
```
<Capabilities>
    ...
    <Capability Name="internetClient" />
    ...
</Capabilities>
```
