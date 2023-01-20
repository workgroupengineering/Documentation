---
description: Create a solution compatible with Desktop, Mobile and Web
---

# Create a cross platform solution

Make sure you use latest .NET 6 SDK. iOS especially requires developers to use 6.0.202 SDK or newer.

Install the Avalonia dotnet templates. Version `0.10.13` and above adds support for mobile.

```bash
dotnet new install avalonia.templates
```



Once the templates are installed you can generate a new project.

Create a folder name that matches the name of your project. Then enter that folder.

```bash
mkdir HelloWorld
cd HelloWorld
```



Now create a cross platform solution using the templates.

```bash
dotnet new avalonia.xplat
```



This will create a project with the following structure:

* HelloWorld (Avalonia UI project with Views and ViewModels)
* HelloWorld.Android (Avalonia bootstrap code for Android)
* HelloWorld.Desktop (Avalonia bootstrap code for Desktop - Windows, macOS and Linux)
* HelloWorld.iOS (Avalonia bootstrap code for iOS)
* HelloWorld.Web (Avalonia bootstrap code for Web)
* nuget.config (gives access to nightly builds of Avalonia)
* Directory.Build.props (sets the Avalonia version your application will target)
* HelloWorld.sln (the solution file if you use an IDE)

Now continue to:

[setting-up-your-developer-environment-for-ios.md](ios/setting-up-your-developer-environment-for-ios.md "mention") or [setting-up-your-developer-environment-for-android.md](android/setting-up-your-developer-environment-for-android.md "mention")
