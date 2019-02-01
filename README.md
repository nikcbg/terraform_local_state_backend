# terraform_local_state_backend

### Purpose of the repository 
- The repository creates local state backend.

#### List of files in the repository

File name                            | File description 
------------------------------------ | --------------------------------------------------------------
`.gitignore` | list of files and directories to ignore.
`main.tf` | Terraform configuration file. 

### How to use this repository. 
- Install `terraform` by following this [instructions](https://www.terraform.io/intro/getting-started/install.html).
- Create GitHub repository and give it name, initialize README.md and add a licence. 
- Clone the repository to your local computer: `git clone git@github.com:nikcbg/terraform_local_state_backend`.
- Go to the cloned repo on your computer: `cd terraform_local_state_backend`.
- Create a new branch in the repo you just cloned by eaxecuting ` git checkout -b newbranch` command.
- Create `main.tf` file by executing `vim man.tf` command and copy/paste the below code in `main.tf` file:

    ```
    resource "null_resource" "helloWorld" {
    provisioner "local-exec" {
        command = "echo hello world"
    }
   }
    ```

- Save and exit the `main.tf` file by executing `:wq!` command.
- Execute `terraform init` to download the necessary plugins.
- Execute `terraform apply` to create the new resources. 
- Next if you execute `git status` you will see that new files were cretaed after you ran `terraform apply`:

    ```
    On branch newbranch
    Untracked files:
    (use "git add <file>..." to include in what will be committed)

	  .terraform/
	  main.tf
	  terraform.tfstate

    nothing added to commit but untracked files present (use "git add" to track)

    ```

- Next you need to create `.gitignore` file and put the `.terraform/` and `terraform.tfstate` files in there. 
- Next if you execute `git status` you will see that `.terraform/` and `terraform.tfstate` files are not displayed anymore:

    ```
    Untracked files:
    (use "git add <file>..." to include in what will be committed)

	  .gitignore
	  main.tf

    nothing added to commit but untracked files present (use "git add" to track)

    ```

- Next you can commite your changes to teh GitHUb repository you created:
  - execute `git add .gitignore main.tf` command to add the files that will be commited.
  - execute `git commint -m "your comment here"` to commite the files to the newbranch, the output should display:
  
  ```
  git commit -m "add file"
  [newbranch a518a82] add file
  2 files changed, 8 insertions(+)
  create mode 100644 .gitignore
  create mode 100644 main.tf
  ```
- Next step is to push all the changes to the GitHub repository:
  - execute `git push origin newbranch` command to push your changes to GitHub, the output should display:
  
  ```
  Counting objects: 4, done.
  Delta compression using up to 8 threads.
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (4/4), 452 bytes | 452.00 KiB/s, done.
  Total 4 (delta 0), reused 0 (delta 0)
  remote: 
  remote: Create a pull request for 'newbranch' on GitHub by visiting:
  remote:      https://github.com/nikcbg/terraform_local_state_backend/pull/new/newbranch
  remote: 
  To github.com:nikcbg/terraform_local_state_backend.git
  * [new branch]      newbranch -> newbranch
  
  ```
- Next go to GitHub and follow the prompts to create and merge the pull request.

