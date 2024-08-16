#### Backup of all the site reference and Markdown. 

# create new post
```shell script
hugo new posts/lambda_function_python.md
```

#### make sure the path is good in git submodule
<!-- url = git@github-mac:shekharkoirala/shekharkoirala.github.io.git -->

#### add new theme 
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1

rm -rf public
git submodule update --init
## update the submodules
git submodule update --init --recursive
git submodule update --remote --merge

## remove cache
git rm --cached public -f

## ./deploy.sh 


#### delete old theme 
rm -rf loveit

