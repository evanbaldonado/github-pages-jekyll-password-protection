# github-pages-jekyll-password-protection
Automatically password protect (with encryption) certain pages on GitHub Pages/Jekyll sites using [PageCrypt](https://github.com/Greenheart/pagecrypt).

## Usage
1. Configure passwords for .html pages in [_protected_pages.txt](https://github.com/evanbaldonado/github-pages-jekyll-password-protection/blob/main/_protected_pages.txt).
    - Add one file per line (space-delimited in the format `filename.html password`).
2. Add a GitHub action/workflow for encrypting pages: [./github/workflows/pages.yml](https://github.com/evanbaldonado/github-pages-jekyll-password-protection/blob/main/./github/workflows/pages.yml).
3. Automatically deploy this repository with GitHub Pages using Github Actions: `Settings > Code and automation > Pages > Build and deployment > Source > Github Actions`.
