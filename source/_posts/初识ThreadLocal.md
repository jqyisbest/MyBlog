---
title: 初识ThreadLocal
top: 2
copyright: true
date: 2020-05-15 16:43:22
categories:
- Java
tags:
- ThreadLocal
- 多线程
- 并发
- 线程安全
- Spring
---

ThreadLocal是 Java 1.5中新增的一个模板类，可以为指定的线程存储数据，数据存储以后，只有指定线程可以得到存储数据。

<!--more-->

官方解释如下：

```java
/**
 * This class provides thread-local variables.      These variables differ from
 * their normal counterparts in that each thread that accesses one (via its
 * {@code get} or {@code set} method) has its own, independently initialized
 * copy of the variable.  {@code ThreadLocal} instances are typically private
 * static fields in classes that wish to associate state with a thread (e.g.,
 * a user ID or Transaction ID).
 *
 * <p>For example, the class below generates unique identifiers local to each
 * thread.
 * A thread's id is assigned the first time it invokes {@code ThreadId.get()}
 * and remains unchanged on subsequent calls.
 * <pre>
 * import java.util.concurrent.atomic.AtomicInteger;
 *
 * public class ThreadId {
 *     // Atomic integer containing the next thread ID to be assigned
 *     private static final AtomicInteger nextId = new AtomicInteger(0);
 *
 *     // Thread local variable containing each thread's ID
 *     private static final ThreadLocal&lt;Integer&gt; threadId =
 *         new ThreadLocal&lt;Integer&gt;() {
 *             &#64;Override protected Integer initialValue() {
 *                 return nextId.getAndIncrement();
 *         }
 *     };
 *
 *     // Returns the current thread's unique ID, assigning it if necessary
 *     public static int get() {
 *         return threadId.get();
 *     }
 * }
 * </pre>
 * <p>Each thread holds an implicit reference to its copy of a thread-local
 * variable as long as the thread is alive and the {@code ThreadLocal}
 * instance is accessible; after a thread goes away, all of its copies of
 * thread-local instances are subject to garbage collection (unless other
 * references to these copies exist).
 *
 * @author  Josh Bloch and Doug Lea
 * @since   1.2
 */
```

当你为传递线程安全发愁时，当你使用springMVC且想要给旧方法（天知道有多少处使用，万恶的旧方法）传递一些新参数时，来试试ThreadLocal。

> 一段吐槽，可以不看：  
>
> 最近在为现有本地系统做app用的API，组长只肯写个登录校验，其它都得我来==；但是现有接口又臭又长，业务逻辑写的到处都是，实在不想去重写它，那么就只有包装起来。  
>
> 但是，很多接口中又调用了UserUtils.getUser()以获取当前用户，而getUser()又和shrio相关。对于API请求来说shrio直接废了，所以得想办法修改UserUtils.getUser()以获取到API请求中的用户信息。

