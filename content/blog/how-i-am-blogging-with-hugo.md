+++
date = "2017-04-11T17:38:52+05:00"
title = "how i am blogging with hugo"
+++

in case you didn't notice, this blog and all other parts of this site is made by [hugo](https://gohugo.io)

in this article i will describe my posting process.
<!--more-->
## writing post

it all starts with creating a post. it is very easy achievable by following comand:

    hugo new blog/<article-name>.md

new file contains this: 

    +++
     date = "2017-04-11t17:38:52+05:00"
     title = "<article-name>"  
    +++
    
that stuff inside triple plusses called front matter. i don't want to go deeper in this, this all described very well in [docs](https://gohugo.io/content/front-matter/).

next thing is to humanize title, add taxonomies or categories, if you are using any (*i am not using taxonomies or categories at the moment, but i will think about it and maby categorize my blogposts in future*)

the last thing is to write post itself. hugo uses markdown (*i am not sure if there are other options, but i am totaly happy with markdown*)

## deployment

hugo makes it really easy to update your site. 

docs provide you with ready-to-use script which will make all the work for you. i am using github pages as my hosting, so my deployment script looks like this:

``` deploy.sh:        
    echo -e "\033[0;32mdeploying updates to github...\033[0m"
    
    # build the project.
    hugo # if using a theme, replace by `hugo -t <yourtheme>`
    
    # go to public folder
    cd public
    # add changes to git.
    git add -a
    
    # commit changes.
    msg="rebuilding site `date`"
    if [ $# -eq 1 ]
      then msg="$1"
    fi
    git commit -m "$msg"
    
    # push source and build repos.
    git push origin master
        
    # come back
    cd ..
```

make this file executable and simply run it. i don't even have to type username and password for my github account, because i am pushing with shh. that's all!

*updated:*

i decided to keep both raw and compiled site in one repo. it is much easier to maintain. 

so now deployment is as easy as:

1. run ```hugo```. this command compiles your site to clear html
2. commit changes and push them to github

