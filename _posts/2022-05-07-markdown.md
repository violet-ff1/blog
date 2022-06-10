---
layout: post
title: 抽取通用的查询方法，获取entityClass
subtitle: DAO层创建泛型类，通过DAOImpl传来的实体类，DAO层构造方法使用getClass()获取
gh-repo: violet-ff1/blog
gh-badge: [star, fork, follow]
tags: [原生JDBC]
comments: true
---

日拱一卒

**为了抽取通用的查询方法，sql可以使用Objec占位，但是无法确定其实体类的属性类型，故DAO需获取实体类。下面则是展示DAO使用泛型类，通过DAOImpl传实体类，DAO的构造方法使用getClass()获取**

代码展示：
{% highlight javascript linenos %}
 public BaseDAO() {
        //getClass() 获取Class对象，当前执行的是new FruitDaoImpl()，创建的是FruitDAOImpl的实例
        //那么子类构造方法内部首先调用父类BaseDAO的无参构造方法
        //因此此处的getClass()会被执行，但是getClass获取的是FruitDAOImpl的Class
        //所以getGenericSuperclass()获取到的是BaseDAO的Class
        Type genericSuperclass = getClass().getGenericSuperclass();
        //ParameterizedType 参数化类型
        Type[] actualTypeArguments = ((ParameterizedType) genericSuperclass).getActualTypeArguments();
        //只需获取一个即可
        Type actualType = actualTypeArguments[0];
    }
{% endhighlight %}

解决问题，解决了DAO类无法确定实体类进行的查询rs.get？()。
