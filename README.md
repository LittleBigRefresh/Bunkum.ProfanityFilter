# Warning! This repository is no longer updated.
This project has moved development and source code to the central Bunkum repository.

You can find the new source code location under [LittleBigRefresh/Bunkum](https://github.com/LittleBigRefresh/Bunkum).

# Bunkum.ProfanityFilter
A wrapper around Profanity.Detector for Bunkum

## Example usage

```csharp
// Program.cs
BunkumHttpServer server = new();
server.AddProfanityService();
```

```csharp
// FilterEndpoints.cs
[Endpoint("/censorSentence")]
[NullStatusCode(HttpStatusCode.BadRequest)]
public string? CensorSentence(RequestContext context, ProfanityService service)
{
    string? input = context.QueryString.Get("input");
    if (input == null) return null;
    
    return service.CensorSentence(input);
}
```

`AddProfanityService` contains optional parameters to allow/deny certain phrases. You can use them like this:

```csharp
server.AddProfanityService(new []{"f@ck"}, new []{"awjkdh"});
```
