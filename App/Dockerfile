# �tape 1 : Construire l'application
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app

# Copier les fichiers du projet et restaurer les d�pendances
COPY *.csproj .
RUN dotnet restore

# Copier le reste des fichiers de l'application
COPY . .
RUN dotnet publish -c Release -o /app/publish

# �tape 2 : Cr�er l'image d'ex�cution
FROM mcr.microsoft.com/dotnet/runtime:9.0
WORKDIR /app

# Copier les fichiers publi�s depuis l'�tape de build
COPY --from=build /app/publish .

# D�finir le point d'entr�e de l'application
ENTRYPOINT ["dotnet", "DotNet.Docker.dll"]
