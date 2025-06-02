+++
title = 'Entity Framework Core Query'
date = 2025-06-01T21:32:45-06:00
+++

# Query Performance

As Dotnet developers it’s very common to use ORMs like Entity Framework to work with databases. While it’s not the most performance tool, it’s externally useful and flexible to use. With that it’s important to remember that the methods we use can change the performance of the query. Weather to use a `Where` followed by a `FirstOrDefault` or should we just use the `FirstOrDefault`? And what kind of query statement will either of these make? 

I found a cool little settings you add to your `appsetting.Development.json` file that will show the query statement used in the console.  Which is a incredibly useful thing to look at when looking at the performance of our application. This should work for .NET 6+ applications. In the logging object we can add “Information” values for “Microsoft.EntityFrameworkCore.Database.Commad”.

### Examaple

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
     ,"Microsoft.EntityFrameworkCore.Database.Command": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

Recently, we took some time to look over our queries at work. We were able to take the results from these and plug them into SSMS or Azure Data Studio to evaluate ways to improve them.
