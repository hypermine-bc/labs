# blogs

To showcase our research work in the field of cryptography, blockchain, PKI, security etc.

## Install hugo server

- [Install hugo](https://gohugo.io/getting-started/installing)
- Supported version (latest)

## Setup and run locally

**Clone repo**

```
git clone https://github.com/hypermine-bc/blogs
git update submodule
```

**Adding a new post** 
```
hugo new posts/<CATEGORY>/<POSTNAME>.md
# example: hugo new posts/blockchain/my-new-post.md
```

**Adding images in the post**

- Run `mkdir contents/images/<POST-NAME>` and add all image files into this folder. 
- Once added you can refer them in your blog some thing like this `![alt text](/images/<POST-NAME>/<IMAGENAME>.<FILEEXT>)`

**Starting hugo server**

```
hugo server -D --verbose # run server
```

## Giving Pull request

```
git checkout -b <POST-NAME> ## make sure to create branch name with post name
git add --all
git commit -m <COMMIT MESSAGE> 
git push origin <POST-NAME>
```

Once pushed, go to repository and give pull request. 




