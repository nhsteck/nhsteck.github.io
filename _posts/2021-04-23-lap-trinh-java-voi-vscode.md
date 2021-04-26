---
title: Lập trình Java với Visual Studio Code. Tại sao lại không?
author: Hùng Sơn
date: 2021-04-23 21:46:00 +0700
categories: [Java cơ bản]
tags: [java, vscode]
pin: false
image:
  src: /assets/img/posts/vscode.png
  alt: vscode
---

## 1. Giới thiệu

* Hiện nay, Java vẫn là một trong những ngôn ngữ được ưa chuộng bởi các công ty phát triển phần mềm, các lập trình viên cũng như là trong môi trường giáo dục. Tính đến năm 2021, Java vẫn nằm trong top 3 những ngôn ngữ được sử dụng rộng rãi nhất trên toàn thế giới. 

* Sự thành công của Java có đóng góp không nhỏ của các công cụ hỗ trợ phát triển như Netbeans, Eclipse, IntelliJ ... giúp cho các lập trình viên có thể phát triển ứng dụng dễ dàng và nhanh chóng, và đặc biệt hầu hết các công cụ đều rất mạnh nhưng lại hoàn toàn miễn phí. 

* Hôm nay, mình sẽ giới thiệu thêm cho các bạn một công cụ có dung lượng khá là nhẹ, chiếm tài nguyên của hệ thống thấp nhưng lại hỗ trợ rất mạnh cho các ngôn ngữ lập trình, đó là Visual Studio Code (VSCode). Đây là một công cụ hoàn toàn miễn phí, được tạo ra bởi ông trùm của phát triển phần mềm là Microsoft, và cũng có đầy đủ chức năng để lập trình viên có thể dễ dàng phát triển ứng dụng của mình.

## 2. Các bước cài đặt

### 2.1 Cài đặt Java

* Tất nhiên rồi, để có thể phát triển ứng dụng bằng Java, thì điều đầu tiên cần làm là phải cài đặt Java, cụ thể hơn là JDK (Java Development Kit).

* Bạn có thể vào trang [https://jdk.java.net/](https://jdk.java.net/), chọn version mà mình muốn cài đặt. Sau đó, tuỳ vào hệ điều hành mà bạn muốn cài (Windows, Linux, MacOS), bạn hãy chọn phiên bản phù hợp và làm theo hướng dẫn cài đặt thôi nhé.

![Java JDK](/assets/img/posts/jdk_java_net.png)

### 2.2 Cài đặt Visual Studio Code

* Không có gì đơn giản hơn là vào trang web [https://code.visualstudio.com/download](https://code.visualstudio.com/download), sau đó chọn bản cài đặt phù hợp với hệ điều hành hiện tại mà bạn đang xài, nhấn vào là sẽ tự động download về cho mình.

* Sau khi tải về, bạn chỉ cần giải nén, nhấn vào icon của VSCode là bạn đã có thể chạy ứng dụng lên rồi

![VSCode web](/assets/img/posts/vscode_download.png)

### 2.3 Cài đặt các Extensions cần thiết để phát triển Java trên VSCode

* Sau khi bạn mở VSCode rồi, hãy nhấn vào `Extensions` bên phía tay trái (1). 

* Tìm kiếm Extensions với cụm từ `Java Extension Pack` (2). Sau đó, bạn chọn Extension đó rồi nhấn Install

![VSCode web](/assets/img/posts/vscode_extensions.png)

* Quá trình cài đặt khá nhanh chóng, và sau khi cài đặt hoàn thành, bạn cần khởi động lại VSCode để nó hoạt động một cách mượt mà nhất nhé.

* Giới thiệu chút về extension `Java Extension Pack` nhé. Đây là một gói tiện ích mở rộng, được chính Microsoft làm ra giúp các lập trình viên có thể dễ dàng phát triển ứng dụng viết bằng Java trên chính VSCode. Tiện ích này bao gồm các thành phần sau:

  * Language Support for Java™ by Red Hat: Đây là một gói tiện ích hỗ trợ Java cho VSCode được làm ra bởi Red Hat. Đây cũng là một công ty phát triển phần mềm của Mỹ khá nổi tiếng, hẳn không còn xa lạ gì với các anh em lập trình viên. Gói tiện ích này bao gồm: Code Navigation (di chuyển con trỏ đến các function một cách nhanh bằng phím tắt), Auto Completion (Gợi ý code), Refactoring (định dạng code) và Code Snippets (tự động phát sinh ra code với một mẫu có sẵn)

  * Debugger for Java: nghe tên là đã biết rồi, debug từng dòng code :)

  * Java Test Runner: chạy và debug JUnit/TestNG

  * Maven for Java: hỗ trợ cho các dự án Java bằng Maven

  * Project Manager for Java: quản lý project Java, các libraries, resources, packages, classes ...

  * Visual Studio IntelliCode: một bộ AI của VSCode, gợi ý và hỗ trợ viết code nhanh hơn

## 3. Kết luận

* VSCode là một công cụ khá mạnh cho lập trình viên không chỉ riêng Java, mà còn hỗ trợ cho các ngôn ngữ khác

* Trong bài tiếp theo, mình sẽ hướng dẫn chi tiết phát triển một dự án bằng Java trên VSCode nhé.
