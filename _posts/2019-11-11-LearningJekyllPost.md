---
layout: post
title: "Jekyll 블로그에서 Markdown 형식의 파일로 글 쓰는 법 알아보기"
date: 2019-11-11
categories: jekyll update
tags: [learning, Jekyll]
comments: true
---
앞으로 Jekyll 블로그를 운영하기 때문에, Jekyll에 Markdown 형식의 글을 올리는 방법과, Markdown 형식의 글을 쓰는 방법에 대해 알아보았다.

(1) Jekyll 블로그 운영하기
기본적으로 Jekyll 블로그에 제공되는, welcome-to-jekyll.markdown 파일을 번역해 보았다.

우선, 대부분의 글은 `_posts` 폴더에 위치한다. 그리고 모든 글의 양식은 다음과 같다. :

`YEAR-MONTH-DAY-title.md`

`YEAR`은 4자리의 정수, `MONTH`와 `DAY`는 두자리의 정수로 작성한다. 그 후에 적절한 제목을 작성한 뒤, 마크다운 확장자(.md)로 마무리한다.

또, Jekyll은 코드를 보여주는데 적합한 기능을 제공한다.
아래 코드를 보자.

{% highlight python %}
def print_hi(name):
  print(f'Hi, {name}')
print_hi('Tom')
#=> prints 'Hi, Tom'
{% endhighlight %}

위와 같은 형태로 글 내에 작성한 코드에 하이라이팅을 입히고 싶다면, 아래 사진처럼 작성하면 된다.
<img src='../assets/img/2019-11-11-LearningJekyllPost.jpg' width="100%" height="100%" title="Jekyll Code Snippet Function" alt="Jekyll에서 제공하는 코드 하이라이팅 기능이다."

(2) Markdown 알아보기
아직까진 잘 모르고 있던 Markdown 양식에 대해 자세히 알아보았다.
