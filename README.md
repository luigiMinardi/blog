
# Adding a theme:


> This is already a Hugo repo so no need for the init that you may see in some tutorials
> ```sh 
> hugo mod init github.com/<username>/<repo-name>
> ```

Add theme to imports in the `hugo.toml`:
```toml
[[module.imports]]
    path='github.com/jpanther/congo/v2'
```
Start server:
```sh
hugo server
```
