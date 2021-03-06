# HttpToSocks5Proxy
C# Http to Socks5 proxy implementation

HttpToSocks5Proxy implements the IWebProxy interface and can therefore be used with all libraries that support HTTP/HTTPS proxies

## Usage
Example use with the .NET HttpClient

```c#
var proxy = new HttpToSocks5Proxy("127.0.0.1", 1080);
var handler = new HttpClientHandler();
handler.Proxy = proxy;
handler.UseProxy = true;
HttpClient hc = new HttpClient(handler, true);
var httpsGet = hc.SendAsync(new HttpRequestMessage(HttpMethod.Get, "https://httpbin.org/ip"));
Console.WriteLine("HTTPS GET: " + httpsGet.Result.Content.ReadAsStringAsync().Result);
```
</br>

Or with it's original use-case with the Telegram Bot Library (https://github.com/TelegramBots/Telegram.Bot)
```c#
var proxy = new HttpToSocks5Proxy(Socks5ServerAddress, Socks5ServerPort);
proxy.ResolveHostnamesLocally = true; // Allows you to use proxies that are only allowing connections to Telegram
TelegramBotClient Bot = new TelegramBotClient(API_KEY, proxy);
```

## Installation

Install as [NuGet package](https://www.nuget.org/packages/HttpToSocks5Proxy/):

Package manager:

```powershell
Install-Package HttpToSocks5Proxy
```