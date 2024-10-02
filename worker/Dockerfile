FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /source

COPY src/Worker/Worker.csproj ./ 

RUN dotnet restore

COPY src/Worker/. ./ 
RUN dotnet publish -c Release -o /out Worker.csproj

FROM mcr.microsoft.com/dotnet/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=build /out .
ENTRYPOINT ["dotnet", "Worker.dll"]
