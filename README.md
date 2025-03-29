# playreia-cdn

This is the service used to act as host for CDN files.

## Process

1. Vercel hosts the files and serves them in `/static/<file_or_folder>`
2. We configured our DNS to route to Vercel and then we setup another DNS at [cdn.playreia.com](https://cdn.playreia.com) to redirect to our CDN provider (currently Fastly)
3. On the CDN provider, we set the origin to point to the Vercel domain and then we set the domain on the CDN to be cdn.playreia.com

We can now use cdn.playreia.com to route through Fastly to save on bandwidth and to serve images closer to users. This setup also allows us to easily fallback to another service via the DNS if anything ever happens to Fastly 10 years from now.
