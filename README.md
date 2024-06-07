# Names and IPs

```
su -
toor
hostnamectl set-hostname HOST1; exec bash
нажать enter
```

**c.	Пул адресов для сети офиса BRANCH - не более 16**  

255.255.255.240 = /28  

**d.	Пул адресов для сети офиса HQ - не более 64**  

255.255.255.192 = /26  

## Настройка адресации  
**Назначаем адресацию согласно ранее заполненной таблицы №1**  

## **CLI**  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/2a47b1bb-fd52-4d8a-9477-d00cc2edecce)  

```
ip -c a
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/c42a6bb6-4742-47fc-8e04-c50d79d34e0b)  

## **ISP**  
```
su -
toor
enter
nmtui
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/6fd69321-b8af-4fac-8af3-ce3d725c3c79)  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/2c688d45-2e2e-465b-b248-3bbdd35085b7)  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/df296352-40b6-4b49-a803-36918ac6073a)  
После установки ip-адресов необходимо переподключить интерфейсы.  

Произведём настройку маршрута для CLI
```
ip route add default via 192.168.0.2
```

Необходимо включить опцию forwarding:  
```
nano /etc/net/sysctl.conf
ctrl-x
y
enter
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/c468da7e-93e8-4ab6-8512-bff6152f293e)  

```
systemctl restart network
ip -c a
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/9c28a552-a15a-4fb8-9b22-339a5cfd0d5d)   

## **HQ-R**  
```
su -
toor
enter
nmtui
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/563fb426-a5ae-43ad-895a-83c6cf563845)
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/d6547cfc-0796-45f1-bae9-aacde55d9628)

```
ctrl-x
y
enter
```
Необходимо включить опцию forwarding:  
```
nano /etc/net/sysctl.conf
ctrl-x
y
enter
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/c468da7e-93e8-4ab6-8512-bff6152f293e)  
```
systemctl restart network
ip -c a
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/9df4565f-7e66-46cd-a0f3-a279beac373f)

## **HQ-SRV**  
В дальнейшем на HQ-SRV подразумевается получение адреса по DHCP от HQ-R.  
Удостоверимся, что на интерфейсе установлено получение адресов через DHCP.
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/7d906ddf-918d-4d48-b246-b1d8bfd5803e)  

## **BR-R**  
```
su -
toor
enter
nmtui
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/ec24eecb-51fe-464c-a8ff-0445fdabb004)  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/13fc4ab3-2428-484a-985d-a267cf38c143)  


Необходимо включить опцию forwarding:  
```
nano /etc/net/sysctl.conf
ctrl-x
y
enter
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/c468da7e-93e8-4ab6-8512-bff6152f293e)  
```
systemctl restart network
ip -c a
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/0f3c5a5c-81c4-4372-8c36-74a4ab16e2eb)  

## **BR-SRV**  
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/ed430966-cfd6-418d-beb6-0379cf3519a9)

```
ip -c a
```
![image](https://github.com/NyashMan/DEMO2024/assets/1348639/12b60453-c385-4020-a655-fde5f906b65a)
