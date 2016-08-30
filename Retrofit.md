#Android网络请求--Retrofit
Retrofit是一个很流行的网络请求库，由square开发的开源项目，采用注解的方式进行网络请求。在其官网页面上显示：
> **A type-safe HTTP client for Android and Java**

##创建Retrofit对象
```java
public static final BASE_URL = "http://127.0.0.1:8080/VIID/";
Retrofit retrofit = new Retrofit.Builder()
    .baseUrl(BASE_URL)
    .addConvertFactory(GsonConverterFactory.create())
    .build();
```
> 在创建Retrofit2对象时，传入的BASE_URL必须以'/'结束，不然会抛出IllegalArgumentException异常</br>
在以后进行各个接口定义时，使用`GET`、`POST`、`PUT`、`DELETE`是传入的路径都是相对URL。
