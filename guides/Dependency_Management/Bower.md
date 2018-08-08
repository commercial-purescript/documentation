
# How to use Bower for PureScript dependency management

Bower is a simple dependency manager which was originally made to manage dependencies of web sites, like HTML, CSS, and JavaScript. Because Bower is relatively language agnostic, early PureScript users found that it works pretty well for management dependencies of PureScript projects.

## Expected result

A successfully compiling PureScript module which uses PureScript modules maintained by a third-party. The source code of the third-party PureScript modules are not committed with your project's code, but rather are specified in a Bower configuration file and locally installed using the Bower program.

## Guide

### Preparation

``` sh
# In a PureScript project's directory
$ npm install -g bower
```

### Define dependencies

Add the desired PureScript libraries to the `bower.json` Bower configuration file. The easiest way to do this is to use Bower's console interface to add and update entries in the `bower.json` file, as follows.

If you don't specify a version by including it in the dependency name, like "git@github.com:purescript/purescript-prelude.git#v3.1.1", Bower will choose the most recent tag and persist that in the `bower.json` file.

It's also important to note that Bower does not consider which version of the PureScript compiler is being used, which means that it might choose a version of the library which requires a newer version of the PureScript compiler than the one your project is using. Because of this, if your project fails to compile after installing a new dependency, specifying an older release tag when installing it may resolve the issue.

``` sh
$ bower install --save git@github.com:purescript/purescript-prelude.git
$ bower install --save git@github.com:purescript/purescript-effect.git
$ bower install --save git@github.com:purescript/purescript-console.git
$ bower install --save git@github.com:purescript/purescript-newtype.git
$ bower install --save git@github.com:purescript/purescript-control.git
```

### Update dependencies in build process

Then, we can execute this dependency-managing program as a step in our PureScript project's build process.

For example, we can define a Bash script, named "build-ps.sh", which defines our project's build process, implemented as follows.

``` sh
#! /bin/bash
./install_ps-deps.sh
purs compile 'src/**/*.purs' 'bower_components/purescript-*/src/**/*.purs'
```

### Observe result

If everything worked, you should see a series of lines indicating compilation status which includes the third-party PureScript modules, like:

``` sh
Compiling Control.Monad.Eff
Compiling Control.Monad.Eff.Class
Compiling Control.Monad.Eff.Console
...
```
