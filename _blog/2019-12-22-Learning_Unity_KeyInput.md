---
title: "Unity 공부 - 키보드, 마우스 입력 받는 법"
date: 2019-12-22
categories: blog
tags: [blog, Unity]
comments: true
---

오늘은 유니티 엔진에서 키보드와 마우스 입력을 받는 방법을 공부했다.



1. 키 입력의 3가지 상태
   유니티는 키 입력을 3가지로 구분한다. 각각 Down, Stay, Up이라고 부른다.

   * Down 상태는 키가 입력된 순간을 의미한다.
   * Stay 상태는 키가 눌러진 채로 유지되고 있는 상태를 의미한다.
   * Up 상태는 눌려져있던 키가 떼지는 순간을 의미한다.

   유니티에서는 키 입력을 구분해 입력 값을 보다 세밀하게 다룰 수 있도록 한다.

2. 아무 키의 입력 상태 받기

   유니티에서는 입력을 Input 클래스에서 관리한다. 이 Input 클래스에는 여러 변수와 메소드가 존재하는데, 여기서 anyKey~ 변수들은 입력된 키의 종류에 관계없이 키가 입력되었을때 true값을 가진다.

   구체적으로 나눠보면 다음과 같다.

   * anyKeyDown : 어떤 키가 Down 상태에 있을 때, true 값을 가진다.
   * anyKey : 어떤 키가 Stay 상태에 있을 때, true 값을 가진다.
   * anyKeyUp : 어떤 키가 Up 상태에 있을 때, true 값을 가진다.

3. 키보드 입력 받기
   이제 특정한 키의 입력을 받아보자.
   Input 클래스에서는 GetKey~ 라는 메소드들을 제공한다. 이 메소드들 역시 키 입력의 3가지 상태에 따라 구분된다. 이 함수는 다음과 같이 사용할 수 있다.

   * GetKeyDown(KeyCode.X) : 키보드의 X 키가 Down 상태에 있을 때, true 값을 가진다.
   * GetKey(KeyCode.Y) : 키보드의 Y 키가 Stay 상태에 있을 때, true 값을 가진다.
   * GetKeyUp(KeyCode.Z) : 키보드의 Z 키가 Up 상태에 있을 때, true 값을 가진다.

   여기서 각 메소드들에 인자로 전달된 KeyCode 클래스는 키보드, 컨트롤러 등의 각각의 키에 해당하는 변수들을 가진 클래스로, 우리는 이 클래스를 사용해 입력을 받을 키를 지정한다.

4. 마우스 입력 받기
   마우스 입력은 키보드 입력과 비슷하게 GetMouseButton~ 메소드들을 사용한다. 이 함수들은 다음과 같이 사용할 수 있다.

   * GetMouseButtonDown(0) : 마우스의 왼쪽 버튼이 Down 상태에 있을 때, true 값을 가진다.
   * GetMouseButton(1) : 마우스의 오른쪽 버튼이 Stay상태에 있을 때, true 값을 가진다.
   * GetMouseButtonUp(0) : 마우스의 왼쪽 버튼이 Up 상태에 있을 때, true 값을 가진다.

   마우스 입력은 키보드 입력과 다르게 KeyCode 클래스를 사용하지 않고 정수를 사용해 마우스 키를 지정한다.
   그러나 KeyCode 클래스에 Mouse0~Mouse6의 변수들이 제공되는 것을 확인했다. 이것은 따로 알아본 뒤 나중에 글로 정리해보도록 하겠다.



이제 코드로 작성해보자. 각 키를 누르면 플레이어가 취할 수 있는 행동을 Debug.Log()로 출력해보았다.



Player.cs

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    void Update()
    {
        if (Input.anyKeyDown)
            Debug.Log("어떤 키가 눌렸습니다.");
        if (Input.anyKey)
            Debug.Log("어떤 키가 눌려있습니다.");

        /*
         * KeyCode : 키보드, 컨트롤러 등의 키를 담당하는 클래스.
         * 키보드 큰 엔터 : KeyCode.Return
         * 숫자 키패드 엔터 : KeyCode.KeypadEnter
         * esc : KeyCode.Escape
         */

        if (Input.GetKeyDown(KeyCode.U))
            Debug.Log("접속중인 유저 목록을 확인합니다.");

        if (Input.GetKey(KeyCode.LeftShift))
            Debug.Log("플레이어가 달리고 있습니다.");

        if (Input.GetKeyUp(KeyCode.R))
            Debug.Log("탄창을 재장전했습니다!");

        if (Input.GetMouseButtonDown(0))
            Debug.Log("권총을 발사합니다!");

        if (Input.GetMouseButton(1))
            Debug.Log("에너지를 충전하는 중입니다...");

        if (Input.GetMouseButtonUp(1))
            Debug.Log("에너지포를 발사합니다!");
    }
}
```



Scene에 캡슐 하나를 배치한 뒤, 이 스크립트를 부여한 후, 게임을 실행해 잘 작동하는지 확인해보자.

{% include youtube.html id = "tLbOBqlERBQ" %}



다음에는, 오늘 공부한 키 입력을 활용해 오브젝트의 이동을 키보드 입력으로 제어해보는 방법을 공부해야겠다.









