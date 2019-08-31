---
layout: post
title:  "컴파일러 와 인터프리터"
date:   2019-08-28
categories: Study, CS
---

# 컴파일러 와 인터프리터

---

## 개요

컴파일러, 인터프리터 둘 다 C나 자바 같은 고레벨 언어로 작성된 코드를 기계어로 변환하는 것은 공통점이나 그 과정에 있어서 차이를 보인다

- 컴파일러는 전체소스코드를 보고 명령어를 수집하고 재구성

- 인터프리터는 소스코드의 각 행을 연속적으로 분석하며 

- 컴파일 언어와 인터프리터 언어의 가장 큰 차이점은 **컴파일 시점**이다 (런타임 전에 컴파일을 하는지 안하는지)

---

## 컴파일러 (Complier)

---

<img width="750" alt="Compiler" src="https://user-images.githubusercontent.com/42841888/63821181-f41f3f80-c986-11e9-8898-c006ffb44c0f.jpg">

- 컴파일러는 특정 프로그래밍 언어로 이루어진 문서를 다른 프로그래밍 언어로 옮기는 프로그램을 말한다

    - 문서는 소스 코드 또는 원시 코드라고 부르고, 출력된 문서를 목적 코드라고 한다
    
    - 목적 코드틑 주로 다른 프로그램이나 하드웨어가 처리하는데 용이한 형태로 출력되지만 사람이 읽을 수 있는 문서 파일이나 그림 파일 등으로 옮기는 경우도 있다
    
- 원시 코드에서 목적 코드로 옮기는 과정을 컴파일이라고 한다

- 소스 코드를 컴파일 하는 이유는 사람에게 이해하기 쉬운 형태의 고수준 언어로부터 실행 가능한 기계어로 변환하기 위해서이다.

- 컴파일러는 사람이 소스코드를 작성하면 그 소스코드를 한번에 번역한다

    - 줄 단위로 번역을 하는 인터프리터에 비해 시간이 오래 걸리고 과정이 복잡하다

- 한 번 번역을 하면 실행파일(목적파일)이 생성되어 메모리를 사용하지만 다음에 실행할 때는 이 파일만 실행하면 되기 때문에 실행 시간은 인터프리터에 비해 빠르다

---

## 인터프리터 (Interperter)

---

<img width="750" alt="interpreter" src="https://user-images.githubusercontent.com/42841888/63821247-36e11780-c987-11e9-8d9f-099011e419e4.jpg">


- 인터프리터는 고레벨 언어를 중간 코드(Intermediate code)로 변환하고 이를 각 행마다 실행한다.
    
- 인터프리터는 각 행 마다 실행하는 도중 에러가 보고되면 이후 작성된 코드를 살펴보지 않는다

- Ex) Python은 인터프리트 언어, C, C++은 컴파일 언어

- 인터프리터는 줄 단위로 번역과 실행을 진행, 번역시간은 빠르지만 실행시간은 느리다

- 직접 실행하기 때문에 실행파일(목적파일)을 생성하지 않아 메모리는 사용하지 않는다.

---

## 참고자료

[얏구님의 블로그](https://m.blog.naver.com/ehcibear314/221228200531)

[BlankSpace님의 티스토리 블로그](https://blankspace-dev.tistory.com/219)

[초보몽키님의 개발공부로그](https://wayhome25.github.io/cs/2017/04/13/cs-14/)

[티스토리 블로그](https://steady-snail.tistory.com/1)