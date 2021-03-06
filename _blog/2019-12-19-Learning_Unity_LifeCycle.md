---
title: "Unity 공부 - Life Cycle(생명주기)"
date: 2019-12-19
categories: blog
tags: [blog, Unity]
comments: true
---

오늘은 유니티 엔진의 라이프사이클에 대해 공부했다.

유니티의 라이프 사이클은 다음과 같다.



Awake() -> OnEnable() -> Start() -> FixedUpdate() -> Update() -> LateUpdate() -> OnDisable() -> OnDestroy()



각각이 하는 역할에 대해서 정리해봅니다.

1. 초기화 영역
   1. Awake() :
      게임 내에 오브젝트가 생성되는 그 순간, 1회 실행되는 이벤트이다.
   2. Start() :
      Update() 함수가 실행되기 전, 1회 실행되는 이벤트이다.
2. 프레임 영역
   1. FixedUpdate() :
      물리 연산 업데이트가 진행되는 이벤트로 고정된 주기로 반복되어 CPU 부하가 심한 편이라고 한다.
      초당 약 50회정도 반복되며, 보통은 물리연산과 관련된 로직을 주로 작성한다.
   2. Update() :
      주로 물리연산을 제외한 게임 내 로직 등의 연산을 담당한다. 환경에 관계없이 고정적인 FixedUpdate와는 다르게 환경에 영향을 받는다.
   3. LateUpdate() :
      모든 Update 이벤트가 종료된 이후에 실행되는 이벤트로, 주로 게임 로직의 후처리나 플레이어를 따라가는 카메라 등을 구현한다고 한다.
3. 해체 영역
   1. OnDestroy() :
      게임 오브젝트가 해체되는 순간에 1회 실행되는 이벤트이다.
4. 활성화 / 비활성화 영역
   1. OnEnable() :
      게임 오브젝트가 활성화되는 순간에 1회 실행되는 이벤트이다. 
      이 이벤트는 Awake -> OnEnable -> Start 순으로 실행된다.
   2. OnDisable() :
      게임 오브젝트가 비활성화되는 순간에 1회 실행되는 이벤트이다. 
      이 이벤트는 LateUpdate -> OnDisable -> OnDestroy 순으로 실행된다.



이제 이 라이프사이클을 코드로 작성해보자.



LifeCycle.cs

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class LifeCycle : MonoBehaviour
{
    private void Awake()
    {
        Debug.Log("플레이어 생성!");
    }
    
    private void OnEnable()
    {
        Debug.Log("플레이어가 로그인 했습니다!");
    }
    
    private void Start()
    {
        Debug.Log("플레이어가 전투 준비를 합니다.");
    }
    
    private void FixedUpdate()
    {
        Debug.Log("플레이어가 이동합니다.");
    }

    private void Update()
    {
        Debug.Log("플레이어가 스킬을 시전합니다!");
    }

    private void LateUpdate()
    {
        Debug.Log("플레이어의 점수가 오릅니다.");
    }

    private void OnDisable()
    {
        Debug.Log("플레이어가 로그아웃 했습니다.");
    }

    private void OnDestroy()
    {
        Debug.Log("플레이어가 사망하였습니다!");
    }
}
```



Scene에 캡슐 하나를 배치한 뒤, 이 스크립트를 부여한 후, 게임을 실행해 잘 작동하는지 확인해보자.

{% include youtube.html id = "90KIVYW5uao" %}



이 라이프사이클을 활용하면, 유니티의 각 오브젝트들에 필요한 기능들을 보다 효과적으로 다룰 수 있을 것이다. 예를 들면, 플레이어가 몬스터를 죽였을 때 보상을 주려고 할 때, 몬스터 오브젝트의 OnDestroy() 함수에 보상을 주는 기능을 구현하면 될 것이다. 잘 알아두었다 요긴하게 활용해보자.









