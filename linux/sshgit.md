## SSH (Secure Shell):
  is a network protocol used to securely connect to and control remote computers over a network — usually over the internet.

### authorized_keys: 
  Holds the list of public keys that are allowed to connect to user account without a password.

### id_rsa: 
  The public key is derived from this.
### id_rsa.pub:
  Used to verify that a connecting client holds the matching private key.

## SSH Connection Flow (Local_PC → Server_PC)
   1. Generate SSH Key Pair on Local_PC (if not exists)
      $ ssh-keygen -t rsa -b 4096                  // Creates ~/.ssh/id_rsa (private) and ~/.ssh/id_rsa.pub (public) 
   2. Copy Public Key to Server_PC
      $ ssh-copy-id <server_user>@<server_ip>      // Adds Local_PC's public key to Server_PC's ~/.ssh/authorized_keys
   3. Connect to Server_PC
      $ ssh <server_user>@<server_ip>              // Authenticates using the private key (~/.ssh/id_rsa)


### -------------------------- SSH GITHUB ---------------------------
$ ls -al ~/.ssh   // to check ssh list in pc
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"   // to generating ssh command
$ cat ~/.ssh/id_rsa.pub     // To display the content of your SSH public key

$ git remote -v   // to show remote repository location.



$ lsof -i :8001   // to verify specific process run on particuler port
$ kill -9 972846  // to kill process id 972846


# Other ssh key set for other github account
$ ssh-keygen -t rsa -b 4096 -C "other@example.com" -f ~/.ssh/id_rsa_other
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa_another
$ cat ~/.ssh/id_rsa_another.pub

# if not work
$ nano ~/.ssh/config
	# GitHub account 1
	Host github.com-account1
	    HostName github.com
	    User git
	    IdentityFile ~/.ssh/id_rsa
	    IdentitiesOnly yes

	# GitHub account 2
	Host github.com-account2
	    HostName github.com
	    User git
	    IdentityFile ~/.ssh/id_rsa_another
	    IdentitiesOnly yes


# --------------------------- Nohup setting ---------------------------
$ hohup bash runserver.sh &

$ ps aux | grep command_to_run  // Stopping a nohup Process
$ kill PID

$ git clone --single-branch -b <branch_name> <link> .

-------------------------------------Clone---------------------------------
$ git clone <github> --depth 1 -b lesson-26
$ git fetch origin main
$ git checkout -b local-main origin/main



-------------------------------------pull----------------------------------

# pull is a combination of 2 different commands: fetch merge, 
# origin --> remote branch
# HEAD --> Local pc branch

$ git log --oneline          
$ git log origin/master      --> to see remote changes
$ git log origin/master      --> to see difference with local current changes.
$ git merge origin/main      --> to merge with local

$ git branch 
$ git branch -a              --> -a option to see all local and remote branches.
$ git branch -r              --> to see only remote branches. 
$ git checkout <local/remote branch switch>
$ git checkout -b <branch_name>   --> to create and move to new branch.

$ git reset <log_id>         --> to clear all from current <log_id> to <log_id>


$ git revert HEAD --no-edit      --> revert the latest commit using git revert HEAD
$ git revert HEAD~x


$ git commit --amend -m <message>  --> combines changes in the staging environment with the latest commit, and creates a new commit.












$ git config --get pull.rebase    // to check pull rebase status
$ git config --unset pull.rebase    // to unset pull rebase status

$ git config pull.rebase false    // merge the changes both remote and local changes in local machine. it take a commit.
$ git pull

$ git config pull.rebase true     // merge the changes to (origin/main, origin/HEAD) in local machine and currently commit in local machine stashed.
$ git pull

$ git config pull.ff only



$ git cherry-pick <commit_id>    // to move specific commit
$ git cherry-pick --continue
$ git cherry-pick --abort

# but cherry-pick make conflict operation, to extend a specific commit 
$ git checkout -b <new_branch_name> <commit_id>




# -----------------------create a new repository on the command line-----------------------------------

$ echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:Parvez49/test.git
git push -u origin main      

// -u or --set-upstream with git push, you're setting the upstream branch. It's typically used the first time you push a local branch to a remote repository. 

# ------------------------ push an existing repository from the command line -------------------------

$ git remote add origin git@github.com:Parvez49/test.git
git branch -M main
git push -u origin main




















