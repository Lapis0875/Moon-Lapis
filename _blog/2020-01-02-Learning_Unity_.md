---
title: "Unity 공부 - 오브젝트 움직이는 법"
date: 2019-12-30
categories: blog
tags: [blog, Unity]
comments: true
published: false
---

오늘은 유니티 엔진에서 오브젝트를 움직이는 방법을 공부했다.

유니티에서는 이전 편에서 이야기했던, 프로젝트에서 설정할 수 있는 보편적인 입력들의 리스트가 존재한다. 이 리스트를 활용해, 우리는 축 이동을 구현할 수 있다. 



1. 축 이동량 구하기

   ```csharp
   Input.GetAxis("Horizontal");	// -1~1 사이의 값 (float)로 반환됨
   Input.GetAxisRaw("Horizontal");	// 1 혹은 -1의 두가지 값으로 반환됨
   ```

   Input 클래스에서 제공하는 GetAxis와 GetAxisRaw의 두 메소드를 사용해 우리는 플레이어의 이동을 위해 플레이어가 해당 축으로 얼마나 이동했는지 알 수 있다.
   GetAxis 는 플레이어가 해당 축으로 얼마나 이동했는지 보다 세세하게 알려주는 메소드로, 가중치가 존재하여 키 입력을 -1 ~ 1 사이의 값으로 반환한다.
   반면, GetAxisRaw는 가중치 없이 플레이어가 이동한 방향에 따라 -1 또는 1만 반환한다. GetAxisRaw로 수치를 구할 때, 해당 축의 양 방향을 동시에 입력하면 0을 반환한다.

   

2. Vector와 Scala
   수학에서는 우리가 흔히 아는 정수와 같이 '값' 만 가지고 있는 것들을 스칼라, 방향과 크기 모두 가지고 있는 속도와 같은 것들을 벡터라고 부른다. 이는 고등학교 수학 및 과학때 배울 수 있는 내용이다.

   유니티에서도 각 오브젝트들을 움직일 때, Vector를 사용한다.
   벡터는 크기와 방향을 모두 갖는 값이므로, 유니티에서는 벡터를 다음과 같이 생성할 수 있다.

   ```csharp
   v = new Vector3(x,y,z);
   ```

   Vector3는 3차원 벡터 클래스로, x축, y축, z축으로 얼마나 이동할건지 그 수치를 인자로 전달하여 생성한다.

   ```csharp
   v = new Vector2(x,y);
   ```

   Vector2는 2차원 벡터 클래스로, x축, y축으로 얼마나 이동할건지 그 수치를 인자로 전달하여 생성한다.

   확인해보니 Vector4도 존재한다. 이것도 위와 같은 형태로 4개 축의 방향(부호)와 수치를 인자로 전달하여 생성하면 될 것이다. 4번째 축은 어떤 축을 말하는건지는 알아보고 추가하겠다.
   

3. 오브젝트 이동시키기



```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    void Update()
    {
        
    }
}
```



Scene에 캡슐 하나를 배치한 뒤, 이 스크립트를 부여한 후, 게임을 실행해 잘 작동하는지 확인해보자.

{% include youtube.html id = "" %}









