# MkDocs

Static site generator used to build the [MyDocs](https://mikedegan.github.io/MyDocs) documentation site.

#### Commit and push your changes first

````
git add .
git commit -m "updated this doc"
git push origin master
````

#### Deploy to GH Pages

You must be in c:\users\jackie\onedrive\development\docs\

not ...docs\docs\

```
mkdocs gh-deploy
```

#### Develop Your Site

```
mkdocs serve
```

Then open [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to see a live preview of your site.

#### Create a New Documentation Project

```mkdocs new my-project
cd my-project
```
