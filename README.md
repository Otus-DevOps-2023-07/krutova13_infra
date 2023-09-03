# krutova13_infra
krutova13 Infra repository

bastion_IP = 51.250.92.106
someinternalhost_IP = 10.128.0.10

Чтобы подключиться к someinternalhost в одну команду с локального устройства, можно воспользоваться командой: 

	ssh -i ~/.ssh/id_rsa -t -A appuser@51.250.92.106 "ssh 10.128.0.10"
 
Чтобы подключение выполнялось по алиасу someinternalhost, необходимо добавить в файл config ssh параметры:
	
	Host bastion
  	User appuser
  	IdentityFile  ~/.ssh/id_rsa
  	HostName 51.250.92.106

	Host someinternalhost
  	User appuser
  	IdentityFile  ~/.ssh/id_rsa
  	HostName 10.128.0.10

И затем можно подключиться следующим способом: 

	ssh -t -A bastion "ssh someinternalhost"
