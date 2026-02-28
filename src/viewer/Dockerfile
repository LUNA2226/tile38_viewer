# ===== BUILD STAGE =====
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copia apenas o csproj primeiro (melhora cache e evita erro de caminho)
COPY src/viewer/*.csproj ./viewer/

WORKDIR /src/viewer
RUN dotnet restore

# Copia o restante do código
COPY src/viewer/. ./

RUN dotnet publish -c Release -o /app/publish

# ===== RUNTIME STAGE =====
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "tile38_viewer.dll"]