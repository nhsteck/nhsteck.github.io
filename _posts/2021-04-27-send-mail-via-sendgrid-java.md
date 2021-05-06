---
title: Tích hợp gửi mail qua SendGrid bằng Java
author: Hùng Sơn
date: 2021-04-27 15:49:00 +0700
categories: [Java cơ bản]
tags: [java, sendgrid]
pin: false
image:
  src: /assets/img/posts/sendgrid.png
  alt: sendgrid
---

## 1. Giới thiệu

* Sendgrid là một dịch vụ cho phép ứng dụng của mình có thể gửi mail cho khách hàng bằng email doanh nghiệp của bạn mà không cần phải dựng 1 mail server riêng. Với 100 mail miễn phí 1 ngày, đây cũng là 1 sự lựa chọn cho các bạn có ý định khởi nghiệp, hoặc các doanh nghiệp nhỏ.

* Nếu dùng quá 100 email miễn phí mỗi ngày, bạn cũng có thể cân nhắc mua thêm các gói cực kỳ rẻ với giá từ khoảng 15$ / tháng. Để biết thêm chi tiết, bạn vào trang này để xem giá và giới hạn của từng gói để chọn cho mình 1 gói phù hợp nhé. <a href='https://sendgrid.com/pricing/' target='_blank'>https://sendgrid.com/pricing/</a>

![](/assets/img/posts/sendgrid_plan.png)

## 2. Tạo tài khoản SendGrid

* Để đăng ký tài khoản, bạn vào <a href='https://signup.sendgrid.com/' target='_blank'>https://signup.sendgrid.com/</a>

* Sau đó, nhập địa chỉ email và password, tich chọn `I'm not a robot` và `I accept the Terms of Service and have read the Services Privacy Policy`. Xong nhấn `Create Account`

![](/assets/img/posts/sendgrid_create_1.png)

* Điền thêm các thông tin cần thiết (có dấu `*` màu đỏ) như:
  * First Name: Tên của bạn
  * Last Name: Họ của bạn
  * Company Name: Tên công ty
  * Company Website: Tên miền website
  * What is your role: chức vụ của bạn là gì
  * How many emails do you send per month?: Bạn dự định gửi bao nhiêu email mỗi tháng
  * How many employees work at your company?: Công ty của bạn có bao nhiêu nhân viên

* Nhấn `Get Started`, vậy là bạn đã đăng ký xong account rồi nhé

![](/assets/img/posts/sendgrid_create_2.png)

* Tuy nhiên, account của bạn chưa được xác nhận. Bạn cần phải vào email mà bạn đăng ký, mở email được gửi từ SendGrid, sau đó nhấn `Confirm Email Address`

![](/assets/img/posts/sendgrid_create_3.png)

## 3. Tạo tài khoản để gửi mail

* Đây là tài khoản Sender (người gửi), nó tách biệt hoàn toàn với account quản lý SendGrid mà bạn vừa đăng ký ở bước 2. Thông tin trong tài khoản này sẽ được hiển thị trên email của người nhận (như tên, địa chỉ email đăng ký)

* Đầu tiên, bạn cần đăng nhập vào SendGrid với account mà bạn đã tạo ở bước 2.

* Nếu chưa có Sender nào, thì SendGrid sẽ hiẹn màn hình hướng dẫn tạo 1 Account. Bạn nhấn vào `Create a Single Sender`

![](/assets/img/posts/sendgrid_4.png)

* Tiếp theo, bạn điền các thông tin cần thiết (Có dấu `*` màu đỏ) nhé:
  * From Name: Tên sẽ hiển thị trên email gửi đi
  * From Email Address: Email hiển thị
  * Reply To: Email hiển thị khi trả lời lại
  * Company Address: địa chỉ công ty của bạn
  * Nickname: tên đại diện trong cái danh sách Sender của bạn để dễ phân biệt, không hiển thị trên email của người nhận

![](/assets/img/posts/sendgrid_5.png)

* Tiếp theo, nhấn `Create`

* Cuối cùng, bạn vào email mà bạn đăng ký làm Sender, mở email mà SendGrid gửi cho bạn, nhấn `Verify Single Sender` để xác nhận tài khoản nhé

![](/assets/img/posts/sendgrid_6.png)

* Trên màn hình danh sách Sender có, ngay cột Verified có dấu Tick màu xanh, như vậy là ok nhé

![](/assets/img/posts/sendgrid_7.png)

## 4. Tạo API Key SendGrid API để gửi mail

* Sau khi đăng nhập SendGrid, bạn vào <a href='https://app.sendgrid.com/guide/integrate' target='_blank'>https://app.sendgrid.com/guide/integrate</a> để bắt đầu tạo API key

* Chọn nút `Web API`

![](/assets/img/posts/sendgrid_8.png)

* Sau đó, chọn ngôn ngữ mà bạn muốn integrate vào. Ở đây mình chọn Java.

![](/assets/img/posts/sendgrid_9.png)

* Tiếp theo, bạn đặt tên cho API Key mà mình cần tạo trong field `My First API Key Name` -> Nhấn `Create Key`

![](/assets/img/posts/sendgrid_10.png)

* Sau đó, hệ thống sẽ tự phát sinh ra key, bạn nhớ giữ lại key này cho việc tích hợp API nhé

![](/assets/img/posts/sendgrid_11.png)

* Ngay màn hình này, ở phía dưới sẽ có hướng dẫn tích hợp bằng Java, bạn hãy dùng code đó để tích hợp vào ứng dụng của mình, sau đó hãy gửi thử 1 email nhé.

* Cuối cùng, bạn nhấn vào `I've integrated code above` để xác nhận mình đã tích hợp vào ứng dụng, nhấn `Next: Verify Integration`

![](/assets/img/posts/sendgrid_12.png)

## 5. Tích hợp SendGrid bằng Java

* Đầu tiên, bạn thêm thư viện của sendgrid vào project

  ```xml
  <dependency>
    <groupId>com.sendgrid</groupId>
    <artifactId>sendgrid-java</artifactId>
    <version>4.0.1</version>
  </dependency>
  ```

* Sau đó, bạn follow theo code phía dưới khá đơn giản nhé

  ```java
  package com.nhsteck.SendGrid;
  
  import java.io.IOException;
  
  import com.sendgrid.*;
  
  public class SendGridDemo {

    // SendGrid API Key
    public static String SENDGRID_API_KEY = "API_KEY_CUA_BAN";

    // Email mà bạn đã tạo sender ở bước trước
    public static String SENDER_EMAIL = "blog@nhsteck.com";

    // Email người nhận
    public static String MAIL_TO = "info@nhsteck.com";

    // Tiêu đề của email
    public static String TITLE = "Chào mừng bạn đến với NHS Teck Blog";

    // Nội dung email
    public static String CONTENT = "Chúc bạn một ngày mới vui vẻ.";

    public static void main(String[] args) {
      Email from = new Email(SENDER_EMAIL);
      Email to = new Email(MAIL_TO);
      String subject = TITLE;
      Content content = new Content("text/plain", CONTENT);

      Mail mail = new Mail(from, subject, to, content);
      SendGrid sg = new SendGrid(SENDGRID_API_KEY);
      Request request = new Request();
      try {
          request.setMethod(Method.POST);
          request.setEndpoint("mail/send");
          request.setBody(mail.build());
          Response response = sg.api(request);
          System.out.println(response.getStatusCode());
          System.out.println(response.getBody());
          System.out.println(response.getHeaders());
      } catch (IOException ex) {
          ex.printStackTrace();
      }
    }

  }
  ```

* Vậy là xong rồi nhé, khá đơn giản phải không các bạn.