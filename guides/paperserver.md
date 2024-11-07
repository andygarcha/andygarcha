# Installing Paper on Raspberry Pi
All of this information is pulled from [the Paper API page](https://docs.papermc.io/misc/downloads-api).

## Getting the latest version 
```
#!/usr/bin/env sh

PROJECT="paper"

LATEST_VERSION=$(curl -s https://api.papermc.io/v2/projects/${PROJECT} | \
    jq -r '.versions[-1]')

echo "Latest version is $LATEST_VERSION"
```

## Getting the latest stable build number
```
#!/usr/bin/env sh

PROJECT="paper"
MINECRAFT_VERSION="1.21.3"

LATEST_BUILD=$(curl -s https://api.papermc.io/v2/projects/${PROJECT}/versions/${MINECRAFT_VERSION}/builds | \
    jq '.builds | map(select(.channel == "default") | .build) | .[-1]')

if [ "$LATEST_BUILD" != "null" ]; then
    echo "Latest stable build is $LATEST_BUILD"
else
    echo "No stable build for version $MINECRAFT_VERSION found :("
fi
```

## Downloading the latest stable build
```
#!/usr/bin/env sh

PROJECT="paper"
MINECRAFT_VERSION="1.21.3"

LATEST_BUILD=$(curl -s https://api.papermc.io/v2/projects/${PROJECT}/versions/${MINECRAFT_VERSION}/builds | \
    jq -r '.builds | map(select(.channel == "default") | .build) | .[-1]')

if [ "$LATEST_BUILD" != "null" ]; then
    JAR_NAME=${PROJECT}-${MINECRAFT_VERSION}-${LATEST_BUILD}.jar
    PAPERMC_URL="https://api.papermc.io/v2/projects/${PROJECT}/versions/${MINECRAFT_VERSION}/builds/${LATEST_BUILD}/downloads/${JAR_NAME}"

    # Download the latest Paper version
    curl -o server.jar $PAPERMC_URL
    echo "Download completed"
else
    echo "No stable build for version $MINECRAFT_VERSION found :("
fi
```