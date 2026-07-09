## mqtt常见命令
### 本地
- EMS 订阅
- mosquitto_sub -h localhost -p 8883 -u ems_client -P ems_bl11233! \
  -i ems-01 -t "dispatch/soc/+" -q 1 -v \
  --cafile /Users/jevonsmac/Desktop/project/wwProject/wuqi/scales-power-cloud/ruoyi-modules/sp-base/src/main/resources/moquette-dev-cert.pem
- 算法推送
- mosquitto_pub -h localhost -p 8883 -u algo_client -P algo_bl11233! \
  -i algo-dispatch-01 -t "dispatch/soc/S-001" -q 1 -m '{"test":1}' \
  --cafile /Users/jevonsmac/Desktop/project/wwProject/wuqi/scales-power-cloud/ruoyi-modules/sp-base/src/main/resources/moquette-dev-cert.pem

### 生产
- EMS 订阅
- mosquitto_sub -h 121468spdw747.vicp.fun -p 8883 -u ems_client -P ems_bl11233! \
  -i ems-01 -t "dispatch/soc/+" -q 1 -v \
  --cafile /Users/jevonsmac/Desktop/project/wwProject/wuqi/scales-power-cloud/ruoyi-modules/sp-base/src/main/resources/moquette-prod-cert.pem \
  --tls-version tlsv1.2
- 算法推送
- mosquitto_pub -h 121468spdw747.vicp.fun -p 8883 -u algo_client -P algo_bl11233! \
  -i algo-dispatch-01 -t "dispatch/soc/S-001" -q 1 -m '{"test":1}' \
  --cafile /Users/jevonsmac/Desktop/project/wwProject/wuqi/scales-power-cloud/ruoyi-modules/sp-base/src/main/resources/moquette-prod-cert.pem \
  --tls-version tlsv1.2