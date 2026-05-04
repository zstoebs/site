# site

Steps to host a Hugo After Dark site on GitHub pages: 
1. Download the quick start code locally from the [After Dark](https://after-dark.habd.as/feature/quick-install/) website. 
2. Run `hugo` to generate website files in `public/`. 
3. Host the generated files in `public/` on the GitHub pages repo, i.e., a repo named [your username].github.io. 
4. Host the source files in the parent directory in a separate repo, with `public/` ignored. 
- These are the files at the highest level, mainly Markdown files, that Hugo uses to build the static site. 
5. Create a GitHub action or workflow in the source file repo. **(optional)** 
  - Modifying source files and then pushing to source repo will trigger a rebuild and push of the `public/` repo.
  - Hugo offers a copy&paste workflow for this purpose in the [docs](https://gohugo.io/hosting-and-deployment/hosting-on-github/).
