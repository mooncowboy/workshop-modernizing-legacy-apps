FROM microsoft/dotnet:2.2-sdk

WORKDIR /src
COPY ["razor1.csproj", "./"]
RUN dotnet restore "./razor1.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "razor1.csproj" -c Release -o /app
RUN dotnet publish "razor1.csproj" -c Release -o /app
WORKDIR /app
EXPOSE 80
ENTRYPOINT ["dotnet", "razor1.dll"]
