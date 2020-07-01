# Create DNS Record Action for GitHub

Creates a new CloudFlare DNS record.

## Usage via Github Actions

```yaml
name: example
on:
  pull_request:
    type: [opened, reopened]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: infraway/create-dns-record@v1.7
        with:
          type: "A"
          name: "review.example.com"
          content: "10.10.10.10"
          ttl: 1
          proxied: true
          token: ${{ secrets.CLOUDFLARE_TOKEN }}
          zone: ${{ secrets.CLOUDFLARE_ZONE }}
```

## Usage via docker image

```shell script
docker run -it --rm \
  -e "INPUT_TOKEN=1" \
  -e "INPUT_ZONE=2" \
  -e "INPUT_TYPE=A" \
  -e "INPUT_NAME=review.example.com" \
  -e "INPUT_CONTENT=10.10.10.10" \
  -e "INPUT_TTL=3600" \
  -e "INPUT_PROXIED=true" \
  infraway/cloudflare-create-dns-record 
```

## License

The scripts and documentation in this project are released under the [MIT License](LICENSE).
