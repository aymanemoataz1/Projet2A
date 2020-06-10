# UnityRestClient

Un client reposant qui permet de faire de simples appels GET, POST, PUT et DELETE http depuis Unity3d.
## Comment l'utiliser ?

Il existe actuellement deux scènes dans le projet qui peuvent être utilisées pour savoir comment l'utiliser. Également quelques extraits ci-dessous pour faire la démonstration de ses fonctionnalités dans Unity3d.


1. exemple d'appel de l'api azur

```csharp
// setup the request header
RequestHeader clientHeader = new RequestHeader {
    Key = clientId,
    Value = clientSecret
};

// build image url required by Azure Vision OCR
ImageUrl imageUrl = new ImageUrl {
    Url = "https://github.com/dilmerv/AzureVisionAPI/blob/master/images/IMG_5301.JPG?raw=true"
};

// send a post request
StartCoroutine(RestWebClient.Instance.HttpPost(baseUrl, JsonUtility.ToJson(imageUrl), (r) => OnRequestComplete(r), new List<RequestHeader> 
{
    clientHeader
}));
```

2. Exemple Get and Post
```csharp
// send a get request
StartCoroutine(RestWebClient.Instance.HttpGet($"{baseUrl}api/values", (r) => OnRequestComplete(r)));

// setup the request header
RequestHeader header = new RequestHeader {
    Key = "Content-Type",
    Value = "application/json"
};

// send a post request
StartCoroutine(RestWebClient.Instance.HttpPost($"{baseUrl}api/values", 
JsonUtility.ToJson(new Player { FullName = "John Doe" }), 
    (r) => OnRequestComplete(r), new List<RequestHeader> { header } ));
```
