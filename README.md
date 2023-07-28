# GitHub Pages/Jekyll Password Protection
Automatically password protect (with encryption) certain pages on GitHub Pages/Jekyll sites using [PageCrypt](https://github.com/Greenheart/pagecrypt).

## Demo
This repository serves as an example repository for password protecting pages. See [example.html](https://evanbaldonado.github.io/github-pages-jekyll-password-protection/example.html) (password: `examplepassword`) and [example-2.html](https://evanbaldonado.github.io/github-pages-jekyll-password-protection/example-2.html) (password: `repo_by_evanbaldonado.com!`).

## Usage
1. Configure passwords for .html pages in [_protected_pages.txt](https://github.com/evanbaldonado/github-pages-jekyll-password-protection/blob/main/_protected_pages.txt).
    - Add one file per line (space-delimited in the format `filename.html password`).
    - Note that GitHub converts markdown (.md) files to .html files.
    - Because this file begins with an underscore, it will not be published when your site is deployed.
2. Add a GitHub action/workflow for encrypting pages: [/.github/workflows/pages-with-encryption.yml](https://github.com/evanbaldonado/github-pages-jekyll-password-protection/blob/main/.github/workflows/pages-with-encryption.yml).
    - Make sure that it targets the correct branch you want to use for deployment (see line 6: `branches: ["main"]`).
3. Automatically deploy this repository with GitHub Pages using GitHub Actions: `Settings > Code and automation > Pages > Build and deployment > Source > Github Actions`. You can manually run this Action; it will also automatically run when you update your repository.

## Security
- Static websites deployed with GitHub pages can't run server-side code, which means that traditional authentication approaches to access protected files aren't possible. Additionally, GitHub pages does not support .htaccess files, another easy way to password-protect pages.
- This method relies on [PageCrypt](https://github.com/Greenheart/pagecrypt) to encrypt pages using the Web Crypto API. This allows the user to view/access/download pages but only see their contents with a password.
    - Because the user can access these files, they can download them and perform a brute-force attack to attempt to unencrypt them. Your files are only as secure as the Web Crypto API, PageCrypt, _and_ your passwords.
    - PageCrypt only encrypts .html files. For other assets (ex: .css files, .js files, and images), consider inlining them if they must remain private. See [PageCrypt's documentation](https://github.com/Greenheart/pagecrypt#readme).
- Note: although the password file (_protected_pages.txt) is not published along with your site, anyone with access to the repository itself can view it.
- For more information, see [PageCrypt's documentation](https://github.com/Greenheart/pagecrypt#readme).

## License & credits
This repository by [Evan Baldonado](https://evanbaldonado.com) is published under the [AGPL-3.0](LICENSE) license. It utilizes [PageCrypt](https://github.com/Greenheart/pagecrypt) by Samuel Plumppu (a complete rewrite of Maximillian Laumeister's original code).

## Contributing
Feel free to submit issues/pull requests!

## Contact
You can [start a discussion](https://github.com/evanbaldonado/github-pages-jekyll-password-protection/discussions) on this repository or contact [password@evanbaldonado.com](mailto:password@evanbaldonado.com) with questions. The [PageCrypt repository](https://github.com/Greenheart/pagecrypt) also has additional information about the encryption process itself.
