FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copia tudo
COPY . .

# Vai para a pasta correta do projeto
WORKDIR /src/src/viewer

# Restaura explicitamente o projeto
RUN dotnet restore tile38_viewer.csproj

# Publica explicitamente o projeto
RUN dotnet publish tile38_viewer.csproj -c Release -o /app/publish

# Runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "tile38_viewer.dll"]