# Aliases

### Set an Alias

`Usage: ioctl alias set ALIAS ADDRESS`

```
➜  ioctl alias set test io1l3wc0smczyay8xq747e2hw63mzg3ctp6uf8wsg
set
```

### Remove an Alias

`Usage: ioctl alias remove ALIAS`

```
➜  ioctl alias remove frank
frank is removed
```

### List Alias

`Usage: ioctl alias list`

```
➜  ioctl alias list
io1r2r0um9dw35922tptkuphseq43hq2knk3fjrlt - IOsenser
io1l3wc0smczyay8xq747e2hw63mzg3ctp6uf8wsg - test
io14gnqxf9dpkn05g337rl7eyt2nxasphf5m6n0rd - whale
```

### Export Aliases

`Usage: ioctl alias export`

```
➜  ioctl alias export
{"aliases":[{"name":"gas-test","address":"io15kqxz7a0r72akrgy6p7fuu88llg7cxn9rlfjdj"},{"name":"public-length","address":"io15cg78lnv54r8m8vrkrv9ktq4uyngp5aenmj5wa"},{"name":"test","address":"io1v9r84ckmccqczl00r0sdepvaunsk456pcw9rvq"},{"name":"tmp2","address":"io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4"},{"name":"daddypig","address":"io1gh439pm67d4cwxt882xpylj75klys6esepml60"},{"name":"dorothy","address":"io1x0e9jwx7yv7sk2p4lj4vt4czydwtlwkhaaczt7"},{"name":"infinite-loop","address":"io14cu7qpseelx0zg8lm2tl4a927lqmfl7dgr886q"},{"name":"max-time","address":"io1fzyv2tlfh3xkper4xln3phfr0mcklzmgans5p5"},{"name":"tmp","address":"io120au9ra0nffdle04jx2g5gccn6gq8qd4fy03l4"},{"name":"cashier","address":"io1paxfkzr5kpgxjxckfydhttcg3vqtug5ehlrvrx"}]}
```

### Import Aliases

`Usage: ioctl alias import 'DATA'`

```
➜  ioctl alias import '{"name":"max-time","address":"io1fzyv2tlfh3xkper4xln3phfr0mcklzmgans5p5"}'
0/0 aliases imported
Existed aliases:
```

##
