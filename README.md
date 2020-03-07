# Android APK Reverse Engineering
### Avengers, Disassemble! 

Neste repositório encontraremos um passo-a-passo de como realizar a Engenharia Reversa de um APK. 

Começando pelo básico, podemos dividir o nosso Android Package (APK) em algumas partes:  

![Untitled Diagram(1)](https://user-images.githubusercontent.com/37185061/76150991-a2224980-608e-11ea-8363-558491f9adda.png)

- AndroidManifest.xml 

Composto por todas as permissões que a aplicação vai ter, é responsável por fazer a definição da arquitetura desse apk. Dentro dele encontramos requisição de acesso a internet, GPS, notificações e qualquer outra coisa que o aplicativo venha a necessitar, são geralmente os acessos que o aplicativo pede na hora da instalação. Além disso, encontramos informações voltadas a versionamento, nome da aplicação, requisitos mínimos para que ela funcione, componentes voltados para Receivers, Senders e Providers e componentes 

Abaixo temos um exemplo do que encontramos nesse xml: 

    uses-permission android:name="android.permission.INTERNET" 

    uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" 
    
    uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" 
    
    uses-permission android:name="android.permission.VIBRATE" 
    
    uses-permission android:name="android.permission.WAKE_LOCK" 
    
    uses-permission android:name="com.android.vending.BILLING" 
    
 Note que, em diversas aplicações, várias requisições de permissões são feitas mesmo que o app em si não necessite de tais funções. 

- META-INF/ 

Essa pasta contém dados relacionados ao Manifest e outros metadatas carregados pelo arquivo .jar.

Dentro dele encontraremos os seguintes arquivos: 

	- MANIFEST.MF: versão do pacote, número da compilação, criador, etc. 
	- CERT.SF: Nesse doc encontramos a lista de todos os arquivos junto com o resumo do SHA-1.
	- CERT.RSA: Aqui temos o conteúdo assinado do arquivo CERT.SF, juntamente com os certificados da chave pública usada para assinatura. 


- classes.dex 

- lib/ 

- assets/ 


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

Tools: 
Apktool 

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


# Dynamic Analysis 



## Tools 

- Mobsf 

Mobile Security Framework (https://github.com/MobSF) é uma ferramenta que automatiza a análise de APKs. 
Dentro dela conseguimos mais detalhes sobre as partes que compoẽm os APKs, e que vimos anteriormente. 

- dex2jar 

- dedexer

- apktool 

- Frida 

- adb (Android Debug Bridge) 

Comandos: //soon


# Static Analysis 

- Mobsf 

# Materiais 

Agora que já temos uma base de como isso funciona, é hora de praticar! 
Deixo aqui, uma lista com alguns labs que você pode usar como exercício: 


Obrigada por chegar até aqui! 

Have a nice day. <3 
