# Some git errors I encountered and resolving it.

I worked on a personal project that required me to clone a repo and I made some changes to the code. When I got to the stage of pushing the code to a new repository I had created, I found these two useful hacks.


## <b>Dealing with a new remote Repo without README.md file.</b> (Without any content)

1. Cloning the repo to local machine:
   
    ```
    Git clone <url>
    ```

2. Edit the repo with VSCode.

3. The project had master as the default branch, so I changed it to main to match my repo.

    ```
    git branch -m master main
    ```

4. Push the code:
   
    ```
    git status

    git add .

    git commit -m " "

    git push -u origin main
    ```
    This gave a permission error. So, I set the new remote origin.

5. Set the new remote origin:
   
    ```
    git remote set-url origin <new-repo-url>
    ```

6. Finally, push the code again:
   
    ```
    git push -u origin main
    ```

## <b>Dealing with a new remote Repo with README.md file.</b> (With contents)

For this step, I did everything from `steps 1 to 5` above. Then,

6. Verify the new origin with:

    ```
    git remote -v
    ```

7. Push Codes:
   
    ```
    git push -u origin main
    ```
     This time, the error goes like this:

    ```
    ! [rejected]        main -> main (fetch first)
    error: failed to push some refs to ...
    hint: Updates were rejected because the remote contains work that you do
    hint: not have locally. This is usually caused by another repository pushing
    hint: to the same ref. You may want to first integrate the remote changes
    hint: (e.g., 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    ```

8. Git pull command:
   
    ```
    git pull origin main --allow-unrelated-histories
    ```
    This enabled me to pull the remote repo with all the conflicts it met on the local repo. With that, I could open a merge conflict editor on VSCode to rectify and merge the conflicts.

9. Commit:

    ```
    git commit -m " "
    ```
    Note: I made a mistake when typing the message body. And to rectify it, I used this command:

    ```
    git commit --amend
    ```
    
10. Finally, pushing the code again:
   
    ```
    git push -u origin main
    ```





