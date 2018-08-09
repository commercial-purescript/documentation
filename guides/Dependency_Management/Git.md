
# How to use Git to implement a custom dependency-management program for PureScript dependency management

Git is a source code management tool which provides history, branching, diffing, and local & remote copy management. It's also possible to use Git as part of a dependency management tool.

## Expected result

A successfully compiling PureScript module which uses PureScript modules maintained by a third-party. The source code of the third-party PureScript modules are not committed with your project's code, but rather are downloaded as a step in your project's build process.

## Guide

You'll find the PureScript library code repositories yourself, find the release tag you want, and clone them into a directory in your PureScript project. Note that you'll need to also manually install the dependencies of your directly desired libraries, called transitive dependencies. Then, pass the paths of all these PureScript repositories to the compiler when building your project.

### Preparation

``` sh
# In a PureScript project's directory
$ mkdir ps-deps/
```

You will need to choose the projects to depend on, find the source code repositories, and choose the version names. Choosing a version which is compatible with the versions of all other third-party projects your project depends on can become difficult. In addition, you'll need to include the dependencies of your desired dependencies, and their dependencies, called "transitive dependencies".

### Define dependency-updating program and declare dependencies

After deciding on the dependencies, add them to a program in your project which uses Git to fetch them.

For example, we can create a Bash script, named "install-ps-deps.sh", implemented as follows.

``` sh
#! /bin/sh

# Define a function which makes idempotent the dependency-fetching operation:
# - clone if the dependency hasn't been cloned yet
# - update to the declared version if the dependency *has* already been cloned
clone_or_update () {
    local VER=$1
    local REPO_URL=$2
    local DEST_DIR=$3
    if [ -d "$DEST_DIR" ]; then
        cd "$DEST_DIR"
        git reset --hard
        git fetch
        git checkout "$VER"
    else
        git clone --branch "$VER" "$REPO_URL" "$DEST_DIR"
    fi 
}

# Declare and update the desired dependencies.
cd ps-deps
clone_or_update v3.1.1 git@github.com:purescript/purescript-prelude.git purescript-prelude/
clone_or_update v3.2.0 git@github.com:purescript/purescript-eff.git purescript-eff/
clone_or_update v3.3.0 git@github.com:purescript/purescript-monoid.git purescript-monoid/
clone_or_update v3.3.1 git@github.com:purescript/purescript-control.git purescript-control/
clone_or_update v3.0.0 git@github.com:purescript/purescript-invariant.git purescript-invariant/
clone_or_update v2.0.0 git@github.com:purescript/purescript-newtype.git purescript-newtype/
clone_or_update v3.0.0 git@github.com:purescript/purescript-console.git purescript-console/
```

### Update dependencies in build process

Then, we can execute this dependency-managing program as a step in our PureScript project's build process.

For example, we can define a Bash script, named "build-ps.sh", which defines our project's build process, implemented as follows.

``` sh
#! /bin/bash
./install_ps-deps.sh
purs compile 'src/**/*.purs' 'ps-deps/*/src/**/*.purs'
```

### Observe result

If everything worked, you should see a series of lines indicating compilation status which includes the third-party PureScript modules, like:

``` sh
Compiling Control.Monad.Eff
Compiling Control.Monad.Eff.Class
Compiling Control.Monad.Eff.Console
...
```
