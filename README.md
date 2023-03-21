# Instalação do Oracle-19c no Centos 7


### Atualização do SO
  
`#sudo yum update`  
  
  
### Criação dos usuários do Oracle
  
`# groupadd oinstall`  
`# groupadd dba`  
`# useradd -g oinstall -G dba oracle`  
`# passwd oracle`  

![image](https://user-images.githubusercontent.com/25879162/226445787-8f5bb069-743b-4e42-8cd0-4f97f42584e6.png)


### Disable firewall linux

`# vim /etc/selinux/config`  
`selinux disabled`  

![image](https://user-images.githubusercontent.com/25879162/226443938-31c867ce-32b1-40ca-ad02-8d4fa5f69f8e.png)

![image](https://user-images.githubusercontent.com/25879162/226445506-64e5feac-0d97-49ec-9568-b8e86f12170e.png)

```# systemctl stop firewalld```  
```# systemctl disable firewalld```  

![image](https://user-images.githubusercontent.com/25879162/226444159-f1a6d03c-253f-4114-b57a-ef58af842166.png)

### Criação das pastas de instalação do Oracle

`mkdir -p /u01/app/oracle/product/19.0.0/dbhome_1`  
`mkdir -p /u02/oradata` 
`mkdir -p /home/oracle/database`

### Permições para os usuários acessarem as pastas

`chown -R oracle:oinstall /u01 /u02 /home/oracle/database`  
`chmod -R 755 /u01 /u02 /home/oracle/database`  

![image](https://user-images.githubusercontent.com/25879162/226446577-88b2cc9d-0d00-4461-a8f4-0d8a94e9acfe.png)  

### Instalação do pacote de pré-instalação do Oracle

`# curl -o oracle-database-preinstall-18c-1.0-1.el7.x86_64.rpm https://yum.oracle.com/repo/OracleLinux/OL7/latest/x86_64/getPackage/oracle-database-preinstall-18c-1.0-1.el7.x86_64.rpm`   
`# yum -y localinstall oracle-database-preinstall-18c-1.0-1.el7.x86_64.rpm` 

### Instalação do Oracle

Faça o download do Oracle 19c for linux X86-64 no site da oracle e envie o arquivo para o servidor utilizando por exemplo o filezilla:

Site da oracle:
https://www.oracle.com/database/technologies/oracle-database-software-downloads.html

### Acesso com user oracle com -X para export da parte grafica

![image](https://user-images.githubusercontent.com/25879162/226442223-2e0dbca7-dfa6-485a-b3ac-973942df2fb4.png)  
 
### Faça a descompactação do arquivo para a pasta de intalação:

`$ cd /u01/app/oracle/product/10.0.0/dbhome_1/`  
`$ unzip -oq /home/oracle/LINUX.X64_193000_db_home.zip` 

![image](https://user-images.githubusercontent.com/25879162/226462655-d5a14805-db99-4f89-aca2-8c929bfb8c0b.png)

### Inicio da instalação

`./runInstaller` 

![image](https://user-images.githubusercontent.com/25879162/226463907-052b1f3d-c4df-45ae-bbc6-b5675a3db3e7.png)

Clique na primeira opção conforme selecionado na imagem  
  
  

![image](https://user-images.githubusercontent.com/25879162/226464261-684d1344-edcf-42b4-8800-a10406c9ec6f.png)

- Se for um ambiente de teste selecione a primeira opção "Desktop Class"  
- Caso seja um ambiente produtivo selecione a segunda opção "Server Class"  
  
![image](https://user-images.githubusercontent.com/25879162/226466875-5423efa3-cbda-441a-91ec-dcc554a01cf2.png)
insira os dados conforme as pastas criadas nos passos anteriores, apontando o "u02/oradata" conforme a imagem acima.

![image](https://user-images.githubusercontent.com/25879162/226467232-ed7b6484-5388-43a0-9f56-30ad8c75024f.png)
Clique em next.

![image](https://user-images.githubusercontent.com/25879162/226467485-005ade80-3f52-4a12-8c51-08b3f4ff1f1f.png)
Insira a senha de root do servidor para que no processo de instalação todas as etapas que necessitem de privilegio seja feita e não venha a ter nenhum problema posterior.

![image](https://user-images.githubusercontent.com/25879162/226467949-7df51575-60a5-4653-9e54-54a6bf9e3419.png)
Ao efetuar a checagem dos pré-requisitos ele reclamou de um pacote e da área de swap, iremos instalar o pacote que faltou:

![image](https://user-images.githubusercontent.com/25879162/226468695-ae597cb8-6a9e-44ec-849e-b5df1ab03456.png)


![image](https://user-images.githubusercontent.com/25879162/226469028-e024790b-1cc1-467c-96f6-5d90347718f7.png)

Após instalar o pacote clique em "Check Again" e para o swap clique em "Ignore All" e clique em "next"

![image](https://user-images.githubusercontent.com/25879162/226469422-7f8169c0-c105-4c2f-a55f-78107e98715b.png)

Faça a checagem a após isso clique em install

![image](https://user-images.githubusercontent.com/25879162/226469556-3f0fe5d8-c5c3-4556-88f8-99ea5dfe01e4.png)

O passo de instalação vai demorar alguns minutos, quando aparecer a janela perguntando
