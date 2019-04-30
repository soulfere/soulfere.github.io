---
layout: post
title:  "可复用代码片段" 
---

**记录可复用的常用代码片段，持续更新**

---
<br />

获取自定义格式当前时间

{% highlight java %}
"yyyy-MM-dd HH:mm:ss" —— 经典的日期格式
public static String currentTime(String dateFormat) {
    SimpleDateFormat sdf = new SimpleDateFormat(dateFormat);
    String resTime = sdf.format(new Date());
    return resTime;
}
{% endhighlight %}

遍历Map（使用Entry遍历）

{% highlight java %}
Map<String, Object> map = new HashMap();

map.put("aaa", new Random().nextInt(10));
map.put("bbb", new Random().nextInt(10));
map.put("ccc", new Random().nextInt(10));

for (Entry ent : map.entrySet()) {
    System.out.println(ent.getKey());
    System.out.println(ent.getValue());
}
{% endhighlight %}

集合转数组（声明大小）

{% highlight java %}
List<String> list = new ArrayList<String>(2);
list.add("foo");
list.add("bar");
String[] array = new String[list.size()];
array = list.toArray(array);
{% endhighlight %}

HttpGet请求（基于HttpURLConnection）

{% highlight java %}
public static String httpGet(String path) {
    try {
        // GET的地址
        URL url = new URL(path.trim());
        // 打开连接
        HttpURLConnection urlConnection = (HttpURLConnection) url.openConnection();
        // getResponseCode()方法执行后，会自动执行connect方法，所以不需要显式调用
        if (HttpURLConnection.HTTP_OK == urlConnection.getResponseCode()) {
            // 得到输入流
            // 200的情况下，用getInputStream获取返回的输入流
            // 非200的情况下，用getErrorStream获取返回的输入流
            InputStream is = urlConnection.getInputStream();
            ByteArrayOutputStream baos = new ByteArrayOutputStream();
            byte[] buffer = new byte[1024];
            int len = 0;
            while(-1 != (len = is.read(buffer))){
                baos.write(buffer, 0, len);
                baos.flush();
            }
            return baos.toString("utf-8");
        }
    }  catch (IOException e) {
        e.printStackTrace();
    }
    return "";
}
{% endhighlight %}

HttpPost请求（基于HttpURLConnection）

{% highlight java %}
public static String httpPost(String path,String post) {
    URL url = null;
    try {
        url = new URL(path);
        HttpURLConnection httpURLConnection = (HttpURLConnection) url.openConnection();
        httpURLConnection.setRequestMethod("POST");// 提交模式
        // conn.setConnectTimeout(10000);//连接超时 单位毫秒
        // conn.setReadTimeout(2000);//读取超时 单位毫秒
        // 发送POST请求必须设置如下两行
        httpURLConnection.setDoOutput(true);
        httpURLConnection.setDoInput(true);
        // 获取URLConnection对象对应的输出流
        PrintWriter printWriter = new PrintWriter(httpURLConnection.getOutputStream());
        // 发送请求参数
        printWriter.write(post); //post的参数 xx=xx&yy=yy
        // flush输出流的缓冲
        printWriter.flush();
        //开始获取数据
        BufferedInputStream bis = new BufferedInputStream(httpURLConnection.getInputStream());
        ByteArrayOutputStream bos = new ByteArrayOutputStream();
        int len;
        byte[] arr = new byte[1024];
        while((len=bis.read(arr))!= -1){
            bos.write(arr,0,len);
            bos.flush();
        }
        bos.close();
        return bos.toString("utf-8");
    } catch (Exception e) {
        e.printStackTrace();
    }
    return "";
}
{% endhighlight %}


截取字符串标记前的某一部分且不包括标记（注意空指针）

{% highlight java %}
public static String trimString(String str, String pattern) {
    if (str != null && !"".equals(str) && str.contains(pattern)) {
        return str.substring(0, str.lastIndexOf("."));
    }
    return "";
}
{% endhighlight %}


JSON字符串解析（https://github.com/alibaba/fastjson/releases）

{% highlight java %}
import com.alibaba.fastjson.JSON;
import com.alibaba.fastjson.JSONArray;
import com.alibaba.fastjson.JSONObject;

// 解析JSON字符串，获取JSON对象
JSONObject obj = JSONObject.parseObject(new String (response.getBody()));
// 解析JSON字符串，获取JSON数组
JSONArray arr = JSONArray.parseArray(new String (response.getBody()));
// 从JSON对象中获取JSON数组
JSONArray arr = obj.getJSONArray("data");
{% endhighlight %}

JSON对象及JSON字符串构建

{% highlight java %}
import com.alibaba.fastjson.JSON;
import com.alibaba.fastjson.JSONArray;
import com.alibaba.fastjson.JSONObject;

// 通过Map构建JSON字符串（常在构造请求时使用）
Map<String,String> map =  new HashMap<>();
map.put("name", "Jos");
map.put("region","China");
String jsonParam = JSON.toJSON(map).toString();
{% endhighlight %}

读取配置文件（注意配置文件位置）

{% highlight java %}
import java.util.Properties;

// 声明新的配置文件
private static final Properties prop = new Properties();

// 从项目文件中读取配置文件
// 这里注意，如果getResourceAsStream()里直接写配置文件名，那么配置文件要放到src文件夹（这个文件夹是项目设置中设置的代码文件夹，即ClassPath根）下的首层位置，不要放到其他包下
prop.load(Config.class.getClassLoader().getResourceAsStream("constant.properties"));

// 使用getProperty方法，获取属性
String sth = prop.getProperty("THE_KEY");
{% endhighlight %}

截取字符串（以某个字符为标识）

{% highlight java %}
// 待截取字符串
// 注意，对于截取字符串的方法，都是左闭右开，即左边参数包含标识，右边参数不包含标识
// 最后的效果，就是如果截取左边的字符串，不会包含标识字符，如果截取右边的字符串，会包含标识字符
String url = "http://www.baidu.com";
url.substring(url.lastIndexOf(".")); // 返回结果：.com
url.substring(url.lastIndexOf(".") + 1); // 返回结果：com
url.substring(0, url.lastIndexOf("."));// 返回结果：http://www.baidu
{% endhighlight %}

遍历文件夹以及所有子文件夹

{% highlight java %}
import java.io.File;
import java.util.ArrayList;
import java.util.List;

public class TestTraversalFiles {

    public static void main(String[] args) {
        traversalFiles("C:\\Windows");
    }

    public static void traversalFiles(String filePath) {
        List<File> list = new ArrayList<File>();
        File file = new File(filePath);
        list.add(file);
        // 这里的for循环不写i的变化，for循环中第三项之所以改变i的值，是为了避免死循环
        // 实际上，这里不更新i，循环里更新i也可以，不更新i，更新list的大小也可以
        // 此处代码中，list的大小总归会递减到0，循环最终会停止
        for (int i = 0; i < list.size(); ) {
            if (list.get(i).isDirectory()) {
                File[] tempList = list.get(i).listFiles();
                if (tempList != null) {
                    for (int j = 0; j < tempList.length; j++) {
                        list.add(tempList[j]);
                    }
                }
            }
            // 在这里对当前遍历的文件做处理
            System.out.println(list.get(i).getName());
            // 避免集合中存放元素数量过多，造成堆溢出
            list.remove(i);
        }
    }
}
{% endhighlight %}

从硬盘读入二进制文件，转为图片格式输出

{% highlight java %}
public static void fileTransfer (String inputFilePath, String outputFilePath) throws IOException {
    // 把二进制文件读进来（传入的二进制文件没有路径）
    File fi = new File(inputFilePath);
    // 生成的文件（传入路径要加一下图片格式的后缀）
    File fo = new File(outputFilePath);
    FileInputStream fis = new FileInputStream(fi);
    FileOutputStream fou = new FileOutputStream(fo);
    byte buf[] = new byte[1024];
    int i = fis.read(buf);
    while(i != -1) {
        fou.write(buf,0,i);
        i = fis.read(buf);
    }
    fou.close();
    fis.close();
}
{% endhighlight %}