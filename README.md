Gittle
=========

A simple Node.js wrapper for the Git CLI. The API uses promises. This library is used in [Codebox](https://github.com/FriendCode/codebox).

### Installation

```
npm install gittle
```

### How to use it?

```javascript
var Gittle = require("gittle");
```

#### Global Methods

* Load a repository: ```var repo = new Gittle("./");```
* Clone a repository: ```Gittle.clone("https://github.com/FriendCode/gittle.js.git", "./test")```
* Initialize an empty repository: ```Gittle.init("./test")```

Check out [Authentication](#authentication) about how to configure https/ssh authentication for cloning.

#### Repository:

##### Status

* Get status: ```repo.status()```

##### Identity

* Get identity: ```repo.identity()```, Returns an Actor object
* Set identity: ```repo.identify(actor)```, actor is an object like: ```{name: "", email: ""}```

##### Push/pull

* Pull: ```repo.pull(remote, branch)```
* Push: ```repo.push(remote, branch)```
* Fetch: ```repo.fetch(remote)```

Check out [Authentication](#authentication) about how to configure https/ssh authentication.

##### Commits

* List all commits: ```repo.commits(start, limit, skip)```

##### Tags

* List all tags: ```repo.tags()```

##### Branches

* List all branches: ```repo.branches()```
* Create a branch: ```repo.create_branch(name)```
* Delete a branch: ```repo.delete_branch(name)```

##### Remotes

* List all remotes: ```repo.remotes()```
* Add a remote: ```repo.remore_add(name, url)```
* Delete a remote: ```repo.remote_remove(name)```

##### Authentication

A last argument could be use for authentication on ```Gittle.clone```, ```repo.push```, ```repo.pull```, ```repo.fetch```:
```javascript
{
    // SSH:
    'passphrase': "...",
    'refuseUnknownHost': true, // Default is false
    
    // HTTPS:
    'username': "...",
    'password': "..."
}
```