#### Backup of all the site reference and Markdown. 

# create new post
```shell script
hugo new posts/lambda_function_python.md
```

#### make sure the path is good in git submodule
<!-- url = git@github-mac:shekharkoirala/shekharkoirala.github.io.git -->

#### add new theme 
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1

## update the submodules
git submodule update –remote 

#### delete old theme 
rm -rf loveit