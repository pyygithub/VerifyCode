# 验证码插件：VerifyCode
## 使用方法：

----------


-  导入verifycode.jar到项目WEB-INF/lib
-  在web.xml中配置servlet
>     <servlet>
>     	<servlet-name>ImageServlet</servlet-name>
>     	<servlet-class>com.bdyc.verifycode.ImageServlet</servlet-class>
>     </servlet>
>     <servlet-mapping>
>     	<servlet-name>ImageServlet</servlet-name>
>     	<url-pattern>/verifyCode.jpg</url-pattern>
>     </servlet-mapping>


- 在页面使用img标签发送请求即可：

> 		验证码： <img id="codeImg" src="verifyCode.jpg" />


-  使用生成验证码：
> 	
> public void doGet(HttpServletRequest request, HttpServletResponse response)
> 			throws ServletException, IOException {

> 		//获取输入的验证
> 		String code = request.getParameter("code");
> 		//从session中获取生成的验证码，"verifyCode"存入session中的验证码key值名称
> 		String sessionCode = (String) request.getSession().getAttribute("verifyCode");
> 		if(code.equalsIgnoreCase(sessionCode)){
> 			write(response,"ok");
> 		}else{
> 			write(response,"fail");
> 		}
> 	}
- 效果图：

![](http://i.imgur.com/WKd1mqn.png)
