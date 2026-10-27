# Hugo blog

A small, theme-free Hugo blog ready to publish with GitHub Pages.

## Work locally

Install [Nix](https://nixos.org/download/) with flakes enabled. In a Git checkout, add `flake.nix` to Git so Nix can see it, then run:

```sh
git add flake.nix
nix develop
hugo server -D
```

The first `nix develop` resolves the flake input and creates `flake.lock`; commit that file to keep the development environment reproducible. The GitHub Pages workflow installs Hugo Extended 0.166.0 separately, so its version may differ from the Nix shell.

Open the local address shown in the terminal. Change the title and description in `hugo.toml` and edit `content/about.md` to make the site yours.

## Write a post

```sh
nix develop 
hugo new content posts/my-post.md
```

Edit the resulting Markdown file and set `draft = false` when it is ready to publish. Drafts appear locally with `-D` but are excluded from the published site. The sample post can be edited or deleted.

## Publish on GitHub Pages

1. Create a GitHub repository and push these files to its `main` branch.
2. In the repository, open **Settings → Pages** and select **GitHub Actions** as the source.
3. Push a change to `main` or run **Deploy Hugo site to Pages** from the Actions tab. The deployment job links to the published site.

The workflow uses the Pages-provided base URL, including the repository path for project sites. If your default branch is not `main`, update the workflow's branch filter. To use a custom domain, configure it in GitHub Pages settings.
