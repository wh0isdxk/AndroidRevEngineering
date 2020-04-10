#  Interceptando o Tráfego das Requisições em Android 

## 1 - Verificando as Configurações de Rede 

Verifique o IP do computador, que será utilizado como proxy. 

> ifconfig   
> ip addr  

## 2 - Configurando o Burp Suite 

Nessa segunda etapa faremos a configuração do Burp Suite para que ele possa ouvir as requisições. 

- Vá até "Burp Proxy Listener" e selecione a aba "Proxy"; 
- Em seguida, vá até Opções e em "Proxy Listener" clique em add. 
- Binding tab -> 
- Bind to port: 8082 
- selecionar a opção ALL INTERFACES 
- Salvar as configurações em "Ok". 

## 3 - Configurando o Proxy (Android)

- Na aba de configurações do seu dispositivo, entre na opção de Wifi; 
- Selecione a rede desejada e estabeleca a conexão; 
- Dentro do sistema, vá até "Modify Network Config" e então "Show Advanced Options";
- Altere em "Proxy Setting" para a configuração MANUAL e então preencha o campo de Proxy Hostname com o ip obtido na nossa primeira etapa, e Proxy Port como 8082;
- Salve essas modificações. 

Para checar o funcionamento, vá em Proxy Intercept, dentro do Burp Suite, e verifique se essa opção se encontra ON. 

Volte ao navegador do seu dispositvo móvel, entre em um site qualquer e veja se as requisições estão sendo ouvidas pelo Burp. 

Se sim, ele estará funcionando. 

## 4 - Interceptação de Tráfego 


### Ferramentas:  

- Burp Suite 
- MITM Proxy 
- Charles 
