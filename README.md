# Welcome to ligato-site2

Contains the code for a new hugo-based Ligato.io website. This is used for development/testing purposes. Once completed it will be deployed
using Netlify to replace the existing Ligato.io site.

## Instructions to Clone/Run

### Step 1 - Install Hugo

Follow the instruction located [here](https://gohugo.io/getting-started/quick-start/).

Don't worry about the theme in the quickstart guide. Initially we are using `https://github.com/JugglerX/hugo-hero-theme`


### Step 2 - Clone this site

The hero theme is treated as submodule. This is required for when it is deployed using Netlify.

Be sure to use this command specifically:
```
git clone --recurse-submodules git@github.com:chrismetz09/ligato-site2.git
```


### Step 3 - Run it locally

```
cd ligato-site2
hugo server -D
```
Go to localhost:1313 on your favorite browser and check it out.

This uses live reload so any changes will be instantaneous.



