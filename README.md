# Hash-based colored de Bruijn graph with wavelet trie and Bloom filter color compression


Prerequisites
- cmake 3.6.1
- C++14
- HTSlib
- sdsl-lite
- GNU GMP (wavelet trie only)
- libmaus2

Install
1. `git clone --recursive https://github.com/ratschlab/graph_annotation`
2. install **libmaus2** and **sdsl-lite** in `external-libraries/` following the corresponding instructions
3. go to the **build** directory `mkdir -p annograph/build && cd annograph/build`
4. compile by `cmake .. && make && ./unit_tests`

Build types: `cmake .. <arguments>` where arguments are:
- `-DCMAKE_BUILD_TYPE=[Debug|Release|Profile]` -- build modes (Debug by default)
- `-DBUILD_STATIC=ON` -- link statically (OFF by default)

Install wavelet trie compressor
1. `cd wavelet_trie`
2. `make`

Typical workflow
1. Generate graph and uncompressed annotations (`.precise.dbg` and `.rawrows.dbg` files)
`./annograph build -o <OUTPREFIX> <FLAGS> <INPUTS>`
2. Compress annotation with Bloom filters
`./annograph build -i <OUTPREFIXX> -o <BLOOMOUTPREFIX> <FLAGS> <INPUTS>
3. Compress annotation with wavelet tries (see README in wavelet_trie folder)