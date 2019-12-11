---
layout: post
title: "Jekyll 블로그에서 Markdown 형식의 파일로 글 쓰는 법 알아보기"
date: 2019-11-11
categories: jekyll
tags: [learning, Jekyll]
comments: true
---
앞으로 Jekyll 블로그를 운영하기 때문에, Jekyll에 Markdown 형식의 글을 올리는 방법과, Markdown 형식의 글을 쓰는 방법에 대해 알아보았다.

(1) Jekyll 블로그 운영하기
기본적으로 Jekyll 블로그에 제공되는, welcome-to-jekyll.markdown 파일을 번역해 보았다.

우선, 대부분의 글은 `_posts` 폴더에 위치한다. 그리고 모든 글의 양식은 다음과 같다. :

`YEAR-MONTH-DAY-title.md`

`YEAR`은 4자리의 정수, `MONTH`와 `DAY`는 두자리의 정수로 작성한다. 그 후에 적절한 제목을 작성한 뒤, 마크다운 확장자(.md)로 마무리한다.

(2) Markdown 알아보기
아직까진 잘 모르고 있던 Markdown 양식에 대해 자세히 알아보았다. 현재 블로그에 적용한 테마인 Moon 테마에 기본적으로 들어있던 글들 중에 markdown-syntax 라는 글이 있어 번역해본다.

(번역중...)

# HTML 요소들

# 제목 1

## 제목 2

### 제목 3

#### 제목 4

##### 제목 5

###### 제목 6

### 본문 내용

*기울임* **강조**

### 블럭으로 감싸진 글

> 다람쥐 헌 쳇바퀴에 타고파

## 목록 유형

### 정렬된 목록

1. 1번 요소
   1. 1번 세부 요소
   2. 2번 세부 요소
   3. 3번 세부 요소
2. 2번 요소

### 정렬되지 않은 목록

* 1번 요소
* 2번 요소
* 3번 요소

## 표

| 헤더1 | 헤더2 | 헤더3 |
|:--------|:-------:|--------:|
| 1번 칸   | 2번 칸   | 3번 칸   |
| 4번 칸   | 5번 칸   | 6번 칸   |
|----
| 1번 칸  | 2번 칸   | 3번 칸   |
| 4번 칸  | 5번 칸   | 6번 칸   |
|=====
| Foot1   | Foot2   | Foot3
{: rules="groups"}

## 코드 하이라이팅

{% highlight css %}
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
{% endhighlight %}

## 버튼

Make any link standout more when applying the `.btn` class.

{% highlight html %}
<a href="#" class="btn btn-success">Success Button</a>
{% endhighlight %}

<div markdown="0"><a href="#" class="btn">Primary Button</a></div>
## KBD

You can also use `<kbd>` tag for keyboard buttons.

{% highlight html %}
<kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd>
{% endhighlight %}

Press <kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd> to move your car. **Midtown Maddness!!**

## Notices

**Watch out!** You can also add notices by appending `{: .notice}` to a paragraph.
{: .notice}