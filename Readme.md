# my_hugo_site

A static blog site built with [Hugo](https://gohugo.io/) and automatically deployed to [Firebase Hosting](https://firebase.google.com/products/hosting) via [Google Cloud Build](https://cloud.google.com/build).

## Overview

This project uses:

- **Hugo** – A fast and flexible static site generator.
- **Theme** – [`hello-friend-ng`](https://github.com/rhazdon/hugo-theme-hello-friend-ng), a clean and minimal Hugo theme.
- **Google Cloud Build** – CI/CD pipeline that automatically builds and deploys the site on every push.
- **Firebase Hosting** – Hosts the generated static files.

## Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.96.0 or later)
- [Firebase CLI](https://firebase.google.com/docs/cli)
- A Firebase project

## Local Development

1. **Clone the repository**

   ```bash
   git clone https://github.com/VaibhavSoni24/my_hugo_site.git
   cd my_hugo_site
   ```

2. **Start the local development server**

   ```bash
   hugo server -D
   ```

   The site will be available at `http://localhost:1313/`.

3. **Build the static site**

   ```bash
   hugo
   ```

   The generated files will be placed in the `public/` directory.

## Deployment

Deployment is handled automatically by Google Cloud Build whenever changes are pushed to the repository. The build pipeline (defined in `cloudbuild.yaml`) performs the following steps:

1. Downloads the Firebase CLI.
2. Downloads and extracts the specified Hugo Extended binary.
3. Runs `hugo` to generate the static site.
4. Deploys the generated site to Firebase Hosting.

### Manual Deployment

To deploy manually, ensure you have Hugo and the Firebase CLI installed, then run:

```bash
hugo
firebase deploy --only hosting
```

## Configuration

Site-wide settings are managed in `config.toml`:

| Setting        | Value                              |
|----------------|------------------------------------|
| `baseURL`      | `http://example.org/`              |
| `languageCode` | `en-us`                            |
| `title`        | `Blogging with Hugo and Cloud Build` |
| `theme`        | `hello-friend-ng`                  |

> **Note:** Update `baseURL` to your actual production URL and `title` to your desired site name before deploying.

## Project Structure

```
my_hugo_site/
├── archetypes/        # Content templates
├── public/            # Generated static site output (not committed)
├── themes/            # Hugo themes
│   └── hello-friend-ng/
├── cloudbuild.yaml    # Google Cloud Build pipeline
├── config.toml        # Hugo site configuration
├── firebase.json      # Firebase Hosting configuration
└── .firebaserc        # Firebase project alias
```

## License

This project is open source. See the repository for details.
