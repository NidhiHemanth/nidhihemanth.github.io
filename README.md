# Nidhi's Personal Website

This repository contains the code of my personal blog, built using [hugo-PaperMod](https://github.com/adityatelange/hugo-PaperMod) and [Github Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages).

Check out my website at [nidhihemanth.github.io](https://nidhihemanth.github.io)👋

## How to run this project locally?

### 1) Installing pre-requisites

- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Go](https://go.dev/doc/install) 
- [Dart SASS](https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass)
- Latest version of [Hugo](https://github.com/gohugoio/hugo/releases)

Visit [here](https://gohugo.io/installation/) for detailed instructions.

### 2) Set up the project locally

Clone the project on your local machine.

For example, using https ```git clone https://github.com/nidhihemanth/nidhihemanth.github.io.git```

### 3) Run the hugo server

Open the command line in the cloned directory.

Run ```hugo server``` which will run the application locally on the default port [http://localhost:1313/](http://localhost:1313/) 

Now you can view & test your changes locally before deploying it 🍜

## How to create your own website using Hugo & Github Pages?

Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again. 

Hugo provides us a wide variety of [themes](https://themes.gohugo.io/) which makes it easier to create & maintain simple websites. The theme used in this repository is called [PaperMod](https://themes.gohugo.io/themes/hugo-papermod/).

### 1) Create a new site using Hugo

We assume all the [prerequisites](#installing-pre-requisites) have already been installed.

1. Create a new site using the command ```hugo new site <name of site> --format yaml``` in your command line.
2. Change current directory to project directory using ```cd <name of site>```. This creates the directory structure of our project.
3. Add the desired theme to your project by executing the following commands
   ```
   git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
   cd themes/PaperMod
   git pull
   ```
4. From the root directory execute the following command to add the theme as a [submodule](https://www.atlassian.com/git/tutorials/git-submodule) to your repository.
   ```
   git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
   ```
   Replace the links in step 3 & 4 to the github repository of your desired theme.
5. Update the theme in your hugo.yaml file by setting the theme as ```theme: "PaperMod"```

### 2) Create & push code to a new repository

1. Initialise the project as git repository executing ```git init``` from the root directory of the hugo site.
2. Create a new repository on Github and name it as `<username>.github.io`. This will be the URL of your GitHub Pages website.
3. In the `hugo.yoml` file update baseURL to point to your github page `baseURL: "https://<username>.github.io"`
4. Push the hugo site to the empty Github repository
   ```
   git remote add origin https://github.com/<username>/<username>.github.io.git
   git branch -M main
   git commit -m "first commit"
   git push -u origin main
   ```

Additionally, create new pages using ```hugo new <filename>``` on your website, refer to your respective theme documentations for detailed instructions.

### 3) Configure Github Actions to Publish to the Github Pages

1. Manually create a new branch in the Github repository named `gh-pages`. This is the branch github pages will fetch from.
2. Allow Read and Write Permissions on the Workflow under Settings > Actions > General > Workflow permissions
3. Set the GitHub Pages site to build from the `gh-pages` branch under Settings > Pages > Build and deployment
4. Define custom github actions to fetch code from the *main* branch and create a static site in the `gh-pages` branch.
   - For that add the following file under with the same directory structure [.github/workflows/deploy.yml](.github/workflows/deploy.yml) under your project root directory.
   - (You might want to change the version of hugo being downloaded to the latest version in the `curl` command under "Setup Hugo")

Github automatically deploys the code at `https://<username>.github.io`

To deploy your website under a custom Domain Name refer to [this](https://theplaybook.dev/docs/deploy-hugo-to-github-pages/) article.
