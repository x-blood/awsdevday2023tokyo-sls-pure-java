# awsdevday2023tokyo-sls-pure-java

## Result of K6

```
     data_received..................: 1.2 MB 278 kB/s
     data_sent......................: 168 kB 40 kB/s
     http_req_blocked...............: avg=306.5ms  min=245.27ms med=303.61ms max=374.58ms p(90)=355.27ms p(95)=362.3ms 
     http_req_connecting............: avg=14.41ms  min=6.93ms   med=16.15ms  max=24.75ms  p(90)=20.1ms   p(95)=22.27ms 
     http_req_duration..............: avg=2.48s    min=2.27s    med=2.49s    max=2.89s    p(90)=2.58s    p(95)=2.62s   
       { expected_response:true }...: avg=2.48s    min=2.27s    med=2.49s    max=2.89s    p(90)=2.58s    p(95)=2.62s   
     http_req_failed................: 0.00%  ✓ 0         ✗ 200  
     http_req_receiving.............: avg=297.62µs min=7µs      med=25.5µs   max=2ms      p(90)=1.14ms   p(95)=1.25ms  
     http_req_sending...............: avg=60.26µs  min=25µs     med=48.5µs   max=495µs    p(90)=77µs     p(95)=125.29µs
     http_req_tls_handshaking.......: avg=234.83ms min=167.42ms med=232.44ms max=306.58ms p(90)=283.42ms p(95)=290.65ms
     http_req_waiting...............: avg=2.48s    min=2.27s    med=2.49s    max=2.89s    p(90)=2.58s    p(95)=2.62s   
     http_reqs......................: 200    47.625262/s
     iteration_duration.............: avg=3.79s    min=3.59s    med=3.8s     max=4.19s    p(90)=3.9s     p(95)=3.92s   
     iterations.....................: 200    47.625262/s
     vus............................: 4      min=4       max=200
     vus_max........................: 200    min=200     max=200
```

## Result of CloudWatch Logs Insights

```
filter @type="REPORT" and ispresent(@initDuration)
| stats count() as coldStarts, avg(@maxMemoryUsed), avg(@duration + @initDuration) as totalDuration_avg, avg(@duration), avg(@initDuration), min(@initDuration), max(@initDuration) by bin(10m)
```
---
| coldStarts | avg(@maxMemoryUsed) | totalDuration_avg | avg(@duration) | avg(@initDuration) | min(@initDuration) | max(@initDuration) |
|------------|---------------------|-------------------|----------------|--------------------|--------------------|--------------------|
| 200        | 156270000           | 2223.3054         | 617.6657       | 1605.6398          | 1467.81            | 1943.24            |
---
