docker build -t servercore-ltsc2022:latest -m 2GB .
docker run -it --rm servercore-ltsc2022

docker run -v "$(pwd):C:\code" msbuild msbuild yourproject.sln /p:Configuration=Release

