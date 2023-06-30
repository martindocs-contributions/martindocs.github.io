# Git Workflow
## Steps:
### 1. Create a new Git repository and add the theme for GitHub pages:
- Create new repository, click `New repository` and type the name of repo. In order to have repository on GitHub pages the name of repo must be: `martindocs.github.io`
- Add a new file `index.md` and include some markdown.
- To create a theme for Github Pages, create an `_config.yml` file in the root directory and add the following text:
    
        title: Git Workflow
        description: Development workflow for Gitflow.
        show_downloads: true
        google_analytics:
        theme: jekyll-theme-leap-day
    


### 2. Create an additional branch:
- To support Git workflow, we should have at least two long-lived branches: `main` which contains a copy of the production code, and `develop` for creating new features before merging with the `main` branch.
- Use the Git UI to create an additional new `develop` branch.
- To protect these two branches from accidental modification, go to `Settings -> Branches -> Add rule`. Enter the name of the branch you want to protect and select `Require a pull request before merging`, then click `Create rule`.

### 3. Development work on new features:
- Clone the repository to your local workstation:

        git clone https://github.com/martindocs/martindocs.github.io.git


- Create a local `develop` branch that tracks the shared `develop` repository branch:

        git checkout -b develop origin/develop


- Create a feature branch: `git checkout -b feature/initials-ticket_number-description_of_what_you_are_working_on`

        git checkout -b feature/mt-123-site-content


- Make changes to the `index.md` file.
- Stage the changes and commit them to the local repository on the feature branch, then push the local changes to the shared repository:

        git add .
        git commit -m "Added features to the site"
        git push origin feature/mt-123-site-content -u

### 4. Create a pull request:
- On GitHub, create a pull request by clicking on `Pull request -> New pull request`.
- From the left drop-down menu, choose the branch you are merging to, and from the second drop-down menu, choose the branch you want to merge:

        develop <- feature/mt-123-site-content

- Click on `Create pull request` and write additional comments, then click `Create pull request`.
- This will create a pull request for other members to review and approve.
- When working individually, you can click `Merge pull request -> Confirm merge` to merge the changes from the feature branch to the `develop` branch.
- At that point, you can delete the feature branch if you know that you will not be doing more work on it. Click `Delete branch` to delete it.