# Работа със сървъра Tomcat 

Сървърът Tomcat представлява безплатен Web-контейнер, който може да изпълнява Web-приложения сред който са Java сървлети, JSP страници. 
Tomcat е Web-application сървър, написан на Java, който при клиентска HTTP заявка освен статични файлове, може да връща и динамични 
документи, създадени в резултат от изпълнението на сървлет или JSP.

# Инсталиране на Tomcat Сървърът 

Tomcat е достъпен за свободно изтегляне от адрес: 

http://jakarta.apache.org/tomcat/

Последната версия на сървъра може да се изтегли като .zip файл (пример: apache-tomcat-9.0.27-windows-x64.zip), който трябва да се
разархивираме в директория предназначена за мрежови достъп. Препоръчва се в името на директорията да не се съдържат интервали, 
защото интервалите служат за разделители в Java и могат да създатат проблеми. 

Преди да използваме Tomcat Сървърът е необходимо да инсталираме JDK на нашия компютър. Можем да си го издърпаме от:

http://java.sun.com/j2se/ 

#Стартиране на Tomcat 

За стартиране на сървъра Tomcat е необходимо първо в променливите на средата (Environment variables) да добавим променливата JAVA_HOME 
със стойност директорията където е инсталиран JDK. Това може да стане например от конзолата с командата 

``` PowerShell
set JAVA_HOME=C:\j2sdk1.4.2_01
```

или от настройките на операционната система. 

За да стартираме самия сървър Tomcat, трябва да изпълним скрипта за стартиране, който се намира в поддиректорията bin на основната 
директория на Tomcat сървъра. Например ако сме инсталирали Tomcat в директория F:\DevTools\apache-tomcat-9.0.27, нашата bin директория 
ще бъде 

``` PowerShell
F:\DevTools\apache-tomcat-9.0.27\bin. 
```

В тази поддиректория bin има файл за управлвние на сървиса service.bat, с който можем да стартираме сървъра. Стартирането на сървъра става с командата:

``` PowerShell
./service.bat install
```

Използвайте PowerShell.

Когато се стартира сървърът слуша на порт 8080 за идващи HTTP заявки, а не на стандартния за протокола HTTP порт 80. Ако няма съобщения за грешки, то сървърът е стартирал успешно. 

За да проверим дали всичко работи нормално, можем да стартираме нашия Web-браузър и да въведем адреса 

http://localhost:8080/

Ако всичко е наред, ще се появи заглавната страница на Tomcat. 