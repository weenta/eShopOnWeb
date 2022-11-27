# Microsoft eShopOnWeb ASP.NET Core Reference Application

[Getting Started for Beginners](https://github.com/dotnet-architecture/eShopOnWeb/wiki/Getting-Started-for-Beginners) guide

[Steve "ardalis" Smith](https://twitter.com/ardalis) recorded [a live stream providing an overview of the eShopOnWeb reference app](https://www.youtube.com/watch?v=vRZ8ucGac8M&ab_channel=Ardalis) in October 2020. 

## Local Setup
### 创建Db
connect sql-server
```
server=localhost; Database=FakeTwoDb; User Id=sa; Password=Password12!;
```

 ```
dotnet restore
dotnet tool restore
dotnet ef database update -c catalogcontext -p ../Infrastructure/Infrastructure.csproj -s Web.csproj
dotnet ef database update -c appidentitydbcontext -p ../Infrastructure/Infrastructure.csproj -s Web.csproj
```

### Add Migration
``` 
-- create migration (from Web folder CLI)
dotnet ef migrations add InitialModel --context catalogcontext -p ../Infrastructure/Infrastructure.csproj -s Web.csproj -o Data/Migrations

dotnet ef migrations add InitialIdentityModel --context appidentitydbcontext -p ../Infrastructure/Infrastructure.csproj -s Web.csproj -o Identity/Migrations
```

### run app
in Web ```dotnet run```, will listening on `https://localhost:5501/`
in PublicApi ```dotnet run``` will listening on `https://localhost:5099/swagger/index.html`