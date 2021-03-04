*selfcontained application docker image*
```
docker build --pull -t dotnetapp:alpine-x64-selfcontained -f Dockerfile.alpine-x64-selfcontained .
```

```
docker run --rm dotnetapp:alpine-x64-selfcontained
```

**inspired from **
[dotnet-docker/samples/dotnetapp/](https://github.com/dotnet/dotnet-docker/tree/main/samples/dotnetapp)

