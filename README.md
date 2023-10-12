# VS Code snippets

The [Electric Book Works](https://electricbookworks.com) team uses these snippets in VS Code.

## Setup

To sync this repo with your global snippets (originally taken from [this now deleted post](https://betterprogramming.pub/creating-and-syncing-personal-snippets-in-vs-code-d03a8d441019)):

> On macOS, these files are stored in your User/Library. In Windows, it’s User/AppData. Here are the commands I used to create those symlinks from my usual projects folder over to where VS Code is looking for them. If you already have a snippets folder in your app data folder, the symlink command will fail. You’ll have to delete the snippets folder to be able to create the symlink (just make sure to back up any existing snippets you may have).
>
> ### Mac
>
> ```sh
> ln -s /Users/<USER>/<YOUR REPOS FOLDER>/vs-code-snippets/ /Users/<USER>/Library/Application\ Support/Code/User/snippets
> ```
> 
> ### Windows
>
> ```bat
> mklink /D c:\Users\<USER>\AppData\Roaming\Code\User\snippets c:\<YOUR REPOS FOLDER>\vs-code-snippets
> ```
> 
> Any changes you make to the snippets within either the app data folder or your checkout folder will be instantly updated (actually they are the same file) so you can push/pull your git repo to update your snippets.

As that points out, importantly, the commands above won't work if the VS Code `User\snippets` folder already exists. So you need to delete it first (saving separately any snippets you've created there).

For example, let's say Arthur has cloned this repo to `c:\src\vs-code-snippets`. First, he'll delete his VS Code `User\snippets` folder, and then he'd run this in a Command Prompt on Windows:

```bat
mklink /D c:\Users\Arthur\AppData\Roaming\Code\User\snippets c:\src\vs-code-snippets
```

Now VS Code's `User\snippets` folder actually points to his clone of this repo at `c:\src\vs-code-snippets`. When he updates the repo, his VS Code snippets are updated automatically, because they actually live in that repo.

Keep in mind, though, that this repo on his machine is now the only place he can store global snippets. If he creates any snippets that he does not want to share with others in this repo, he must not commit them in Git.

### Activating snippets in markdown

In VS Code, markdown does not get snippet functionality by default, and you have to turn it on manually by editing your global `settings.json` file. Open `settings.json` and add this setting:

```json
    "[markdown]": {
        "editor.quickSuggestions": {
            "comments": "on",
            "strings": "on",
            "other": "on"
    },
```

You may already have a `"[markdown]"` section, in which case you're only adding `"editor.quickSuggestions": true` there.

### Personal snippets

Files that start with `local` will not be committed to version control. For instance, you can keep your own personal snippets in, say, `local-rockstar.code-snippets` and `local-lisp.code-snippets`, and they won't be shared with others using this repo.

Refer to the VS Code docs for guidance on [creating your own snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_create-your-own-snippets).