# ===== BUILD =====
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copia o projeto inteiro
COPY . .

# Entra na pasta correta
WORKDIR /app/src/viewer

# Restore e Publish usando caminho explícito
RUN dotnet restore tile38_viewer.csproj
RUN dotnet publish tile38_viewer.csproj -c Release -o /publish

# ===== RUNTIME =====
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app

COPY --from=build /publish .

ENTRYPOINT ["dotnet", "tile38_viewer.dll"]