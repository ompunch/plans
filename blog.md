## 1. 数据模型

博客主要是如下几个模型，用户、文章、评论、分类、标签等。在django中，模型一般都继承自models.Model，需要先倒入相关模块，`from django.db import models`

### 1.1 用户模型
用户模型继承自AbstractUser，通过`from django.contrib.auth.models import AbstractUser`倒入相关模块，

- XXXUser
	- username
	- password
	- email
	- avatar
	- intro

### 1.2 文章模型
- Post
	- title
	- body
	- created_time
	- excerpt
	- category = models.ForeignKey(Category)
	- tags = models.ManyToManyField(Tag, ...)
	- author = models.ForignKey(User)

#### 1.2.1 多对一关系

ForeignKey表明一种一对多的关联关系，比如文章和分类的关系，一篇文章只能对应一个分类，而一个分类下可以有多篇文章。

#### 1，2，2 多对多关系

ManyToManyField表明一种多对多的关系，比如文章和标签，一片文章可以有多个标签，而一个标签页可以有多个文章。


### 1.3 评论模型

- Comment
	- user = models.ForeignKey(xxx)
	- post = models.ForeignKey(Post)
	- text 评论内容
	- create_time
	- parent = models.foreignKey('self') 引用

### 1.4 分类模型
- Category
	- name

### 1.5 标签模型
- Tag
	- name
