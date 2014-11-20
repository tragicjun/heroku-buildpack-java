This is a customized buildpack-java built on top of [heroku-buildpack-java](https://github.com/heroku/heroku-buildpack-java). The modifacations are as follows:

- Copy artifacts from http://lang-jvm.s3.amazonaws.com/jvm-buildpack-common-v8.tar.gz including
    - opt directory
    - version.properties
    - bin/java and bin/util

- Modify bin/common to use environment variable ${HTTP_SERVER_URL} to allow custom server serving both maven and jdk tarballs.

- Modify bin/compile to directly use bin/java and bin/util instead of downloading jvm-buildpack-common-v8.tar.gz


To use this buildpack, type below sample command:

    cat yourcode.tar | docker run -i -v /tmp/buildpacks:/tmp/buildpacks -e HTTP_SERVER_URL=http://192.168.59.103:8080 -a stdin -a stdout flynn/slugbuilder
    
**Note**:
- Copy this buildpack base directory to "/tmp/buildpacks" in the host
- Start a HTTP server listening 192.168.59.103:8080 to serve maven and jdk binaries, such as "maven-3.2.1.tar.gz" and "jdk/openjdk1.6.0_27.tar.gz"
