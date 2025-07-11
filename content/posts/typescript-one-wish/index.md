+++
title = 'Typescript One Wish'
date = 2025-03-11T14:59:24-06:00
+++

It's optional name parameters...thank you for coming to my Ted Talk

### Here's why

While there are many features I would like to be added in Typescript there is one major one that needs to make it's way over from C#. That would be optional named parameters. At this point I'm not sure how this hasn't been added into the language. Personally, I used it a lot when writing in C# and I've ran into a few _self inflicted_ bugs that named parameters would have prevented. For those who don't program in a language that has named parameters it allow you to specify the parameter when calling a function or method. 

Below is an example of a simple semi-pseudo C# code which is a class and a method that takes in two parameters and makes an http call.

```c#
public static class HttpClient
{
	public static async Task<HttpResponseMessage> Post(string baseUrl, string parameter)
	{
		return await _httpClient.Post(baseUrl, parameter);
	}
}

```

Calling this method using the optional name parameters would look like this:

```c#
var response = await HttpClient.Post(baseUrl: "https://www.github.com", parameter: "repo=linux");
```

For small method like this feature might seem overkill and it is. But for larger methods that take in three or four parameters chained with optional parameters this can help save you from passing in the wrong parameter. I can already hear the comments "if you write clean code you shouldn't need that many parameters" and I hear you....but sometimes life doesn't work out like that. You have to make comprises with good standard to meet technical or business goals.

### Conclusion

Look I get that vanilla JavaScript doesn't have this feature, but for a language that is modeled after C# this blows my mind?! There has been proposals to add this feature and I really hope that it gets added. 

### PS

I know you can get around this by passing in an object, and that is the current common solution. I think that is fine for large configuration needs, but for simple parameters this would be a nice addition.
