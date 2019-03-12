# pivomatic
Bash Script to wrap around Pivnet CLI and OM. This script downloads and uploads with a single command. Intended to be used on a Jump Server for easy internet access.
Note: Sometimes the Pivnet Api (network.pivotal.io) returns multiple files marked as software, in this case the process is stopped and the id needs to be provided with a flag.

Pivomatic uses default [om](https://github.com/pivotal-cf/om) environment variables and you can use the same in `pivomatic` as suggested by the usage below.

```
Usage: pivomatic
        -t <pivnet-token>, PIVNET_TOKEN
        -o <opsman-url>, OM_TARGET
        -u <opsman-user>, OM_USERNAME
        -p <opsman-pass>, OM_PASSWORD
        -s <product-slug (optional, will enter interactive mode if not provided)>
        -r <release (optional, will enter interactive mode if not provided)>
        -i <id (optional)>
```

After upload it will provide you with a summary of uploaded products on OpsManager.

## Interactive Mode

Pivomatic has been extended to enter interactive mode if no product-slug nor release have been passed. It will present you with a list of possible options for both slug and release:

```
$ ./pivomatic -t <token>
Checking for installed scripts
Logged-in successfully
Here's a list of available products:

NAME                                                      SLUG
----                                                      ----
MySQL for PCF                                             pivotal-mysql
Pivotal Application Service (formerly Elastic Runtime)    elastic-runtime

=> Please choose one and provide the slug:
pivotal-mysql

✓ Will upload pivotal-mysql
Searching for available releases...
Here's what I found on network.pivotal.io:

VERSION                  DESCRIPTION
-------                  -----------
2.5.3                    MySQL for PCF v2.5.3. It provides on-demand single node

=> Please choose one and provide the version:
2.5.3
```

Once all options are satisfied, `pivomatic` will upload as if you passed these params along the initial command.

## Requirements

- [pivnet-cli](https://github.com/pivotal-cf/pivnet-cli)
- [om](https://github.com/pivotal-cf/om)
- [jq](https://stedolan.github.io/jq/)

### Why BASH? No GOLANG?

Was on the go while writing this and only had my iPad with me with access to that Jump Box. Served me well and will do the same for you.
