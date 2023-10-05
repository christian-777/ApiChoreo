FROM mcr.microsoft.com/dotnet/sdk:8.0 as build
WORKDIR /src
COPY ApiChoreo.csproj/ ./
RUN dotnet restore
COPY . .
RUN dotnet build
WORKDIR /src
RUN dotnet publish -c Release -o /app
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
EXPOSE 8080
COPY --from=build /app .
USER 10001
ENTRYPOINT ["dotnet", "ApiChoreo.dll"]