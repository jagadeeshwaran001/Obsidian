representing your current working directory, the HEAD pointer can be moved to different branches, tags, or commits when using   [[git checkout]]

[[git]] keeps the special pointer to specify the current branch.
![[Pasted image 20240918224340.png]]

if the branch is changes the head is referred to the corresponding branch.

![[Pasted image 20240918224511.png]]

![[Pasted image 20240918224221.png]]

There is a hash key in the `.git/refs/heads/main` we can refer this after every commit.

Whenever a change occurs for a commit, the single hashed ID will update to be the latest commit for that working directory.