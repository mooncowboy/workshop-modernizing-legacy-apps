FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /app

COPY 01-container.csproj ./
RUN dotnet restore 01-container.csproj

# copy everything else and build app
COPY ./. ./
# WORKDIR /app/aspnetapp
RUN dotnet publish -c Release -o out

WORKDIR /app/out
ENTRYPOINT ["dotnet", "aspnetapp.dll"]