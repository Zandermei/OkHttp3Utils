# OkHttp3Utils
网路请求封装<br>
1、封装了常用的网络请求方法 get 和 post 方法<br>
2、get方法支持追加参数<br>
3、网络请求乃是异步操作，服务端返回数据已做线程处理，可直接更新UI<br>

具体方法使用

在项目的根目录的build.gradle文件中添加如下代码<br>
```
   maven { url 'https://jitpack.io' }
```

添加完成后的效果如下
```
    allprojects {
        repositories {
	   
            maven { url 'https://jitpack.io' }
        }
    }

```
<br>

步骤2.添加依赖项<br>

```
	dependencies {
		....省略了其他依赖
	        implementation 'com.github.Zandermei:MyOkHttp:1.0'
	}
```



----------在自己的--Application--中初始化网络------
```
        //初始化网络请求
        OkHttp3Utils.initEvent();
	
```
----配置完成---即可使用----<br>

---------------GET-无参数请求-请求----------
```
                OkHttp3Utils.sendGetRequest("url", new ResultListener() {
                    @Override
                    public void onSucess(Call call, String msg) {
                        //成功返回，默认返回字符串，可转json数据 处理
                      	//可直接更新UI
                    }

                    @Override
                    public void onFilure(Call call) {
                        //请求失败返回
			//可直接更新UI
                    }
                });

```
--------------Get-url链接追加---参数请求--------
```
                Map<String, String> map = new HashMap<>();
                map.put("key","value");
                //通过 Map 集合添加数据
                OkHttp3Utils.sendGetRequest("url", map, new ResultListener() {
                    @Override
                    public void onSucess(Call call, String object) {
                        //返回成功----处理数据直接更新UI
                    }

                    @Override
                    public void onFilure(Call call) {
                        //返回失败--处理
                    }
                });
		
```		
--------------post---请求---------<br>
```
                Map<String, String> map = new HashMap<>();
                map.put("key","value");
                //通过 Map 集合添加数据
               OkHttp3Utils.sendPostRequest("url", map, new ResultListener() {
                   @Override
                   public void onSucess(Call call, String object) {
                       //返回成功--处理数据
                       Toast.makeText(getApplicationContext(),"成功",Toast.LENGTH_SHORT).show();
                   }

                   @Override
                   public void onFilure(Call call) {
                       //返回失败
                       Toast.makeText(getApplicationContext(),"失败",Toast.LENGTH_SHORT).show();
                   }
               });
```



		
