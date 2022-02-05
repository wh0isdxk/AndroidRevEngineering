# Conceitos 

### AndroidManifest.xml 

Composto por **todas as permissões** que a aplicação vai ter, é responsável por fazer a definição da arquitetura desse apk. Dentro dele encontramos requisição de acesso a internet, GPS, notificações e qualquer outra coisa que o aplicativo venha a necessitar, são geralmente os acessos que o aplicativo pede na hora da instalação. Além disso, encontramos informações voltadas a versionamento, nome da aplicação, requisitos mínimos para que ela funcione, componentes voltados para Receivers, Senders e Providers e componentes.

Abaixo temos um exemplo do que encontramos nesse xml: 

    uses-permission android:name="android.permission.INTERNET" 

    uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" 
    
    uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" 
    
    uses-permission android:name="android.permission.VIBRATE" 
    
    uses-permission android:name="android.permission.WAKE_LOCK" 
    
    uses-permission android:name="com.android.vending.BILLING" 
    
 Note que, em diversas aplicações, várias requisições de permissões são feitas mesmo que o app em si não necessite de tais funções. 

### META-INF/ 

Essa pasta contém dados relacionados ao Manifest e outros metadatas carregados pelo arquivo .jar.

Dentro dele encontraremos os seguintes arquivos: 

	- MANIFEST.MF: versão do pacote, número da compilação, criador, etc. 
	- CERT.SF: Nesse doc encontramos a lista de todos os arquivos junto com o resumo do SHA-1.
	- CERT.RSA: Aqui temos o conteúdo assinado do arquivo CERT.SF, juntamente com os certificados da chave pública usada para assinatura. 


### classes.dex 

Quando descompilamos o apk, no .dex teremos **todas as classes java que estão presentes no código** do aplicativo. Esses arquivos são os exexutados pelo DVM (Dalvik Virtual Machine)e não inclui os recursos, que são mantidos separadamente na pasta /res. 

Caso você decida modificar esse arquivo, estará alterando o comportamento dos programas; se excluir, ele deixará de ter um código executável. 

### lib/ 

Composto pelas **bibliotecas nativas** da aplicação. 

### assets/ 

Carregam consigo **bibliotecas adicionais** e outros arquivos que possam ser necessários para o App. 

### res/

Diretório com todos os **recursos**, xlms de **atividades, layouts, imagens** e etc. 

### resources.arcs 

Por último temos o arquivo que funciona como um **índice de todos os recursos mencionados**, mapeando essas entradas. 

# 

# Componentes 

### Activities 
Representam partes da aplicação onde há **interação com o usuário**, como formulários, botões, caixas de texto...

### Services
São como as activities, porém **rodam em segundo plano** (background), continuam funcionando mesmo quando o usuário abriu uma outra aplicação. 

Possuem 2 modos: **iniciado** ou **vinculado** a alguma outra aplicação. 

### Content Providers 
Funcionam como uma **base de dados**, um storage que permite com que dados sejam armazenados de uma forma segura. 
Também fornecem uma maneira padrão de recuperar, modificar e excluir dados.  

### Broadcast Receivers 
Permite ao sistema **distribuir eventos**, ou seja, uma parte do código da aplicação é executada quando um determinado evento acontece e, desde que tenha autorização, realiza uma ação, como notificação de SMS, por exemplo. 
