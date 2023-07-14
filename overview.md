# CHAPTER 1: Overview of HTTP

Chương tổng quan ngắn gọn về HTTP, chủ đề chính:

- Cách web clients và servers giao tiếp
- Resourses đến từ đâu
- Cách các giao dịch web hoat động
- Định dạng của các messages được sử dụng cho giao tiếp HTTP
- Cơ bản về TCP
- Các biến thể của giao thức HTTP
- Một số thành phần kiến trúc HTTP được cài đặt xung quanh Internet

## HTTP: The Internet’s Multimedia Courier

- Giao thức HTTP được sử dụng rộng rãi trong công nghệ Web vì nó nhanh, thuận tiện và đáng tin cậy khi truyền dữ liệu
- Chúng ta không cần phải lo đến việc dữ liệu sẽ bị sai, trùng lặp hay xáo trộn trong quá trình truyền

### Web Clients and Servers

- Web contents lives on web servers => web server speak HTTP protocol, so they are often called HTTP servers
- HTTP servers store Internet’s data. Clients send HTTP request to server -> server return the requested data in HTTP responses
- HTTP servers and clients make up the basic components of the WWW

### Resources

- A web resources is the source of web content
- The simplest kind of web resource is static file on the web server’s filesystem
- Resources can also be software programs that generate content on demand, based on your identity, on what info you’ve request,…
- Summary, a resources is any kind of content source

### Media Types

- HTTP carefully tags each object being transported through the Web with a data format label called a MIME types.
- MIME (Multipurpose Internet Mail Extensions) was originally designed to solve problems encountered in moving messages between different electronic mail systems. It’s work so well for email that HTTP adopted it to describe and label its own multimedia content
- Web servers attach a MIME type to all HTTP object data. When a web browser gets an object back from a server, it looks at the associated MIME type to see if it knows how to handle the object
- A MIME type is a textual label, represented as a primary object type and a specific subtype, separated by a slash.Example: text/html, text/plain, image/jpeg

### URIs

- Each web servers resource has a name, so clients can point out what resources they are interested in.
- This name is called a uniform resource identifier or URI Example: http://www.gsttech.vn/favicon.ico is URI for an image resource
- URI come in two flavors, called URLs and URNs

### URLs

- The uniform resource locator (URL) is the most common form of resource identifier. It describe the specific location of a resource on a particular server and tell you exactly how to fetch a resource from a precise, fixed location
  ￼ - The first part of the URL is called the scheme, and it describes the protocol used to access the resource. This is usually the HTTP protocol (http://) - The seconds part gives server Internet address (www.joes-hardware.com) - The rest names a resource on the web servers (/specials/saw-blade.gif)
- Today, almost URI is a URL

### URNs

- The seconds flavor of URI is the uniform resource name, or URN. a URN serves as a unique name for a particular piece of content, independent of it’s location
- URNs are still experimental and not yet widely adopted. To work effectively, URNs need a supporting infrastructure to resolve resource locations; the lack of such an infrastructure has also slowed their adoption. But URNs do hold some exciting promise for the future. We’ll discuss URNs in a bit more detail in Chapter 2, but most of the remainder of this book focuses almost exclusively on URLs.
- Unless stated otherwise, we adopt the conventional terminology and use URI and URL interchangeably for the remainder of this book.

## Transactions

An HTTP transaction consists of a request command and a response result. This communication happens with formatted blocks of data called HTTP messages

### Method

- HTTP request message has a method. The method tells the server what action to perform

### Status Codes

- Every HTTP response comes back with a status code. The status code is a three-digit numeric code that tells the client if the request succeeded or if other actions are required
  Web Pages Can Consist of Multiple Objects

### Message

- HTTP request are simple, line-oriented sequences of characters. Because they are plain text, not binary, they are easy for humans to read and write
- HTTP messages consist of three parts:
  - Start line: the first line of the message is the start line, indicating what to do for a request or what happened for a response
  - Header fields: Zero or more header fields follow the start line. Each header field consists of name and a value, separated by a colon for easy parsing. The headers end with a blank line. Adding a header fields is as easy as adding another line
  - Body: after the blank line is an oprional message body containing any kind of data. Request bodies carry data to the web server; response bodies carry data back to the client. Unlike the start line and header, which are textual and structured, the body can contain arbitrary binary data and text of course.

## Connections

Let’s talk about how messages move from place to place, across Transmission Control Protocol (TCP) connections

### TCP/IP

- HTTP is an application layer protocol, it doesn’t worry about the nitty-gritty details of network communication; instead it leaves the details of networking to TCP/IP, the popular Internet transport protocol
- TCP provides:
  - Error-free data transportation
  - In-order delivery
  - Unsegmented data stream
- The Internet itself is based on TCP/IP, a popular layered set of packet-switched network protocols spoken by computers and network devices around the world. TCP/IP hides the peculiarities and foibles of individual networks and hardware, letting computers and network of any type talk together reliably.
- Một khi kết nối TCP được thiết lập, messages được trao đổi giữa client và server sẽ không bao giờ bị mất, hư hỏng hoặc bị xáo trộn khi nhận dữ liệu
- Trong thuật ngữ mạng, giao thức HTTP được xếp nằm trên TCP. HTTP sử dụng TCP để vận chuyển messages của nó. Tương tự như vậy, TCP được xếp lớp trên IP

### Connections, IP Addresses, and Port Numbers

- Trước khi một HTTP client có thể gửi message đến server, nó cần phải thiết lập một kết nối TCP/IP với server sử dụng địa chỉ Internet Protocol (IP) và số cổng (Port)

## Architectural Components of the Web

Trong phần tổng quan, chúng ta tập trung vào cách hai ứng dụng web (client-server) giao tiếp với nhau qua lại để triển khai các giao dịch cơ bản. Phần này, chúng ta sẽ tìm hiểu tổng quan về một số ứng dụng web phổ biển khác, bao gồm:

- Proxies: Các server HTTP trung gian nằm giữa client và server - Caches: Kho lưu trữ bản sao dữ liệu phổ biến của server

- Caches: Kho lưu trữ bản sao dữ liệu phổ biến của server

- Gateways: Các Web server đặc biệt sử dụng để kết nối đến các ứng dụng khác - Tunnels: Các proxies đặc biệt dùng để chuyển tiếp giao tiếp HTTP

- Tunnels: Các proxies đặc biệt dùng để chuyển tiếp giao tiếp HTTP

- Agents: Các clients bán thông minh sử dụng để thực hiện các request HTTP tự động

Proxies

- Thành phần quan trọng trong việc bảo mật web, tích hợp ứng dụng và tối ưu hoá hiệu suất
