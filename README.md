## Illustrate
- This projects aims to implement and utilize basic **data structure and algorithm**
- Thoughts come from the _Web_ and _classical books_

## Note
_Need set env variables before execute binary (Mac need not do this)_

```bash
export LD_LIBRARY_PATH=./lib:$LD_LIBRARY_PATH
```
_or just_

```bash
source env.sh
```

_Header directory [Inc](./inc) use soft link, making each template itself can be used as standalone_

```bash
# example
ll ./inc

common.h@ -> ../common/common.h
kmp.h@ -> ../kmp/kmp.h
md5.h@ -> ../rbtree/md5.h
rbtree.h@ -> ../rbtree/util_rbtree.h
sort.h@ -> ../sort/sort.h
```

_Each template will generate dynamic library, for shared use_

```bash
# example
ldd lib/libsort.so
        linux-vdso.so.1 =>  (0x00007ffdd0929000)
        libcommon.so => ./lib/libcommon.so (0x00002afbcd8e0000)     <= mylib
        libstdc++.so.6 => /lib64/libstdc++.so.6 (0x00002afbcdae3000)
        libm.so.6 => /lib64/libm.so.6 (0x00002afbcddeb000)
        libgcc_s.so.1 => /lib64/libgcc_s.so.1 (0x00002afbce0ed000)
        libc.so.6 => /lib64/libc.so.6 (0x00002afbce303000)
        /lib64/ld-linux-x86-64.so.2 (0x00002afbcd4b2000)
```

## Gallery
### _Quick Start_
> _`kmp` & `sort` need c++11 support_<br>
_`consistent hash` uses `rbtree` which is a standalone source_

```bash
make -j
source env.sh

# then binary was under ./bin
```

### _Concept of Sort_
#### Complexity of Time
| Sort Method | Average | Best | Worst | Stable |
| :--: | :--: | :--: | :--: | :--: |
| bubble | N<sup>2</sup> | O(N) | N<sup>2</sup> | &radic; |
| insert | N<sup>2</sup> | O(N) | N<sup>2</sup> | &radic; |
| bucket | O(N) | O(N) | O(N) | &Chi; |
| radix | O(N) | O(N) | O(N) | &radic; |
| shell | N<sup>1.3</sup> |  |  | &Chi; |
| heap | Nlog<sub>2</sub><sup>N</sup> | Nlog<sub>2</sub><sup>N</sup> | Nlog<sub>2</sub><sup>N</sup> | &Chi; |
| merge | Nlog<sub>2</sub><sup>N</sup> | Nlog<sub>2</sub><sup>N</sup> | Nlog<sub>2</sub><sup>N</sup> | &radic; |
| quick | Nlog<sub>2</sub><sup>N</sup> | Nlog<sub>2</sub><sup>N</sup> | N<sup>2</sup> | &Chi; |

#### _Demonstrate_
![](./gif/sortdemo.gif)

### _Concept of KMP_
#### _next array_
_You may know well about the `next` array from this figure_

![](./gif/next.png)

#### _Demonstrate_
```bash
./bin/kmpdemo
basic kmp:
str = BBCABCDABABCDABCDABDET
pattern = BCDABDE
-1 0 0 0 0 1 0
Index = 14

optimized kmp:
str = BBCABCDABABCDABCDABDET
pattern = BCDABDE
-1 0 0 0 1 1 0
Index = 14
```

## License
The [MIT](./LICENSE.txt) License (MIT)