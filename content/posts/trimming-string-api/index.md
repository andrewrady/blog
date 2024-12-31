+++
title = 'Trimming Strings For Api Using Dotnet'
date = 2024-12-26T23:39:49-07:00
tags = ['c#', 'dotnet']
+++

# Keeping data clean

One important aspect of managing data coming in through our api(s). Of course this is what data types and validation is for, but an easily overlooked aspect is handling strings and how we want store them in the database.
It's an easy oversight for anyone who hasn't handle a large amount of data that us being used by multiple teams. An easy example is when two systems are comparing an email, but one system didn't trim any white space and the user inputed
their email with a space at the end. Sounds simple, right? It happens much more often then you'd think. We don't want to add a lot of extra logic every time we compare strings to ensure there isn't any white space unless abosultely nessicary.
Which is why it's important to add logic to handle this on every request - which is pretty easy with Donet.

## Solution

[Linked](https://github.com/andrewrady/dotnet-trim-strings) is an example repo of a dotnet generated project for a webapi. You can generate it with the dotnet command `dotnet new webapi -n API -controllers` - I still use controllers for the most part. There's a new post endpoint that takes in the standard WeatherForcast class that is included from the generated code and returns it back. 
This is helpful because it will show the results of the converter in swagger. We'll create a new `TrimStringConverter` class that will handle all of the logic.

```c#
using System.Text.Json.Serialization;

public class TrimStringConverter : JsonConverter<string?>
{
    public override string? Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
    {
        return reader.GetString().Trim();
    }

    public override void Write(Utf8JsonWriter writer, string? value, JsonSerializerOptions options)
    {
        writer.WriteStringValue(value);
    }
}
```

Most of the time you'll see Converters used on the data annotion level which can be very granular, but we want to apply this to every property that is a string. We can do that by adding a few lines in the `Program.cs` file.

```c#
builder.Services
    .AddControllers()
    .AddJsonOptions(option =>
    {
        option.JsonSerializerOptions.Converters.Add(new TrimStringConverter());
    });
```

Now if we hit out endpoint `http://localhost:5175/WeatherForecast` with a payload with intended spaces in the properties that strings values it will return with those trimmed. This will happen before the values hit the controller. If you put a break point on the method name of the controller you can see the values update automatically.

### Payload
```json
{
  "date": "2024-12-27",
  "temperatureC": 29,
  "summary": "Warm "
}
```

### Response
```json
{
  "date": "2024-12-27",
  "temperatureC": 29,
  "temperatureF": 84,
  "summary": "Warm"
}
````

## Improvements

While this is a good first step we an improve on this. Keeping strings clean and not having additional white space is important and we should also stop any blank string from being saved in columns. This can cause headaches for anyone who has to maintain the data later.

```c#
using System.Text.Json.Serialization;

public class TrimStringConverter : JsonConverter<string?>
{
    public override string? Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
    {
        var value = reader.GetString();
        if (string.IsNullOrWhiteSpace(value))
        {
            return null;
        }

        return value.Trim();
    }

    public override void Write(Utf8JsonWriter writer, string? value, JsonSerializerOptions options)
    {
        writer.WriteStringValue(value);
    }
}
```

## Conclusion

Something as simple handing empty strings on requests can easily overlooked, but can cause a lot of headaches down the road if not handled. With Dotnet's middleware it makes it easy to take our custom converters and apply them to all requests before going to the controllers.
There may be times where we only want to apply these with data annotations (which is a more common way to use converters) so applying them to the middlware is something you'll need to consider if you want the behavior by default.

