
[назад](/../..)

# Създаване на сървлети

Сървлетите са джава програми, които обслужват HTTP заявки и имплементират javax.servlet.Servlet интерфейса. Разработчиците на уеб приложения създават сървлети като наследяват javax.servlet.http.HttpServlet класа, абстрактен клас, който имплементира сървлет интерфейса и е специално проектиран за обслужване на HTTP заявки.

```java

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/HelloJava")
public class HelloJava extends HttpServlet {
    
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse
response) throws ServletException, IOException {
    response.setContentType("text/html");
    PrintWriter out = response.getWriter();
    out.println("<h1> Hello Java </h1>");
}
```

# Инсталиране на сървлет

Според стандарта за структура и разположение, сървлетите се поставят в
директорийната структура на `\WEB-INF\classes`. За да бъдат достъпен за клиентски заявки, сървлетът трябва да бъде деклариран в контекста на приложението. Това става по два начина - чрез описание в дескриптора на приложението `web.xml` или чрез анотацията `@WebServlet`.

## Декларация посредством web.xml

```xml
<servlet>
    <servlet-name>HelloJava</servlet-name>
    <servlet-class>HelloJava</servlet-class>
</servlet>

<servlet-mapping>
    <servlet-name>HelloJava</servlet-name>
    <url-pattern>/HelloJava</url-pattern>
</servlet-mapping>
```

Идеята на дескриптора е създаване на връзка между класа на сървлета и URL адреса на, което той ще отговаря. Това става на две стъпки:
- Първата е задаване на псевдоним на сървлета за конкретен клас
- Втората е обвързване на този псевдоним с определен URL

## Декларация посредством анотацията `@WebServlet`

```java
@WebServlet("/HelloJava")
public class HelloJava extends HttpServlet {
    ...
}
```

Тук, сървлета „HelloJava“ е свързан с адреса /HelloJava. Имената на сървлетите и адресите могат да бъдат и най-често са напълно различни.

### Декларация на сървлет с повече от едно URL
```java
@WebServlet(urlPatterns = {"/sendFile", "/uploadFile"})
public class UploadServlet extends HttpServlet {
    ...
}
```
### Декларация на сървлет с допълнителна информация
```java
@WebServlet(
    name = "MyServlet",
    description = "This is my first annotated servlet",
    urlPatterns = "/processServlet"
)
public class MyServlet extends HttpServlet {
...
}
```

### Декларация на сървлет с инициализиращи параметри
```java
@WebServlet(
    urlPatterns = "/imageUpload",
    initParams =
    {
        @WebInitParam(name = "saveDir", value = "D:/FileUpload"),
        @WebInitParam(name = "allowedTypes", value = "jpg,jpeg,gif,png")
    }
)
public class ImageUploadServlet extends HttpServlet {
    ...
}
```

[назад](/../..)
