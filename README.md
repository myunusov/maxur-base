# Base POM

[![Build Status](https://travis-ci.org/myunusov/maxur-base.svg?branch=master)](https://travis-ci.org/myunusov/maxur-base)

[![Dependency Status](https://www.versioneye.com/user/projects/5626986c36d0ab0016001030/badge.svg?style=flat)](https://www.versioneye.com/user/projects/5626986c36d0ab0016001030)

[![Issue Stats](http://issuestats.com/github/myunusov/maxur-base/badge/pr)](http://issuestats.com/github/myunusov/maxur-base)

[![Issue Stats](http://issuestats.com/github/myunusov/maxur-base/badge/issue)](http://issuestats.com/github/myunusov/maxur-base)

[![DevOps By Rultor.com](http://www.rultor.com/b/myunusov/maxur-base)](http://www.rultor.com/p/myunusov/maxur-base)

## About

Base Maven projects on this artifact and you will get many pre-configuration benefits, 
including up-to-date dependencies, plugins, build extensions, repositories, and more. 

All that you need to do is to define our artifact as a parent of your project:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <parent>
    <groupId>org.maxur</groupId>
    <artifactId>maxur-base</artifactId>
    <version>0.6</version>
  </parent>
  <groupId>your-group-id</groupId>
  <artifactId>your-artifact-id</artifactId>
  <version>1.2.3-SNAPSHOT</version>
  [...]
</project>
```

## Documentation 
http://myunusov.github.io/maxur-base/