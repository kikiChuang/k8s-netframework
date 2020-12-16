FROM microsoft/dotnet-framework:4.6.1-sdk-windowsservercore-1803 AS build
WORKDIR /app

COPY *.sln .
COPY WebApplication1/*.csproj ./WebApplication1/
RUN nuget restore


RUN msbuild /p:Configuration=Release


FROM microsoft/aspnet:4.6.1-windowsservercore-1803 AS runtime
WORKDIR /inetpub/wwwroot
COPY --from=build /app/WebApplication1/. ./