+++
date = "2017-04-11T17:38:52+05:00"
title = "How I am blogging with Hugo"
+++

In case you didn't notice, this blog and all other parts of this site is made by [Hugo](https://gohugo.io).  If you want to know more, [click here]({{< ref "projects/this-site.md" >}}).

In this article i will describe my posting process.
<!--more-->
## Writing post

It all starts with creating a post. It is very easy achievable by following comand:

    hugo new blog/<article-name>.md

New file contains this: 

    +++
     date = "2017-04-11T17:38:52+05:00"
     title = "<article-name>"  
    +++
    
That stuff inside triple plusses called Front Matter. I don't want to go deeper in this, this all described very well in [docs](https://gohugo.io/content/front-matter/).

Next thing is to humanize title, add taxonomies or categories, if you are using any (*I am not using taxonomies or categories at the moment, but I will think about it and maby categorize my blogposts in future*)

The last thing is to write post itself. Hugo uses markdown (*I am not sure if there are other options, but I am totaly happy with markdown*)

## Deployment

Hugo makes it really easy to update your site. 

Docs provide you with ready-to-use script which will make all the work for you. I am using Github Pages as my hosting, so my deployment script looks like this:

``` deploy.sh:        
    echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"
    
    # Build the project.
    hugo # if using a theme, replace by `hugo -t <yourtheme>`
    
    # Go To Public folder
    cd public
    # Add changes to git.
    git add -A
    
    # Commit changes.
    msg="rebuilding site `date`"
    if [ $# -eq 1 ]
      then msg="$1"
    fi
    git commit -m "$msg"
    
    # Push source and build repos.
    git push origin master
        
    # Come Back
    cd ..
```

Make this file executable and simply run it. I don't even have to type username and password for my Github account, because I am pushing with SHH. That's all!

*Updated:*

I decided to keep both raw and compiled site in one repo. It is much easier to maintain. 

So now deployment is as easy as:

1. Run ```hugo```. This command compiles your site to clear html
2. Commit changes and push them to Github

