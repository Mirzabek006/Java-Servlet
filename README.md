# Java-Servlet
Java Servletlariga kirish
Oxirgi yangilanish: 2025-yil 4-oktabr
Java Servlet - bu Java-ga asoslangan veb-server yoki dastur serverida ishlaydigan Java dasturi. U mijoz so'rovlarini qayta ishlaydi, ularni qayta ishlaydi va dinamik ravishda javoblar yaratadi. Servletlar samaradorligi va masshtablanishi tufayli ko'plab server tomonidagi Java ilovalarining asosini tashkil qiladi.

Java Servletlarining xususiyatlari
Server tomonida ishlang.
Murakkab mijozlar so'rovlarini samarali bajaring.
Dinamik javoblarni yarating.
CGI kabi eski texnologiyalarga qaraganda yaxshiroq ishlashni ta'minlang.
Korxona darajasidagi veb-ilovalarda yuqori darajada kengaytirilishi mumkin.
Java Servletlari Arxitekturasi
Java servlet konteyneri juda muhim rol o'ynaydi. U yuklarni muvozanatlash, sessiyalarni boshqarish va resurslarni taqsimlash kabi muhim vazifalarni bajarish uchun javobgardir, barcha so'rovlar yuqori trafik sharoitida samarali qayta ishlanishini ta'minlaydi. Konteyner so'rovlarni bir nechta holatlarda tarqatadi, bu esa tizim ish faoliyatini yaxshilashga yordam beradi.

Servlet arxitekturasini rasmning o'zidan quyida keltirilganidek tasvirlash mumkin:  

Jsp-servlet-arxitekturasi
Servlet arxitekturasi ish jarayoni:
Servletlarni bajarish asosan oltita asosiy bosqichni o'z ichiga oladi: 

Mijozlar so'rovni veb-serverga yuboradilar.
Veb-server so'rovni qabul qiladi.
Veb-server so'rovni tegishli servletga yuboradi.
Servlet so'rovni qayta ishlaydi va javobni chiqish shaklida yaratadi.
Servlet javobni veb-serverga qaytaradi.
Veb-server javobni mijozga qaytaradi va mijoz brauzeri uni ekranda ko'rsatadi.
Server tomonidagi kengaytmalarga ehtiyoj
Server tomonidagi kengaytmalar serverda dasturlarni ishga tushirish orqali dinamik veb-sahifalarni yaratish imkonini beradi.
Veb-serverlar ishlab chiquvchilarga ushbu ilovalarni yaratishda yordam berish uchun API-larni taqdim etadi.
Java Servletlari (Jakarta EE tarkibiga kiradi) Java asosidagi veb-ishlab chiqish uchun asosiy API hisoblanadi.
Servlet konteyneri
Servlet konteyneri, shuningdek, Servlet dvigateli sifatida ham tanilgan, Java Servlet komponentlari uchun ish vaqti muhitini ta'minlaydigan integratsiyalashgan obyektlar to'plamidir. Bu veb-mijoz so'rovlarini qayta ishlash uchun veb-server ustida Java Servlet komponentlarini boshqaradigan tizimdir. 

Servlet konteyneri tomonidan taqdim etiladigan xizmatlar: 

Tarmoq xizmatlari: Servlet klassini yuklaydi. Yuklash mahalliy fayl tizimidan, masofaviy fayl tizimidan yoki boshqa tarmoq xizmatlaridan bo'lishi mumkin. Servlet konteyneri so'rov va javob yuboriladigan tarmoq xizmatlarini taqdim etadi.
MIME asosidagi xabarlarni dekodlash va kodlash : MIME asosidagi xabarlarni dekodlash va kodlash xizmatini taqdim etadi.
Servlet konteynerini boshqarish: Servletning hayot aylanishini boshqaradi.
Resurslarni boshqarish : HTML fayllari, Servletlar va JSP sahifalari kabi statik va dinamik resurslarni boshqaradi.
Xavfsizlik xizmati: Resurslarga kirishni avtorizatsiya qilish va autentifikatsiya qilish bilan shug'ullanadi.
Sessiyani boshqarish: URL yo'liga sessiya identifikatorini qo'shish orqali sessiyani saqlaydi
Asosiy Servlet yaratish
Talablar

JDK (Java Development Kit) ni o'rnating
Apache Tomcat serverini o'rnating (masalan, 9 yoki 10-versiya)
Eclipse yoki IntelliJ IDEA kabi IDE ni o'rnating 
Servlet API JAR faylini yuklab oling (allaqachon Tomcat-ga kiritilgan)
Misol: Servlet qanday ishlashining oddiy misoli:

1-qadam: Dinamik veb-loyihani yarating (Eclipse-da)
Eclipse -> Fayl -> Yangi -> Dinamik Veb-loyihani oching
Loyihaga nom bering (masalan, HelloWorldServlet)
Maqsadli ish vaqti -> Apache Tomcat-ni tanlang
Tugatish tugmasini bosing
2-qadam: Servlet klassini yarating
src -> New-> Servlet ustiga o'ng tugmasini bosing
Uni HelloWorldServlet deb nomlang va Finish tugmasini bosing
HelloWorldServlet.java


import java.io.*;
import jakarta.servlet.*;
import jakarta.servlet.http.*;

public class HelloWorldServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) 
    throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body><h1>Hello, World!</h1></body></html>");
    }
}
Izoh:

HelloWorldServlet HttpServletni kengaytiradi.
doGet() HTTP GET so'rovlarini qayta ishlaydi.
response.setContentType("text/html") javob turini bildiradi.
PrintWriter HTML javobini mijozga qaytarib yuboradi.
Servletni sozlash
Servletni joylashtirish uchun uni web.xml faylida sozlashingiz kerak. Ushbu fayl URL manzillarini servletlarga bog'laydi. Masalan,

XML asosidagi konfiguratsiya (web.xml):


<web-app xmlns="http://www.oracle.com/webfolder/technetwork/jsc/xml/ns/javaee/index.html" 
         xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
         xsi:schemaLocation="http://www.oracle.com/webfolder/technetwork/jsc/xml/ns/javaee/index.html 
         http://www.oracle.com/webfolder/technetwork/jsc/xml/ns/javaee/index.html/web-app_3_0.xsd" 
         version="3.0">

    <servlet>
        <servlet-name>HelloWorldServlet</servlet-name>
        <servlet-class>HelloWorldServlet</servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>HelloWorldServlet</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>

</web-app>
Izoh:
Bu URL manzillarini servletlarga moslashtirish uchun ishlatiladigan web.xml fayli. Shunday qilib, http://localhost:8080/yourApp/hello manziliga kirganingizda, servlet ishga tushadi va brauzerda "Salom, Dunyo!" degan yozuvni ko'rsatadi.

Izohga asoslangan konfiguratsiya (zamonaviy yondashuv)
Servlet 3.0 versiyasidan boshlab, servlet konfiguratsiyasi annotatsiyalar yordamida ham amalga oshirilishi mumkin. web.xml dan foydalanish o'rniga, biz servletni @WebServlet annotatsiyalari yordamida sozlashimiz mumkin.


@WebServlet("/hello") 
public class HelloWorldServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body><h1>Hello, World!</h1></body></html>");
    }
}
Izoh: Bu yerda biz servletni to'g'ridan-to'g'ri kodda ro'yxatdan o'tkazish uchun @WebServlet("/hello") annotatsiyasidan foydalandik (web.xml kerak emas). U servletni /hello URL manziliga bog'laydi.

Nima uchun boshqa texnologiyalar o'rniga Java Servletni tanlash kerak?
Dinamik veb-kontent server tomonidagi texnologiyalarni talab qiladi. Ko'p variantlar mavjud bo'lsa-da, Java Servlet Common Gateway Interface (CGI) kabi alternativalarga nisbatan afzalliklari bilan ajralib turadi.

CGI cheklovlari:

Jarayonning qo'shimcha xarajatlari: CGI har bir mijoz so'rovi uchun jarayonni yaratadi va yo'q qiladi, bu esa yuqori resurslarni sarflashga olib keladi.
Masshtablash muammolari: Mijozlarning so'rovlarining ortishi bilan ishlashning sustligi.
