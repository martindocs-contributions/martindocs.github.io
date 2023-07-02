# Gitflow & GitHub Workflow
## Gitflow Steps:
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
- To protect these two branches from accidental modification, go to `Settings -> Branches -> Add rule`. Enter the name of the branch you want to protect and select `Require a pull request before merging`, then click `Create rule`. Create rule for both branches.

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
- On GitHub, create a pull request by clicking on `Pull requests -> New pull request`.
- From the left drop-down menu, choose the branch you are merging to, and from the second drop-down menu, choose the branch you want to merge:

        develop <- feature/mt-123-site-content

- Click on `Create pull request` and write additional comments, then click `Create pull request`.
- This will create a pull request for other members to review and approve.
- When working individually, you can click `Merge pull request -> Confirm merge` to merge the changes from the feature branch to the `develop` branch.
- At that point, you can delete the feature branch if you know that you will not be doing more work on it. Click `Delete branch` to delete it.

### 5. Release the features:
When we get enough features we want merge with `main` branch then we need to:
- create new branch that is branched off from develop branch, we can use Github UI by first selecting the `develop` branch,
- next click again on the `develp` branch and type the name of the branch `release/1`.  
- after that click on the `Create branch: release/1 from 'develop'`
- we shouldn't do any major changes in that branch, but if we have some small changes we can do it
- next we merge `reelase/1` branch with `main` branch. Follow the <a href="#4-create-a-pull-request">STEP 4 - Create a pull request</a> to acomplish this. Also, the pull request need to be set to:

        main <- release/1

- lastly we need to merge the changes from `release` branch to `develop` branch to make sure that `develop` branch is up to date.

### 6. Hotfixes:
If at any point we need to do quick fixes to our code we should use/create hotfix brach for it. Hotfixes are usually are branched off our main branch
- create a new `hotfix/1` branch using Github UI and click on the `Create branch: hotfix/1 from 'main'`
- now we can add any necessery fixes, then commit staged changes and create pull request:

                main <- hotfix/1

- also do not forget we need to merge the hotfix changed to `develop` branch too.

## GitHub Workflow Steps:
### 1. Have only one long lived branch:
This workflow is used mostly when the code is being change offten. It's simillar to Gitflow, but it has less branches. 
There is only one long live branch `main`, with additional `feature` branch. Each developer pull the changes from shared repository and localy create own `feature` branch to work on it. After they commit the changes they push them to the shared `feature` branch and create pull request. After the pull request is reviewed it's merged to `main` branch.

### 2. Have feature branch:
- we should have only `fetaure` branches. 
- follow the <a href="#3-development-work-on-new-features">STEP 3 - Development work on new features</a> to create & commit any changes
- then do <a href="#4-create-a-pull-request">STEP 4 - Create a pull request</a>
- if we nned to do any hotfixes we just fix any isuees localy on the `feature` branch and push & pull request to shared repository.

