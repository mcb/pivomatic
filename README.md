# pivomatic :beer:
Bash Script to wrap around Pivnet CLI and OM

```bash
Usage: pivomatic -t <pivnet-token> -o <opsman-url> -u <opsman-user> -p <opsman-pass> -s <product-slug> -r <release>
```


## Known issues

- Known to not work with RabbitMQ Tile, as it provides multiple files labelled as "Software". As such the script can't upload the files directly. 
