---
layout: post
title: Serving static files in VS 2017 
---

Pre-Requirement: Visual studio 2017 installed.  

1. Create a new **ASP.NET Core Web Application(.Net Core)** project and select the empty template
![alt](../images/vs17empty/01Create.png)
![alt](../images/vs17empty/01EmptyTemplate.png)

2.  Add the ***Microsoft.AspNetCore.StaticFiles*** nugget package so you can serve static files
![](../images/vs17empty/StaticFilesNuget.png)

3.  Add to your startup.cs file:<br> UseDefaultFiles looks for files named index.html or default.html; UseStaticFiles will let use serve client files  html,css,jscript etc..

```csharp
    app.UseDefaultFiles();
    app.UseStaticFiles();
```


4. Create ***index.html*** file in wwwroot folder
![alt](../images/vs17empty/index.png)

5.  Now run you project,  you should see your the index.html file displayed in the browser












