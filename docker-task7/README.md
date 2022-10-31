### Task 7. Build automation (Available with Pro, Team and Business Docker Hub subscriptions)

1. Create new repository on GitHub/BitBucket.
2. Push a project with Dockerfile file to this Git repository.
3. Create new account on Docker Hub (or use existing one).
4. Logged into Docker Hub using existing account and go to your Account Settings and then click `Linked Accounts` item
   from left menu. Select your provider (GitHub or BitBucket) and click `Connect`. Select your repository and click
   `Authorize Docker`.
5. Click `Repositories` - > `Create Repository` in the top menu. Enter repository name. Click `Connected` image under
   Build Settings, choose GitHub/BitBucket option and Git repository and then select branch, Dockerfile location and
   Docker tag. Click `Create & Build` button.
6. Open your Hub repository page and go to `Build details` tab. Verify that build is running.
7. When build has completed make a commit to GitHub repository and push it. Verify that new build is running again.
8. You can trigger build of the Docker image without commit if you use open `Build settings` tab and click `Trigger`
   button.
