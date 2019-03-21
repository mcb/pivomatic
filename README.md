# pivomatic
Bash Script to wrap around Pivnet CLI and OM. This script downloads and uploads with a single command. Intended to be used on a Jump Server for easy internet access.
Note: Sometimes the Pivnet Api (network.pivotal.io) returns multiple files marked as software, in this case the process is stopped and the id needs to be provided with a flag.

Pivomatic uses default [om](https://github.com/pivotal-cf/om) environment variables and you can use the same in `pivomatic` as suggested by the usage below.

```bash
Usage: pivomatic
        -t <pivnet-token>, PIVNET_TOKEN
        -o <opsman-url>, OM_TARGET
        -u <opsman-user>, OM_USERNAME
        -p <opsman-pass>, OM_PASSWORD
        -s <product-slug>
        -r <release>
        -i <id (optional)>
```

After upload it will provide you with a summary of uploaded products on OpsManager.

## Requirements

- [pivnet-cli](https://github.com/pivotal-cf/pivnet-cli)
- [om](https://github.com/pivotal-cf/om)
- [jq](https://stedolan.github.io/jq/)
- `column` command line tool. As pointed out by @portepa it might be containted in the 'bsdmainutils' package.

### Why BASH? No GOLANG?

Was on the go while writing this and only had my iPad with me with access to that Jump Box. Served me well and will do the same for you.
