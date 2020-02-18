# Android APK Reverse Engineering
### Avengers, Disassemble! 

Neste repositório encontraremos um passo-a-passo de como realizar a Engenharia Reversa de um APK. 

Começando pelo básico, podemos dividir o nosso Android Package (APK) em algumas partes:  
- AndroidManifest.xml 

Composto por todas as permissões que a aplicação vai ter, é responsável por fazer a definição da arquitetura desse apk. Dentro dele encontramos requisição de acesso a internet, GPS, notificações e qualquer outra coisa que o aplicativo venha a necessitar, são geralmente os acessos que o aplicativo pede na hora da instalação. Além disso, encontramos informações voltadas a versionamento, nome da aplicação, requisitos mínimos para que ela funcione, componentes voltados para Receivers, Senders e Providers e componentes 

Abaixo temos um exemplo do que encontramos nesse xml: 

    uses-permission android:name="android.permission.INTERNET" 

    uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" 
    
    uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" 
    
    uses-permission android:name="android.permission.VIBRATE" 
    
    uses-permission android:name="android.permission.WAKE_LOCK" 
    
    uses-permission android:name="com.android.vending.BILLING" 

- META-INF/ 

- classes.dex 

- lib/ 

- assets/ 



# Dynamic Analysis 




# Static Analysis 
