---
layout: post
title: Create a simple blog in asp.NET core
---

### Creating a simple blog in Asp.net core (Part 1)

In this tutorial we will create a simple blogging app


Requirements: Visual Studio professional or community edition installed, windows 10


1. Create a **new project** and call it SimpleBlog
![image](../images/simpleblog/ScreenShot2016-10-03.png)

2. Change the authentication to **individual user** 
![image](../images/simpleblog/ScreenShot1.png)
Click **OK** to create project
![image](../images/simpleblog/ScreenShot2.png)

3. Create a new class in the Models folder called ***Post.cs***
![image](../images/simpleblog/ScreenShot3a.png)
![image](../images/simpleblog/ScreenShot3b.png)

4. Create a new class in the Data folder called ***SimpleBlogDataContext.cs***
Note:The dataContext  is your in between the code and database.  It lets you talk to your database in code.  
Inherit from DbContext class **:DbContext**

![image](../images/simpleblog/ScreenShot4.png)

  * Add the top of your class make sure you add the  following using statement:
```csharp
using Microsoft.EntityFrameworkCore;
using SimpleBlog.Models;
```

  * Create a Dbset of type post 
```csharp  
       public DbSet<Post> posts { get; set; } 
```

  * Register the context with dependency injection 
In the ***startup.cs*** file add the SimpleBlogDataContext as a service in the configuration service method.  
Tell it what database provider to use and get the connection string for that database.  The connection string for that database is located in appsetting.json
Place it just before the applicationDBContext service.  
```csharp
     services.AddDbContext<ApplicationDbContext>(options =>
                options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));

```

![image](../images/simpleblog/ScreenShot4a.png)
 

Since were using dependency injection 
Make sure you a contstructor to the dbcontext class that takes 
```csharp
    public SimpleBlogDataContext(DbContextOptions<SimpleBlogDataContext> options) : base(options)
```

  *  Type **Add-Migration** in the package manager console.  This gets everything ready to create a database.  
```csharp
    PM> Add-Migration IntialDB -context ASimpleBlogDataContext

```
in the data folder you should see a folder called ***Migrations*** and in that folder a file name ASimpleBlogDataContext
Type **Updata-Database** command to create the database
```csharp
    PM> Update-Database -Context AsimpleBlogDataContext 

```

5.  Now we will scaffold out a ***PostController*** so we can interact with our data.  Scaffolding out a controller creates the CRUD operation so we can interact with it

![image](../images/simpleblog/ScreenShot5a.png)
![image](../images/simpleblog/ScreenShot5b.png)

Now run your program and browse http://localhost:portnumber/posts/index
you should be able to perform the basic CRUD operations







