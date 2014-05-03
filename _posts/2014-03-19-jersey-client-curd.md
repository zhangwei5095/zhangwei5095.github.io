---
layout: post
title: 用Jersey构建RESTful服务4--通过jersey-client客户端调用Jersey的Web服务模拟CURD
date: 2014-03-19 03:13
author: admin
comments: true
categories: [Java, Jersey, REST]
tags: [Java, Jersey, RESTful]
---
<p>一、总体说明</p>
<p>通过jersey-client接口，创建客户端程序，来调用Jersey实现的RESTful服务，实现增、删、改、查等操作。</p>
<p>服务端主要是通过内存的方式，来模拟用户的增加、删除、修改、查询等操作。</p>
<p>二、创建服务端</p>
<p>&nbsp;</p>
<p>1.在上文项目中，</p>
<p>在“com.waylau.rest.resources.UserResource“中修改代码，</p>
<p>首先创建一个HashMap，用来保存添加的用户</p>
<p>private static Map&lt;String,User&gt; userMap  = new HashMap&lt;String,User&gt;();<br />
2.创建增、删、改、查 用户资源等操作</p>
<p>/**<br />
* 增加<br />
* @param user<br />
*/<br />
@POST<br />
@Consumes({MediaType.APPLICATION_XML, MediaType.APPLICATION_JSON})<br />
public void createStudent(User user)<br />
{<br />
userMap.put(user.getUserId(), user );<br />
}</p>
<p>/**<br />
* 删除<br />
* @param id<br />
*/<br />
@DELETE<br />
@Path("{id}")<br />
public void deleteStudent(@PathParam("id")String id){<br />
userMap.remove(id);<br />
}</p>
<p>/**<br />
* 修改<br />
* @param user<br />
*/<br />
@PUT<br />
@Consumes(MediaType.APPLICATION_XML)<br />
public void updateStudent(User user){<br />
userMap.put(user.getUserId(), user );<br />
}</p>
<p>/**<br />
* 根据id查询<br />
* @param id<br />
* @return<br />
*/<br />
@GET<br />
@Path("{id}")<br />
@Produces({MediaType.APPLICATION_XML, MediaType.APPLICATION_JSON})<br />
public User getUserById(@PathParam("id") String id){<br />
User u = userMap.get(id);<br />
return u;<br />
}</p>
<p>/**<br />
* 查询所有<br />
* @return<br />
*/<br />
@GET<br />
@Produces({MediaType.APPLICATION_XML, MediaType.APPLICATION_JSON})<br />
public List&lt;User&gt; getAllUsers(){<br />
List&lt;User&gt; users = new ArrayList&lt;User&gt;();<br />
users.addAll( userMap.values() );<br />
return users;<br />
}</p>
<p>三、创建客户端程序</p>
<p>&nbsp;</p>
<p>1.创建包“com.waylau.rest.client”，在包下建一个UserClient.java，代码如下：</p>
<p>&nbsp;</p>
<p>package com.waylau.rest.client;</p>
<p>import javax.ws.rs.client.Client;<br />
import javax.ws.rs.client.ClientBuilder;<br />
import javax.ws.rs.client.Entity;<br />
import javax.ws.rs.client.WebTarget;<br />
import javax.ws.rs.core.MediaType;<br />
import javax.ws.rs.core.Response;</p>
<p>import org.codehaus.jackson.jaxrs.JacksonJsonProvider;</p>
<p>import com.waylau.rest.bean.User;<br />
/**<br />
* 用户客户端，用来测试资源<br />
* @author waylau.com<br />
* 2014-3-18<br />
*/<br />
public class UserClient {</p>
<p>private static String serverUri = "http://localhost:8089/RestDemo/rest";<br />
/**<br />
* @param args<br />
*/<br />
public static void main(String[] args) {<br />
addUser();<br />
getAllUsers();<br />
updateUser();<br />
getUserById();<br />
getAllUsers();<br />
delUser();<br />
getAllUsers();</p>
<p>}<br />
/**<br />
* 添加用户<br />
*/<br />
private static void addUser() {<br />
System.out.println("****增加用户addUser****");<br />
User user = new User("006","Susan","21");<br />
Client client = ClientBuilder.newClient();<br />
WebTarget target = client.target(serverUri + "/users");<br />
Response response = target.request().buildPost(Entity.entity(user, MediaType.APPLICATION_XML)).invoke();<br />
response.close();<br />
}</p>
<p>/**<br />
* 删除用户<br />
*/<br />
private static void delUser() {<br />
System.out.println("****删除用户****");<br />
Client client = ClientBuilder.newClient();<br />
WebTarget target = client.target(serverUri + "/users/006");<br />
Response response = target.request().delete();<br />
response.close();<br />
}</p>
<p>/**<br />
* 修改用户<br />
*/<br />
private static void updateUser() {<br />
System.out.println("****修改用户updateUser****");<br />
User user = new User("006","Susan","33");<br />
Client client = ClientBuilder.newClient();<br />
WebTarget target = client.target(serverUri + "/users");<br />
Response response = target.request().buildPut( Entity.entity(user, MediaType.APPLICATION_XML)).invoke();<br />
response.close();<br />
}<br />
/**<br />
* 根据id查询用户<br />
*/<br />
private static void getUserById() {<br />
System.out.println("****根据id查询用户****");<br />
Client client = ClientBuilder.newClient().register(JacksonJsonProvider.class);// 注册json 支持<br />
WebTarget target = client.target(serverUri + "/users/006");<br />
Response response = target.request().get();<br />
User user = response.readEntity(User.class);<br />
System.out.println(user.getUserId() + user.getUserName() + user.getAge());<br />
response.close();<br />
}<br />
/**<br />
* 查询所有用户<br />
*/<br />
private static void getAllUsers() {<br />
System.out.println("****查询所有getAllUsers****");</p>
<p>Client client = ClientBuilder.newClient();</p>
<p>WebTarget target = client.target(serverUri + "/users");<br />
Response response = target.request().get();<br />
&lt;span style="white-space:pre"&gt; &lt;/span&gt; String value = response.readEntity(String.class);<br />
&amp;nbsp; &amp;nbsp; &lt;span style="white-space:pre"&gt; &lt;span style="white-space:pre"&gt; &lt;/span&gt;&lt;/span&gt; System.out.println(value);<br />
&amp;nbsp; &amp;nbsp; &amp;nbsp; &amp;nbsp; &lt;span style="white-space:pre"&gt; &lt;/span&gt;&amp;nbsp;response.close(); &amp;nbsp;//关闭连接<br />
}</p>
<p>}</p>
<p>四、运行</p>
<p>&nbsp;</p>
<p>启动服务端项目，运行客户端程序UserClient，控制台输出如下</p>
<p>****增加用户addUser****<br />
****查询所有getAllUsers****<br />
[{"userId":"006","userName":"Susan","age":"21"}]<br />
****修改用户updateUser****<br />
****根据id查询用户****<br />
006Susan33<br />
****查询所有getAllUsers****<br />
[{"userId":"006","userName":"Susan","age":"33"}]<br />
****删除用户****<br />
****查询所有getAllUsers****<br />
[]<br />
五、总结</p>
<p>&nbsp;</p>
<p>1.客户端如果需要进行JSON转换，需要进行JSON注册</p>
<p>&nbsp;</p>
<div> Client client = ClientBuilder.newClient().register(JacksonJsonProvider.class);</div>

