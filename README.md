# repo-repo-repo
R3(config)#crypto isakmp policy 10
R3(config-isakmp)#encryption 3des
R3(config-isakmp)#authentication pre-share
R3(config-isakmp)#hash md5
R3(config-isakmp)#group 2
R3(config-isakmp)#exit
R3(config)#crypto isakmp key Admin address 10.12.15.1 # ip внешнего интерфейса др роутера
R3(config)#crypto ipsec transform-set Admin123 esp-sha-hmac esp-3des
R3(cfg-crypto-trans)#mode transport
R3(cfg-crypto-trans)#exit
R3(config)#crypto ipsec profile SEC_GRE
R3(ipsec-profile)#set transform-set Admin123
R3(ipsec-profile)#ex
R3(config)#int tun0
R3(config-if)#tunnel protection ipsec profile SEC_GRE
должно появиться смс *Apr 18 18:47:02.079: %CRYPTO-6-ISAKMP_ON_OFF: ISAKMP is ON
проверить шифрование можно при помощи
R1(config)#do sh crypto ipsec sa
