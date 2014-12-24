# lein-sass [![Build Status](https://travis-ci.org/101loops/lein-sass.svg)](https://travis-ci.org/101loops/lein-sass)

Leiningen plugin to compile sass and scss files.

[![Clojars Project](http://clojars.org/lein-sass/latest-version.svg)](http://clojars.org/lein-sass)

## Installation

You can install the pluggin by adding lein-sass to your `project.clj` file in the `plugin` section:

```clj
(defproject example "1.2.3"
  :plugins [[lein-sass "0.2.7-SNAPSHOT"]])
```

Run the following command to download the library:

    $ lein deps

## configuration

The configuration for sass and scss is specified under the `:sass` and `:scss` sections of your `project.clj.

Here is an example of `project.clj` with all the possible definitions.

```clj
(defproject example-project "1.2.3"

  :sass {:src "resources/sass"
         :output-directory "resources/public/css"
         ;; Other options (provided are default values)
         ;; :output-extension "css"
         ;; :delete-output-dir true ;; -> when running lein clean it will delete the output directory if it does not contain any file
         ;; :ignore-hooks [:clean :compile :deps] ;; -> if you use the hooks, this option allows you to remove some hooks that you don't want to run
         ;; :gem-version "3.3.0.rc.2"
         }

  :scss {:src "resources/scss"
         :output-directory "resources/public/css"
         ;; Other options (provided are default values)
         ;; :output-extension "css"
         ;; :delete-output-dir true ;; -> when running lein clean it will delete the output directory if it does not contain any file
         ;; :ignore-hooks [:clean :compile :deps] ;; -> if you use the hooks, this option allows you to remove some hooks that you don't want to run
         ;; :gem-version "3.3.0.rc.2"
         }
    )
```

It is good to know that you only need to specify the section you plan to use.  So if you are only interested in scss just specify the `:scss` section.

By default lein-sass will come bundled with sass gem version 3.2.1. However, if you like you can specify another gem version by using the `:gem-version` key for sass or scss subtasks.
lein-sass will download the appropriate gem by using `lein <subtask> deps` or `lein deps` if you have configured the hooks.

## Usage

Tasks available:

* sass: compiles sass files
* scss: compiles scss files

For each task, three subtasks are availbale:

* once: compiles the source files once
* auto: keeps the compiler running and watches for new files and file changes
* clean: cleans the files that were generated by the compiler

## Sass specifics

The load paths are the root of the sass src directory (what was specified in :src) and the root of the output directory (what was specified in :output-directory).

## Hooks

The following hooks are supported by lein-sass for all sass and scss types of file:

    $ lein compile
    $ lein clean

To enable the hooks, add the following lein to your `project.clj` file:

```clj
:hooks [leiningen.sass
        leiningen.scss]
```

## Contribute

Run tests

    $ lein with-profile tests spec

## TODO

* Improve partial support for sass/scss
* allow user to override the gemjars url
* Ensure the newly downloaded gems are on the classpath after download
* cleanup ensure-engine-started
* make project.clj lein2 idiomatic...
* improve ensure-engine-started!
* document separate usage for lein1 and lein2
* add check for lein2 in lein1 version and fail appropriately
* document usage of project
* need to do some kind of perf test
* create some kind of CI to run against different versions of lein
* put colors in the terminal output

## License

Copyright (C) 2013 Renaud Tircher

Distributed under the Eclipse Public License, the same as Clojure.
