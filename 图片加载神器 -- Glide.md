---
title: 图片加载神器 -- Glide
tags: 图片加载,Glide,框架
grammar_cjkRuby: true
---
最近的项目需要加载图片，小白就上网寻找这方面的资料，项目的架构为`MVP+Retrofit`,看了比较多的资料，于是决定使用Glide,用了才知道该库很牛。稍微归纳一下，整理学习。

图片加载一直是一个比较棘手的事情，俗话说就是`“坑”`比较多，于是就google了一下这方面的库，有很多图片库，例如Picasso, Universal-Image-Loader,Fresco,Glide等，这些库都是很火的，使用量很大的图片库， 他们各有优点，不能评说那一个不好，根据项目的需求适当选择。

### 几个库的简单比较

 - Picasso：是Square出品的图片库，当然是很厉害的，该公司还有响当当的`Okhttp`和`Retrofit`，都是很牛逼的网络请求库,搭配使用效果可能更好一些，之所以这么说是因为Picasso可以将网络请求到的数据缓存交给Okhttp来处理。
 - Universal-Image-Loader：一个强大的图片加载库，包含的配置比较多，使用很广泛，很老牌。
 - Fresco：是Facebook出品的，也超强大。从知乎问答下看到该库最大的优点是5.0以下（最低2.3）的bitmap加载，在5.0以下，会将图片放到一个特别的内存存储区，称为：`Ashmem区`，在图片不显示的时候也会自动清除内存（这个是必须的），使得App更加流畅，减少图片内存占用引发的内存不足（OOM）。
 - Glide：谷歌推荐使用的图片加载库，Google一些图片应用就使用该库进行图片加载，用起来很流畅，可以说是在Picasso上的进一步扩展，比如支持Gif动态图，在使用时接受更多的上下文等等，他们两者最大的区别在于默认的设置不同，比如默认的图片格式不同，尺寸大小也不同，在下面的链接文章中有具体的分析。
 - 总结：Picasso的能做的Glide也可以做，无非就是配置的不同。

网上关于`Picasso`和`Glide`性能进行比较的文章挺多，不过遗憾的是，大多数都是抄来抄去的，比较清晰的是这篇：[Google推荐的图片加载库Glide介绍][1]，`Picasso`和`Glide`的使用极其相似，但也有不少细节上的区别，看了这篇文章可以大致了解一二。

现在整理一下`Glide`的使用：

### 配置Glide
在Module根目录下的build.gradle中进行库依赖：

``` java

dependencies {
	compile 'com.github.bumptech.glide:glide:$latestVersion'
    compile 'com.android.support:support-v4:19.1.0'
}
```
然后同步一下代码build successful,就可以使用Glide了。
### 使用Glide

``` java
//图片的url
private String image_url = "https://www.image.com/myimage?id=1";
private ImageView imageView = (ImageView)super.findViewById(R.id.image);
Glide.with(context)
	.load(image_url)
    .into(imageView);
```
用这段代码就可以将url所表示的图片装到ImageView显示出来，是不是很爽呢？
with里面的参数不仅仅接受上下文context,还可以是`Activity`,`Fragment`等。Glide不仅仅支持加载网络图片，还支持以下一种加载方式：

 - 加载资源文件：`DrawableTypeRequest<Integer> load(Integer resourceId)`

``` java
Glide.with(context).load(R.drawable.my_image).into(imageview);
```

 - 加载本地文件：`DrawableTypeRequest<File> load(File file)`

``` java
File file = new File("sdcard/myimage/","image.jpg");
Glide.with(context).load(file).into(imageView);
```

 - 加载Uri：`DrawableTypeRequest<Uri> load(Uri uri)`

``` java

File file = new File(Environment.getExternalStorageDirectory() + File.separator +  "image", "image.jpg");
Uri uri = Uri.fromFile(file);
Glide.with(context).load(uri).into(imageView);
```

 - String加载：`DrawableTypeRequest<String> load(String string)`

**设置占位图片**
图片加载并不是很实时的，加载成功的时间是不确定的，在加载时，可以设置一个图片显示在ImageView上进行一些`正在加载...`提示等等。

``` java
Glide.with(context)
	.load(image_url)
    .placehold(R.drawable.loading)
    .into(imageView);
```
在加载网络图片时，如果突然网络断掉，肯定加载不到正确的图片，这时可以设置一个错误图片到ImageView,提示用户加载失败。

``` stylus
Glide.with(context)
	.load(image_url)
    .error(R.drawable.loaderror)
    .into(imageView);
```
当然，也可以给Glide设置监听，当图片加载失败时，可以知道为什么加载失败了。

***我们虽平凡，
但不平庸，
做一个能不停告诉自己前进的人，
一步一个脚印向前！***





  [1]: http://blog.csdn.net/sam_zhang1984/article/details/48524893