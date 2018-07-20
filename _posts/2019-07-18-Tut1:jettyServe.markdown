---
layout: post
title: "Tut1: Jetty Server"
date: 2018-07-17 22:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: jetty-logo.png # Add image post (optional)
tags: [Server, Java]
---
## 1.Jetty là gì?

Jetty là một Web containner.Nó gồm các core thành phần sau:

* Http Server

* Servlet Container

* HTTP Client

>Web Container(hay còn gọi là Servlet Container) là một thành phần của Web Server mà tương tác với Java Servlets. Một Web Container chịu trác nhiệm quản lý vòng đời của Servlets, mapping một URL đến một Servlets được chỉ định. 

## 2. Tại sao phải dùng Jetty?

>“Don’t deploy your application in Jetty, deploy Jetty in your application!”

Jetty được xem như một component của ứng, "nhúng" trực tiếp một web server vào ứng dụng và có khả năng mở rộng tốt. Hơn nữa nó nhẹ, dễ cài đặt nhưng cực kỳ hiệu quả.

## 3.Cài đặt


Thêm vào jetty....



{% highlight java %}
import org.eclipse.jetty.server.Server;
import org.eclipse.jetty.servlet.DefaultServlet;
import org.eclipse.jetty.servlet.ServletContextHandler;
import org.eclipse.jetty.servlet.ServletHolder;
public class SearchServer {
    public static void main(String[] args) throws Exception
    {
        Server server = new Server(8080);

        ServletContextHandler context = new ServletContextHandler(ServletContextHandler.SESSIONS);
        context.setContextPath("/");
        context.setResourceBase("./src/resourceWeb/");
        context.addServlet(SearchForm.class, "/index");
        context.addServlet(AdminForm.class, "/Admin");
        context.addServlet(AdminAlterForm.class, "/Admin/Alter");
        
        ServletHolder holderPwd = new ServletHolder("default", DefaultServlet.class);
        context.addServlet(holderPwd,"/*");
        server.setHandler(context);
       server.start();
        server.join();
    }
}
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/