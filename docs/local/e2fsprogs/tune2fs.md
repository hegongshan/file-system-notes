tune2fs

* 升级ext2

```bash
tune2fs -O has_journal,extent,uninit_bg <device>
```

对于新创建的文件系统，如果没有重载选项，将使用定义在文件/etc/mke2fs.conf中的默认参数

```bash
$ cat /etc/mke2fs.conf
[defaults]
	base_features = sparse_super,large_file,filetype,resize_inode,dir_index,ext_attr
	default_mntopts = acl,user_xattr
	enable_periodic_fsck = 0
	blocksize = 4096
	inode_size = 256
	inode_ratio = 16384

[fs_types]
	ext3 = {
		features = has_journal
	}
	ext4 = {
		features = has_journal,extent,huge_file,flex_bg,metadata_csum,64bit,dir_nlink,extra_isize
		inode_size = 256
	}
	small = {
		inode_size = 128
		inode_ratio = 4096
	}
	floppy = {
		inode_size = 128
		inode_ratio = 8192
	}
	big = {
		inode_ratio = 32768
	}
	huge = {
		inode_ratio = 65536
	}
	news = {
		inode_ratio = 4096
	}
	largefile = {
		inode_ratio = 1048576
		blocksize = -1
	}
	largefile4 = {
		inode_ratio = 4194304
		blocksize = -1
	}
	hurd = {
	     blocksize = 4096
	     inode_size = 128
	}

[options]
	fname_encoding = utf8
```