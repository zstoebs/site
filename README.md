# zstoebs_source

Steps to host a Hugo After Dark site on GitHub pages: 
1. Download the quick start code locally from the [After Dark](https://after-dark.habd.as/feature/quick-install/) website. 
2. Run `hugo` to generate website files in `public/`. 
3. Host the files in `public/` on the GitHub pages repo. 
4. Host the source files in the parent directory in a separate repo, with `public/` ignored. 
5. Create a GitHub action or workflow in the source file repo. 
  - Modifying source files and then pushing to source repo will trigger a rebuild and push of the `public/` repo.
  - Hugo offers a workflow for this purpose in the [docs](https://gohugo.io/hosting-and-deployment/hosting-on-github/).
