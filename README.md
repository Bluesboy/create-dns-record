# CloudFlare DNS: Create or Update Record

Creates new CloudFlare DNS record.
Updates the record if it already exists.

Based on Action https://github.com/marketplace/actions/cloudflare-create-dns-record

## Usage example

```yaml
name: Create DNS Record

on:
  pull_request:
    type: [opened, reopened]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: Bluesboy/delete-dns-record@v2.1
        with:
          type: "A"
          name: "review.example.com"
          content: "10.10.10.10"
          ttl: 3600
          proxied: false
          token: ${{ secrets.CLOUDFLARE_TOKEN }}
          zone: ${{ secrets.CLOUDFLARE_ZONE }}
```
Creates `review.example.com` A record with 10.10.10.10, TTL set to 1 hour, not proxied via CloudFlare.

To create CloudFlare API Token follow instructions on https://developers.cloudflare.com/api/tokens/create

You can see Zone ID in bottom right of your zone overview page on CloudFlare


## License

The scripts and documentation in this project are released under the [MIT License](LICENSE).
