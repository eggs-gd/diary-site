# Attention Journal — site

Static SvelteKit landing page for the Attention Journal (觀明) app, plus the
installable PWA served at `/pwa`.

## Development

```sh
yarn install
yarn dev
```

## Checks

```sh
yarn run check
yarn build
```

## GitHub Pages

The project uses `@sveltejs/adapter-static` and deploys through
`.github/workflows/deploy.yml`. During GitHub Actions builds, SvelteKit uses the
repository name from `GITHUB_REPOSITORY` as `paths.base`; relative asset paths
keep it working at the custom domain root. `static/CNAME` binds the custom domain
`journal.eggs.gd`.

## PWA (`/pwa`)

The web build of the app (repo `eggs-gd/diary`) is produced locally and copied
into `static/pwa`, then committed here:

```sh
# in the diary app repo, next to this one
cd ../diary/diary
yarn build:pwa   # builds with base=/pwa and copies into ../../diary-site/static/pwa

# back here
git add static/pwa && git commit -m "update pwa" && git push
```
