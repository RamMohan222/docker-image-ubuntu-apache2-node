# How to push our own docker image to Github

1. Github facilitating to push/publish our own docker images to our Github account with some limitations.
2. **Before pushing our image to Github first we need to create a repository**.
3. Here Repository will work as a layer means under single repository we can push more than one docker image.
4. Here the limitation is we can't delete a particular image from our **public** repository directly because of some reasons for more info [click here](https://help.github.com/en/github/managing-packages-with-github-package-registry/configuring-docker-for-use-with-github-package-registry#deleting-a-package), If you want to delete any repository we need to make a request to Github support team they will check if any project not depending on that particular repository then they will delete it.
5. To push/publish our image first we need to tag that image with some particular format.
```sh
# docker tag image:1.0 docker.pkg.github.com/<account-owner or username>/<repo-name>/<image-name>:<version>
$ docker tag myimage:1.0 docker.pkg.github.com/rammohan222/docker-mages/myimage:1.0
```
6. Before push image to Github, we need to login to our Github account. Using **docker** command we can log in to our Github account with username and a personal access token with the `read:packages` and `write:packages` scopes. To get our personal access token [click here](https://github.com/settings/tokens) and generate your personal token, Don't forget to copy your personal token when you are generating it. because you can see it only once while generating it. once if you reload the page you can not see it again. but don't worry we can do login to docker again with a newly generated token. 
7. To login into Github with logger use the following command.
```sh
# docker login docker.pkg.github.com -u username -p generated-personal-access-token
$ docker login docker.pkg.github.com -u rammohan222 -p 9b33ee98229c117a890999474dd711ae0854e0c6
```
8. After login successfully we can push our image to our repository by using the following command.
```sh
# docker push docker.pkg.github.com/<account-owner or username>/<repo-name>/<image-name>:<version>
$ docker push docker.pkg.github.com/rammohan222/docker-mages/myimage:1.0
``` 
after pushing your image can see your images under packages(It will not show anything under your specified repository).
  
9. To pull or install the image into your local system use the following commands.
```sh
# docker pull docker.pkg.github.com/<account-owner or username>/<repo-name>/<image-name>:<version>
$ docker pull docker.pkg.github.com/rammohan222/docker-images/myimage:1.0
```
10. To logout from our account in docker
```js
docker logout docker.pkg.github.com
```
for more info about docker image packaging [click here](https://help.github.com/en/github/managing-packages-with-github-package-registry/configuring-docker-for-use-with-github-package-registry) Github page.
