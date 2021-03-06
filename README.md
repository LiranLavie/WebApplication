# WebApplication

![demo](doc/demo.png)

 This project shows how to create,build and publish an ASP.NET Core Web App with Internet Information Services (IIS).




## Part 1: Create and build a website

**Installation:**

1. Install Visual Studio - on installation screen check  **ASP.NET and web development** from **Workloads** tab and **.NET Core 3.1 Runtime(LTS)** from **Individual components** tab.

**Build and Publish:**

1. In Visual Studio create a new ASP.NET Core Web App.

2. Add **Newtonsoft.Json** from **Tools > NuGet package manager** 

3. After installing **Newtonsoft.Json** we can see a package referance entry added to csproj file.
```
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
```
4. Restore packages manually using Visual Studio - **Tools > Options > NuGet Package Manager**. Under **Package Restore options** select **Allow NuGet to download missing packages**.

5. In **Solution Explorer** right click the solution and select **Restore NuGet Packages**.

6. Compile (rebuild) your project -In **Solution Explorer** right click the solution and select **Rebuild solution**. 
  
7. The rebuild process will create the following files:
```
.vs/WebApplication/FileContentIndex/dfb8afb8-589a-4adb-b6e9-531c604ded95.vsidx
WebApplication/bin/Debug/netcoreapp3.1/appsettings.Development.json
WebApplication/bin/Debug/netcoreapp3.1/appsettings.json
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.Views.dll
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.Views.pdb
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.deps.json
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.dll
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.exe
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.pdb
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.runtimeconfig.dev.json
WebApplication/bin/Debug/netcoreapp3.1/WebApplication.runtimeconfig.json
WebApplication/obj/Debug/netcoreapp3.1/Razor/Pages/Error.cshtml.g.cs
WebApplication/obj/Debug/netcoreapp3.1/Razor/Pages/Index.cshtml.g.cs
WebApplication/obj/Debug/netcoreapp3.1/Razor/Pages/Privacy.cshtml.g.cs
WebApplication/obj/Debug/netcoreapp3.1/Razor/Pages/Shared/_Layout.cshtml.g.cs
WebApplication/obj/Debug/netcoreapp3.1/Razor/Pages/Shared/_ValidationScriptsPartial.cshtml.g.cs
WebApplication/obj/Debug/netcoreapp3.1/Razor/Pages/_ViewImports.cshtml.g.cs
WebApplication/obj/Debug/netcoreapp3.1/Razor/Pages/_ViewStart.cshtml.g.cs
WebApplication/obj/Debug/netcoreapp3.1/apphost.exe
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.MvcApplicationPartsAssemblyInfo.cache
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.RazorCoreGenerate.cache
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.RazorTargetAssemblyInfo.cache
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.RazorTargetAssemblyInfo.cs
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.TagHelpers.input.cache
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.TagHelpers.output.cache
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.Views.dll
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.Views.pdb
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.csproj.CopyComplete
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.csproj.CoreCompileInputs.cache
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.csproj.FileListAbsolute.txt
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.dll
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.genruntimeconfig.cache
WebApplication/obj/Debug/netcoreapp3.1/WebApplication.pdb
WebApplication/obj/Debug/netcoreapp3.1/staticwebassets/WebApplication.StaticWebAssets.Manifest.cache
```
8. Publish the application - In **Solution Explorer** right click the project name and select
**Publish**.
9. On **Publish** screen select **Folder** and publish the project to a shared folder on the server or choose any other option.

## Part 2: Create website on your Microsoft machine

1. Create a folder for your new website and add the published project files from previous step.
2. Add **Information Services (IIS)** on your server:
   1. Open **Control Panel** and click **Programs and Features > Turn Windows features on or off** and enable **Internet Information Services**.
   2. Expand the Internet Information Services feature and verify that the web server        components listed in the next section are enabled.

   * .NET Extensibility 4.5
   * ASP.NET 4.5
3. Add a new IIS application pool - In the left navigation tree, right-click the **Application  Pools** node and select **Add Application Pool**

4. Add a new website - In the left navigation tree, right-click the **Sites** node and select **Add Website**
5. Select your website and enter **Binding** in the right navigation tree. Change the port number to **5100**
6. Select **Basic Setting** in the right navigation tree and set the path to your published project folder
7. browse the website through **http://localhost:5100/**
8. you will get the following error :
```
   HTTP Error 500.0 - ASP.NET Core IIS hosting failure (in-process) in Dot net core 3.1
```
9. To solve this error install **.NET Core Hosting Bundle on the** IIS server from [**Here**](https://dotnet.microsoft.com/en-us/download/dotnet/3.1).
   The bundle installs the **.NET Core Runtime**  **.NET Core Library** and the **ASP.NET Core Module** The module allows ASP.NET Core apps to run behind IIS

10. You should now be able to browse the website.
