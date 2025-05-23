# Deploy Multi-Version Documentation to GitHub Pages 🚀

[![Release](https://img.shields.io/github/v/release/rainboyan/deploy-github-pages?label=Release&logo=github)](https://github.com/rainboyan/deploy-github-pages/releases/latest)


This action is used to deploy multi-version documentation to [GitHub Pages](https://pages.github.com/).

## Usage

We recommend this action to be used in a dedicated job:

```yaml
jobs:
  # Build job
  build:
    permissions:
      contents: read  #  to fetch code (actions/checkout)
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: rainboyan/deploy-github-pages@v1
        env:
          TOKEN: ${{ secrets.GH_TOKEN }}    # GitHub Personal Access Token
          VERSION: '1.0.0-SNAPSHOT'         # The version of the documentation
          BRANCH: gh-pages                  # The branch to deploy
          FOLDER: build/docs                # The directory of the generated documentation
```

Here’s the directory structure for the documentation,

```bash
.
├── 1.0.0-SNAPSHOT
│   ├── ..
│   └── index.html
├── 1.0.x
│   ├── ..
│   └── index.html
├── latest
│   ├── ..
│   └── index.html
├── snapshot
│   ├── ..
│   └── index.html
└── README.md
```

After deployment is successful, you can access the documentation through the following links,

* https://OWNER.github.io/REPO/1.0.0-SNAPSHOT/
* https://OWNER.github.io/REPO/1.0.x/
* https://OWNER.github.io/REPO/latest/
* https://OWNER.github.io/REPO/snapshot/

### Environment Variables 🌎

| Variable | Description |
| -------- | ----------- |
| `TOKEN` | GitHub Personal Access Token |
| `VERSION` | The version of the documentation, if empty it will deploy to the ROOT |
| `BRANCH` | The branch to deploy |
| `FOLDER` | The directory of the generated documentation |
| `CNAME` | This will create a CNAME file |

## License

The scripts and documentation in this project are released under the [MIT License](LICENSE).

## Links

- [Grace Framework](https://github.com/graceframework/grace-framework)
- [Grace Plugins](https://github.com/grace-plugins)
