1.下载源码

```bash
git clone https://github.com/HDFGroup/hdf5.git
```

2.创建编译目录

```bash
cd hdf5 && mkdir build && cd build
```

3.配置

```bash
cmake -DHDF5_ENABLE_PARALLEL=ON ..
```

这里添加了`-DHDF5_ENABLE_PARALLEL=ON`选项，以支持并行。

4.编译

```bash
make -j12
```

5.安装

```bash
make install
```
