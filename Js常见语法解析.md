# Js常见语法解析

## 1.xhr

实现xhr请求的方法有两种：1.原生XMLHttpRequest;2.通过jquery封装好的xhr请求方法实现请求。

前者的一大特点就是和其他的js包一样，都是先导入一个包，然后通过创建对象设置属性的方式，来构筑一个请求对象，最后通过.send()完成发包。

```
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://example.com/api", true);  // open创建一个新的请求
xhr.setRequestHeader("Content-Type", "application/json");  // 必须在open的后面
xhr.setRequestHeader("Authorization", "Bearer YOUR_ACCESS_TOKEN");

xhr.onreadystatechange = function() {
    if (xhr.readyState == 4 && xhr.status == 200) {
        console.log(xhr.responseText);
    }
};

xhr.send()
```

而后者则更加简单，各种参数的设置也更加简单明了：

```
$.ajax({
  url: 'https://example.com/api/data',
  method: 'GET',
  headers: {
    'Authorization': 'Bearer token123'
  },
  success: function(response) {
    console.log('Success:', response);
  },
  error: function(xhr, status, error) {
    console.error('Error:', error);
  }
});
```

## 2.promise

实际上promise被称为期约，这个对象存在三种状态，pending/resolved/rejected，而.then()会根据promise的状态调用回调函数，可以注册一个或多个回调函数，而.finally()则只能注册一个回调函数，无论最终结果是resolved还是rejected都会被调用。

什么时候发送状态变化？：简单来说promise.resolved,promise.rejected就会让状态发生变化且永远不会再改变，其中resolved和rejected是promise对象的原型方法。

## 3.extend

重写，相当于在父类的基础上再加属性和方法。