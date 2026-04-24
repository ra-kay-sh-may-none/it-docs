#. Undo last commit (unpushed):
  ##. Undo last commit but KEEP your changes (Staged):
    ###. git reset --soft HEAD~1
  ##. Undo last commit and UNSTAGE your changes:
    ###. git reset HEAD~1
  ##. Undo last commit and DELETE all changes (Destroy work):
    ###. git reset --hard HEAD~1
#. Undo last commit (pushed):
  ##. Multistep below:
    ###.
      git revert HEAD
      git push origin <your-branch-name>
    ###.
#. Setup and use multiple identies for different repo's on Windows OS.
  ##. Assumpsions:
    ###. repo_a uses identity_a as owner
    ###. repo_v uses identity_b as contributor
  ##. Privacy:
    ###. email id can be github no-reply email id
  ##. Steps:
    ###. Generate SSH keys for both identity
      ####.
        ssh-keygen -t ed25519 -C "your-owner-email@example.com" -f "%USERPROFILE%\.ssh\id_rsa_repo_a"
        ssh-keygen -t ed25519 -C "your-contributor-email@example.com" -f "%USERPROFILE%\.ssh\id_rsa_repo_b"
      ####.
    ###. Add Keys to GitHub
      ####. Copy the content of the public key (e.g., type %USERPROFILE%\.ssh\id_rsa_repo_a.pub).
      ####. Go to GitHub Settings > SSH and GPG keys > New SSH Key and paste it.
      ####. Repeat for the second account with the second public key
    ###. Create an SSH Config File
      ####. Create a text file at C:\Users\<YourUser>\.ssh\config (no file extension) and paste this:
        #####.
          # Account A (Owner)
          Host github.com-repo-a
              HostName github.com
              User git
              IdentityFile ~/.ssh/id_rsa_repo_a
          
          # Account B (Contributor)
          Host github.com-repo-b
              HostName github.com
              User git
              IdentityFile ~/.ssh/id_rsa_repo_b
        #####.
      ####. The identity file is the private key filename and hence no pub file extension
    ###. Update Your Local Repos
      ####.
        git remote set-url origin git@github.com-repo-a:YourUsername/repo-a.git
        git remote set-url origin git@github.com-repo-b:OwnerUsername/repo-b.git
      ####.
    ###. Now "git push" would ask for keyphrase and would push to the remote
