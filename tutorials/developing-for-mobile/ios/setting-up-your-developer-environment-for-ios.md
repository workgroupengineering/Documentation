# Setting up your developer environment for iOS

### Prerequisites&#x20;

On a mac you will need to have the latest version of MacOS and XCode installed.

### Install the SDK

First it is very important to install the correct [dotnet SDK](https://dotnet.microsoft.com/en-us/download/dotnet/6.0). At the time of writing, the lowest sdk version that works is 6.0.200.

### Install the Workload

```
dotnet workload install ios
```

{% hint style="info" %}
You may need to run the command with `sudo`\
\
You may also need to uninstall old versions. `dotnet workload remove ios`
{% endhint %}

This will allow you to build applications for iOS on any platform. However you will only be able to test and run them if you have access to actual MacOS hardware with XCode installed.
