# POST 请求跨域问题

在Ajax跨域请求时，如果使用POST方法进行请求，首次POST请求将会失败，浏览器实际发送的不是post请求 而是option请求，所以如果需要使用POST进行请求，则需要就行一次冗余请求，不然就使用get请求，否则肯定会报跨域错误