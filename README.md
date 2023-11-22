# Laravel Perf Test

## Usage

Into test server
```
docker exec -it laravel-pt-test-server-1 sh
```
In the server
```
wrk -t4 -c50 -d30s http://phpfpm.test
wrk -t4 -c50 -d30s http://swoole.test
```

## Test Result

### Result

```
/ # wrk -t4 -c50 -d30s http://phpfpm.test
Running 30s test @ http://phpfpm.test
  4 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   141.48ms   35.53ms 463.50ms   76.18%
    Req/Sec    85.17     23.88   141.00     55.97%
  10194 requests in 30.06s, 182.28MB read
Requests/sec:    339.08
Transfer/sec:      6.06MB
/ # wrk -t4 -c50 -d30s http://swoole.test
Running 30s test @ http://swoole.test
  4 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   213.60ms  381.43ms   2.00s    85.92%
    Req/Sec   190.48    116.73   595.00     68.55%
  21901 requests in 30.05s, 390.01MB read
  Socket errors: connect 0, read 0, write 0, timeout 111
Requests/sec:    728.72
Transfer/sec:     12.98MB
```

### Platform

```
System:    Kernel: 5.15.0-67-generic x86_64 bits: 64 compiler: N/A Desktop: Cinnamon 5.0.7 
           wm: muffin dm: LightDM Distro: Linux Mint 20.2 Uma base: Ubuntu 20.04 focal 
Machine:   Type: Laptop System: LENOVO product: 20L8S98200 v: ThinkPad T480s serial: 
           Chassis: type: 10 serial: 
           Mobo: LENOVO model: 20L8S98200 v: SDK0J40697 WIN serial: UEFI: LENOVO 
           v: N22ET70W (1.47 ) date: 08/11/2021 
CPU:       Topology: Quad Core model: Intel Core i5-8250U bits: 64 type: MT MCP arch: Kaby Lake 
           rev: A L2 cache: 6144 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 28800 
           Speed: 3400 MHz min/max: 400/3400 MHz Core speeds (MHz): 1: 3400 2: 3400 3: 3400 
           4: 3400 5: 3314 6: 3397 7: 3373 8: 3400 
```

