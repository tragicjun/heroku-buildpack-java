This is a customized buildpack-java built on top of [heroku-buildpack-java](https://github.com/heroku/heroku-buildpack-java). The modifacations are as follows:

- Copy artifacts from jvm-buildpack-common-v8.tar.gz including
    - opt directory
    - version.properties
    - bin/java and bin/util
