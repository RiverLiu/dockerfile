# postgres

Fork from [oelmekki/postgres-350d](https://github.com/oelmekki/postgres-350d)

Docker build of postgresql-10.7 changing the dimension limit for the cube extension, raising it to 256.

This is needed to be able to work with words embedding with postgres.

You can easily generate a build for your own need in term of dimensions by editing this dockerfile.

# Download

The image dockerhub page is here.

To pull it:

  docker pull riverlcn/postgres:10-cube

# 说明

Postgres 的 cube 扩展，默认支持的最大维度为100维, 可以修改 cube 的源码文件 `cubedata.h`，设置维度的最大长度。该 `Dockerfile` 设置了维度长度为 256，你可以修改该数字，然后重新编译docker 镜像。

> To make it harder for people to break things, there is a limit of 100 on the number of dimensions of cubes. This is set in cubedata.h if you need something bigger.

