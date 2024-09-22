```js
const nextConfig = {
	output: "standalone",
};
```

-   Install sharp to make the images work correctly

```cli
npm install sharp
```

```js
const fs = require("fs");

const copy = (src, dest) => {
	fs.cpSync(src, dest, {
		recursive: true,
		errorOnExist: true,
	});
};

copy("./public", "./.next/standalone/public");
copy("./.next/static", "./.next/standalone/.next/static");
copy("./web.config", "./.next/standalone/web.config");
```

-   Install http platform handler on the server

-   web.config

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <handlers>
            <add name="httpPlatformHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified" requireAccess="Script" />
        </handlers>
        <httpPlatform stdoutLogEnabled="true" stdoutLogFile=".\node.log" startupTimeLimit="20" processPath="C:\Program Files\nodejs\node.exe" arguments=".\server.js">
            <environmentVariables>
                <environmentVariable name="PORT" value="%HTTP_PLATFORM_PORT%" />
                <environmentVariable name="NODE_ENV" value="Production" />
            </environmentVariables>
        </httpPlatform>
    </system.webServer>
</configuration>
```
