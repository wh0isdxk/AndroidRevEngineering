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

## 4 - Instalando o Certificado

No seu computador, acesse https://burp, clique em CA Certificate e salve o arquivo;

- Renomeie para cacert.cer e envie via e-mail para seu device;
- Já no seu device, faça o download do certificado e siga os seguintes passos:
- My files -> all files -> device storage -> downloads 

(Verifique se o certificado se encontra nessa pasta ou localize o lugar onde ele se encontra)

- Siga os seguintes passos: 
- Settings -> More -> Permissions -> Security -> Install from device storage;
- Instale o Certificado com o nome cacert e em Credencial Use: "VPN and apps";
- Verifique se realmente foi instalado em "Trusted Credencials" (ele deverá estar como PortSwigger CA); 

Estará funcionando corretamente se você estiver apta para visitar qualquer site sem que avisos de segurança apareçam no site na hora do acesso inicial. 


### Ferramentas:  

Para interceptação: 

- Burp Suite 
- MITM Proxy 
- Charles 

Emuladores de Android: 

- Genymotion 
- Bluestacks 
- Nox Player 



> Em caso de dúvidas, entrar em contato. <3 
