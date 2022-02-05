# Android APK Reverse Engineering
### Avengers, Disassemble! 


<p align="center">

<img src="https://cdn2.iconfinder.com/data/icons/black-file-type/512/file__apk__android_-512.png" width=300 height=300>


</p>


Neste repositório encontraremos um passo-a-passo de como realizar a Engenharia Reversa de um APK. 

Engenharia Reversa pode nos ajudar em vários aspectos, como **identificar software ou código malicioso**, descobrir **falhas de segurança**, encontrar **funcionalidades que não eram esperadas**/quebras de regra de negócio... 
Dito isso, vamos entrar mais a fundo sobre o universo Android. 

Começando pelo básico, podemos dividir o nosso Android Package (APK) em algumas partes:  

![Untitled Diagram(1)](https://user-images.githubusercontent.com/37185061/76150991-a2224980-608e-11ea-8363-558491f9adda.png)

- [AndroidManifest.xml](https://github.com/wh0isdxk/AndroidRevEngineering/new/master#androidmanifestxml)
- [META-INF/](https://github.com/wh0isdxk/AndroidRevEngineering/new/master#meta-inf)
- [classes.dex](https://github.com/wh0isdxk/AndroidRevEngineering/new/master#classesdex)
- [lib/](https://github.com/wh0isdxk/AndroidRevEngineering/new/master#lib)
- [assets/](https://github.com/wh0isdxk/AndroidRevEngineering/new/master#assets)
- [res/](https://github.com/wh0isdxk/AndroidRevEngineering/new/master#res)
- [resources.arcs](https://github.com/wh0isdxk/AndroidRevEngineering/new/master#resourcesarcs)


### Smali/Baksmali 

O Smali é a versão human readable do Dalvik bytecode, simplificando, funciona como um assemble/disassemble. Dalvik Executable format (.dex)


A termos de código, vamos dar uma olhada na diferença entre Java e Smali:  

    public static void printHelloWorld() {
	System.out.println("Hello World")
    }
    
  E o nosso mesmo código em Smali: 
  
    .method public static printHelloWorld()V
	.registers 2
	sget-object v0, Ljava/lang/System;->out:Ljava/io/PrintStream;
	const-string v1, "Hello World"
	invoke-virtual {v0,v1}, Ljava/io/PrintStream;->println(Ljava/lang/String;)V
	return-void
    .end method
    
    
## Componentes da Aplicação 

- [Activities](https://github.com/wh0isdxk/AndroidRevEngineering/blob/master/Conceitos.md#activities)
- [Services](https://github.com/wh0isdxk/AndroidRevEngineering/blob/master/Conceitos.md#services)
- [Content Providers](https://github.com/wh0isdxk/AndroidRevEngineering/blob/master/Conceitos.md#content-providers)
- [Broadcast Receivers](https://github.com/wh0isdxk/AndroidRevEngineering/blob/master/Conceitos.md#broadcast-receivers)

### Avengers, disassemble! 

Passamos pelos conceitos básicos necessários e agora mãos a obra! 

Passo 1: 

Escolha o APK que você deseja fazer o Reversing. 

Se você não encontrá-lo facilmente pela própria loja de aplicativos, pode fazer diretamente em sites como APKCombo ou APKMonk. 

Chegando aqui, atente-se para algumas coisas que podem ser interessantes: 

	- Qual é o URL da API?  (geralmente emos algo como api.domain.com)
   	- Qual é método de autenticação utilizado? Eu preciso criar um login para acessar? 
  	- Quais são as chamadas que eu posso encontrar e quais são os parâmetros eles esperam?
 
 Uma vez que temos o APK, é hora de fazer a descompilação do mesmo, para que possamos realizar a análise do código. 
 
 (Ferramentas de Análise Dinâmica como o MOBSF permitem que você já consiga realizar o download do código diretamente, sendo ele em Java ou SMALI). 

Agora vamos usar ferramentas, a primeira delas é o APKTOOL, você verá mais detalhes sobre ela abaixo, mas de uma forma geral ela vai ser responsável por descompiilar os arquivos, criando uma pasta, no mesmo lugar, com todos os arquivos descomplilados. A partir daqui, você conseguirá analisar todos os códigos necessarios. 

O comando utilizado aqui vai ser o seguinte: 

	- apktool d ~/Desktop/aplicativo_app.apk
	
Extraindo o arquivo “classes.dex” do APK.

Use a ferramenta dex2jar para converter em arquivos de classe Java. Resultando em um arquivo jar.

	- sh d2j-dex2jar.sh classes.dex
	
Use o JD-GUI para extrair o código-fonte do arquivo jar.

	- Arraste o arquivo classes-dex2jar.jar pro JD-GUI


# Dynamic Analysis 



## Tools 

#### Builders 

- Android Studio 

#### Breakers 

- Frida 
- Burp Suite 
- dex2jar 
- droxer 
- apktool 
- adb

#### Static Analysis 

- [MobSF](https://github.com/MobSF)

#### Dynamic Analysis 

- Mobsf 

Mobile Security Framework é uma ferramenta que automatiza a análise de APKs. 
Dentro dela conseguimos mais detalhes sobre as partes que compoẽm os APKs, e que vimos anteriormente. 

- dex2jar 

- dedexer

- apktool 

O apktool é uma ferramenta Java opensource para engenharia reversa de aplicações Android.
Ele pode decodificar arquivos APK para o seu código original em um XML legível por humanos. Também dividindo todas as classes
e métodos contidos no arquivo em Smali. Dessa forma, você é capaz de modificar recursos ou as execuções do programa. Utilizando o código Smali, você pode adicionar novas funcionalidades dentro dessa aplicação ou alterar o comportamento esperado. 

- Frida 

Usado comumente para SSL Pinning. 

- adb (Android Debug Bridge) 

- androguard 

- Xposed Framework 

Comandos: //soon


### Bypass Root Detection and SSL Pinning 

- Android SSL Bypass 

- Frida 

# Materiais 

Agora que já temos uma base de como isso funciona, é hora de praticar! 
Deixo aqui, uma lista com alguns labs que você pode usar como exercício: 

* [Damn Vulnerable Hybrid Mobile Application](https://github.com/logicalhacking/DVHMA)
* [Android Digital Bank](https://github.com/CyberScions/Digitalbank)
* [Damn Insecure and Vulnerable App](https://github.com/payatu/diva-android)
* [Hackme Bank](http://www.mcafee.com/us/downloads/free-tools/hacme-bank-android.aspx)
* [Insecure Bank](https://github.com/dineshshetty/Android-InsecureBankv2)
* [Damn Vulnerable Android Application](https://code.google.com/archive/p/dvaa/)
* [OWASP GoatDroid](https://github.com/jackMannino/OWASP-GoatDroid-Project)
* [Dodo Vulnerable Bank](https://github.com/CSPF-Founder/DodoVulnerableBank)
* [Vulnerable Android Application](https://github.com/dan7800/VulnerableAndroidAppOracle)
* [Vulnerable Android Application - Urdu](http://urdusecurity.blogspot.co.uk/2014/08/Exploiting-debuggable-android-apps.html)
* [MoshZuk](https://dl.dropboxusercontent.com/u/37776965/Work/MoshZuk.apk)
* [AppKnox Vulnerable Application](https://github.com/appknox/vulnerable-application)
* [Vulnerable Android Application](https://github.com/Lance0312/VulnApp)
* [Security Compass Android Application](https://github.com/SecurityCompass/AndroidLabs)
* [SecurityShepherd](https://github.com/OWASP/SecurityShepherd)
* [owasp-mstg](https://github.com/OWASP/owasp-mstg/tree/master/Crackmes)
* [VulnerableAndroidAppOracle](https://github.com/dan7800/VulnerableAndroidAppOracle)
* [Android InsecureBankv2](https://github.com/dineshshetty/Android-InsecureBankv2)
* [Purposefully Insecure and Vulnerable Android Application (PIIVA)](https://github.com/htbridge/pivaa)
* [Sieve app](https://github.com/mwrlabs/drozer/releases/download/2.3.4/sieve.apk)

### Recomendações 

Teste os seguintes tipos de ataque: 

* Broken crypto
* Insecure data storage
* Poor authentication
* Untrusted input
* Reverse engineering
* Weak server-side controls
* Client side injection
* Content provider leakage
* Unintended Data Leakage
* Usage of weak Initialization Vector
* Man-In-The-Middle Attack
* Remote URL load in WebView
* Object deserialization
* SQL injection
* Missing tapjacking protection
* Enabled Application Backup
* Enabled Debug Mode
* Weak encryptionvHardcoded encryption keys
* Dynamic load of codevCreation of world readable or writable files
* Usage of unencrypted HTTP protocol
* Weak hashing algorithms
* Predictable Random Number Generator
* Exported Content Providers with insufficient protection
* Exported Broadcast Receivers
* Exported ServicesvJS enabled in a WebView
* Deprecated setPluginState in WebView
* Hardcoded data
* Untrusted CA acceptance
* Usage of banned API functions
* Self-signed CA enabled in WebView
* Path Traversal
* Cleartext SQLite database
* Temporary file creation


# Books 

- [Android Hacker's Handbook](https://www.amazon.com.br/Android-Hackers-Handbook-Joshua-Drake/dp/111860864X/ref=sr_1_1?keywords=android+hackers+handbook&qid=1644028298&sprefix=android+hacker%2Caps%2C189&sr=8-1&ufe=app_do%3Aamzn1.fos.25548f35-0de7-44b3-b28e-0f56f3f96147)
- [The Mobile Application Hacker’s Handbook](https://www.amazon.com.br/Mobile-Application-Hacker%E2%80%B2s-Handbook/dp/1118958500/ref=sr_1_2?keywords=android+hackers+handbook&qid=1644028298&sprefix=android+hacker%2Caps%2C189&sr=8-2&ufe=app_do%3Aamzn1.fos.25548f35-0de7-44b3-b28e-0f56f3f96147)
- [Android Security Internals](https://www.amazon.com.br/Android-Security-Internals-Depth-Architecture/dp/1593275811/ref=sr_1_4?keywords=android+hackers+handbook&qid=1644028298&sprefix=android+hacker%2Caps%2C189&sr=8-4&ufe=app_do%3Aamzn1.fos.e05b01e0-91a7-477e-a514-15a32325a6d6)
- [Android Security Cookbook](https://www.amazon.com.br/Android-Security-Cookbook-Keith-Makan/dp/1782167161/ref=sr_1_1?keywords=android+security&qid=1644028398&s=books&sprefix=android+sec%2Cstripbooks%2C190&sr=1-1&ufe=app_do%3Aamzn1.fos.25548f35-0de7-44b3-b28e-0f56f3f96147)
- [Android Security Attacks and Defenses](https://www.amazon.com.br/Android-Security-Defenses-Anmol-Misra/dp/1439896461/ref=sr_1_4?keywords=android+security&qid=1644028398&s=books&sprefix=android+sec%2Cstripbooks%2C190&sr=1-4&ufe=app_do%3Aamzn1.fos.6121c6c4-c969-43ae-92f7-cc248fc6181d)


### Links Interessantes

- [Interceptando o Tráfego das Requisições em Android](https://github.com/wh0isdxk/AndroidRE/blob/master/Interceptacao.md)
- [Bypassing SSL Pinning](https://github.com/wh0isdxk/AndroidRevEngineering/blob/master/SSLPinning.md)

#
*Obrigada por chegar até aqui! 
Have a nice day. <3*

