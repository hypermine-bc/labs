# Hypermine Labs

Hypermine labs is part of [Hypermine organization](https://www.hypermine.in/) whose purpose is to bring researchers, students and techies who love deep diving into latest technologies and innovations, on one platform and hence building a community of like minded people. The idea (but not strict) is to read research papers and convert them into simple readable blogs so that people can understand easily and quickly. At present, our prime focus are in the field of cryptography, blockchain, PKI, security, SSI, DID etc. 

## How can I contribute?

### Install hugo server

- [Install hugo](https://gohugo.io/getting-started/installing)
- Supported version (latest)

### Setup and run locally

**Clone repo**

```
git clone https://github.com/hypermine-bc/labs
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



### Adding author

- Create a directory : `mkdir content/author/<YOUR_NAME_ALIAS>`
    - If your name consist of two words, make folder name `word1-word2` format
- Create a file called `_index.md` inside that directory
- Modify the following template and paste into `_index.md` file.
- Also add your avatar in the same folder
- You can add `title`: `<YOUR_NAME_ALIAS>` and `AvatarUrl`: `/authors/<YOUR_NAME_ALIAS>/<YOUR_NAME_ALIAS>.png"` fields.

```
---
title: <Author name>
---

<Description>

```

- Once added the Author, you can use the author in the `description` section of your post in this way:

```
---
..
...
authors:
  - author1
  - author2
...
..
---
```

### Adding tag and category

You can add `categories` and `tags` in your post for better visibility and access. You have to add the following in the description of your post.

```
---
..
...
categories: ["category1", "category2"]
tags: [tag1, tag2, tag3]
...
..
---
```
