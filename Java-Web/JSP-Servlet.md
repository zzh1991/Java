## JSP
* 动态网页技术
* 实现了业务逻辑与视图实现的分离
* 可以被看作是一个特殊的Servlet

* script标签：<%! %>, <% %>, <%= %>
* page指令：<%@ page language=java %>
* include指令：<%@ include file="" %>，静态包含，存在变量名冲突
* include动作: <jsp:include page="" />，动态包含，不存在变量名冲突，一般使用include动作
* forward动作：<jsp:forward page=""> <param value="", name="">
* import指令：<%@ page import="" %>
