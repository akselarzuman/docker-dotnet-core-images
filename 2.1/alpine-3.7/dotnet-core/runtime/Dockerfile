FROM armutcom/dotnet-core-runtime:2.1.1-deps-alpine

RUN apk add --no-cache \
		ca-certificates \
        curl \
    && rm -rf /var/lib/apt/lists/*

# Install .NET Core
ENV DOTNET_VERSION 2.1.1
ENV DOTNET_DOWNLOAD_URL https://dotnetcli.blob.core.windows.net/dotnet/Runtime/$DOTNET_VERSION/dotnet-runtime-$DOTNET_VERSION-linux-musl-x64.tar.gz
ENV DOTNET_DOWNLOAD_SHA 092c966af4e3b697aaff06315c3eb3e342651643d3a1929bd33bb5f638e73989944ecdfb02ac18b251b797ff4cadcb312f4be9fe8627b4dd4b8dd8b51ea59ba1

RUN curl -SL $DOTNET_DOWNLOAD_URL --output dotnet.tar.gz \
    && echo "$DOTNET_DOWNLOAD_SHA dotnet.tar.gz" | sha512sum -c - \
    && mkdir -p /usr/share/dotnet \
    && tar -zxf dotnet.tar.gz -C /usr/share/dotnet \
    && rm dotnet.tar.gz \
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet
	
LABEL authors="Armut.com <dev@armut.com>"