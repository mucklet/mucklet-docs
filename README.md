# Mucklet Docs

The public documentation and release-notes site for [Mucklet](https://mucklet.com/).

It is built with [Hugo](https://gohugo.io/) and the [Docsy](https://www.docsy.dev/) theme. The first published content area is **Releases**.

## Local development

Prerequisites:

- Hugo Extended 0.160.1 or newer
- Node.js and npm

Install the generated Docsy frontend dependencies, then start the development server:

```powershell
npm ci
hugo server --environment development
```

Open `http://localhost:1313/`. In the development environment, the navigation link back to Mucklet points to `http://localhost:6460/`.

Build the production site with:

```powershell
hugo --minify --environment production
```

The generated static files are written to `public/`.

## Content

Release notes live in `content/en/releases/`, one leaf bundle per release. Keep images used by an entry in that bundle, rather than hotlinking them.
