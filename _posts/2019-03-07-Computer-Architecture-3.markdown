---
layout: post
title:  "컴퓨터시스템의 개요 - 3"
date:   2019-03-07
categories: Computer Architecture
---

# 컴퓨터시스템의 개요

## 정보의 표현과 저장

- 이 글은 김종현님의 저서인 Computer Architecture를 보고 정리한 내용입니다

#### 컴퓨터가 받아들이고 처리하는 정보의 종류로는 "프로그램 코드(program code)"와 "데이터(data)"가 있다
- 디지털 컴퓨터에서 그러한 정보들은 모두 2진수(binary number)를 나타내는 비트(bit)들의 조합으로 표현된다

#### 프로그램 코드를 2진 비트들로 표현하는 방법에 대하여 살펴보자

#### 컴퓨터 프로그램은 C, PASCAL FORTRAN, COBOL 등과 같은 고급언어(high-level language)를 이용하여 작성된다
- 이렇게 작성된 프로그램은 영문자들과 숫자들로 이루어져 있어서 사람들이 이해하기는 쉽지만, 디지털 회로들로 이루어진 컴퓨터의 하드웨어는 전혀 이해하지 못한다
- 이 프로그램은 "컴파일러(compiler)"라고 불리는 소프트웨어에 의해 하드웨어가 이해할 수 있는 언어로 번역된다
- 컴퓨터의 하드웨어가 이애할 수 있는 이러한 언어를 "기계어(machine language)"혹은 "기계 코드(machine code)"라고 한다
    - ##### *컴파일러(compiler)
        - 고급언어 프로그램을 기계어로 변환해주는 소프트웨어
    - ##### *기계어(machine language)
        - 컴퓨터 하드웨어가 이해할 수 있는 언어

#### 고급 언어들은 어느 컴퓨터에서 사용되든 거의 동일하지만, 기계어는 CPU마다 서로 다르다
- 즉, CPU의 내부 구조에 따라 그 하드웨어가 이해할 수 있는 언어도 달라지는 것이다
- 그러한 언어상의 차이를 해결하기 위하여 고급 언어와 기계어 사이에는 각 CPU 고유의 중간 언어가 존재한다
    - 이 언어를 "어셈블리 언어(assembly language)" 혹은 "어셈블리 명령어(assembly instruction)"라고 부른다
        - 이러한 언어로 작성된 프로그램을 "어셈블리 프로그램(assembly program)"이라고 한다
- ##### 고급언어 프로그램이 컴퓨터에서 처리되기 위해서는 먼저 어셈블리 프로그램으로 번역되고, 그런 다음에 해당 CPU를 위한 기계어 프로그램으로 번역 되어야 한다

#### 고급-언어 프로그램이 기계어 프로그램으로 번역되는 과정

#### 각 단계에서의 프로그램 형태에 대한 간단한 예를 보여주고 있다

#### 고급-언어 프로그램은 X와 Y를 더하고, 결과 값을 기억장치의 Z번지에 저장하라는 것이다
- 고급 언어 프로그램 [예] Z = X + Y
- 어셈블리 프로그램 [예] LOAD A,X , ADD A, Y , STOR Z,A
- 기계어 프로그램 [예] 00100101 , 1000110 , 01000111

#### 그 문장을 어셈블리 프로그램으로 번역하면 다음과 같아진다
- LOAD A,X : 기억장치 X번지의 내용을 읽어서 레지스터 A에 적재(load)하라
- ADD A,Y :기억장치 Y번지의 내용을 읽어서 레지스터 A에 적재된 값과 더하고, 결과를 레지스터 A에 적재하라
- STOR Z,A : 레지스터 A의 내용을 기억장치 Z번지에 저장(store)하라

##### 여기서 각 어셈블리 명령어(이하 명령어(instruction)라고 함)가 지정하는 동작을 개략적으로 짐작할 수 있도록 하기 위하여 사용된 기호인 'LOAD', 'ADD 및 'STOR'를 "니모닉스(mnemonics)"라고 부른다
- ##### *명령어(instruction)
    - 어셈블리 명령어(assembly instruction)의 약칭
- ##### *니모닉스(mnemonics)
    - 명령어가 지정하는 동작을 나타내는 간략화된 기호

- 명령어는 CPU가 수행해야 할 동작뿐 아니라 처리할 데이터가 저장되어 있는 기억장치 주소나 레지스터 번호도 구체적으로 지정해준다
- 이와 같은 명령어들은 CPU의 내부 구조와 밀접한 관계가 있기 때문에, 어셈블리 프로그래머는 컴퓨터의 내부 구조를 알고 있어야 프로그램을 작성할 수 있다
- 어셈블리 언어로 작성된 프로그램은 "어셈블러(assembler)"라는 소프트웨어가 기계어 프로그램을 번역해준다
    - ##### *어셈블러(assembler)
        - 어셈블리 프로그램을 기계어로 번역해주는 소프트웨어

##### 컴파일의 마지막 결과인 기계어 프로그램은 2진수인 1과 0들의 조합으로 이루어진다
- 위의 [예]에서는 어셈블리 명령어들이 각각 8-비트 기계어로 번역되었다
- 기계어의 비트틀의 의미를 살펴보면 LOAD A,X 명령어에 대한 기계어는 아래와 같다
    - 연산코드 : 001 오퍼랜드 : 00101
    - 이 경우에는 기계어가 두 개의 필드(field)들로 구성되는 것으로 가정하였는다
        - "연산코드 필드(op code field)"에 저장된 001은 '레지스터 A로 적재하라'는 연산을 지정해주는 비트들
        - "오퍼랜드 필드(operand field)"의 00101은 적재될 데이터가 저장되어 있는 기억장치 주소를 가리킨다
        - 위의 기계어에서는 오퍼랜드가 5번지를 가리키고 있다
        - 따라서 이 기계어는 '기억장치 5번지의 내용을 읽어서 레지스터 A에 저장하라'는 명령을 나타내는 것이다

##### 명령어는 비트들의 개수와 용도 및 주소지정 방식에 따라 다양하게 구성될 수 있다
- 만약 위의 예와 같이 연산 코드가 세 비트들로 이루어진다면 $2^3$ = 8가지의 연산들을 지정할 수 있다
- 또한 오퍼랜드 비트들의 수가 다섯 개이므로, 주소를 지정할 수 있는 기억 장소들의 최대 수는 $2^5$ = 32개가 된다
- 이와 같은 비트들의 구성을 "명령어 형식(Instruction format)"이라고 한다
    - ##### *명령어 형식(Instruction format)
        - 명령어의 비트 수와 용도 및 필드 구성 방법을 지정해주는 형식

##### 번역된 기계어들은 순서대로 기억장치에 저장되는데, 아래의 예는 기계어들이 데이터들과 함꼐 기억장치에 저장되어 있는 모습을 보여주고 있다

```
주소
0        00100101 명령어 
1        10000110 명령어
2        01000111 명령어
3                 명령어
4        ...      명령어
.        . 
.        .
.        .
X        00011011 데이터
Y        11010111 데이터
Z                 데이터
.
.
.
```

- 위의 예에서 기계어들은 0번지부터 저장되어 있고, 계산에 사용될 데이터들은 각각 X번지와 Y번지에 저장되어 있다(실제로는 기억 장소들의 주소도 2진수로 표현된다)
- 각 기억 장소에 저장되는 데이터 단위로서, CPU에 의해 한 번에 처리될 수 있는 비트들의 그룹을 "단어(word)"라고 부른다
- 단어의 길이는 CPU에 하드웨어 구조에 따라 8비트, 16비트, 32비트, 64비트 등으로 다양하다
- 위 예에서는 단어가 8비트 즉 한 "바이트(byte)"인 것으로 가정하고 있다
- 디지털 컴퓨터에서 데이터를 2진수로 표현하는 방법에는 여러가지가 있다
- 위 예에서 X번지와 Y번지에 2의 보수(2's complement)로 표현된 +27과 -41이 각각 저장되어 있다
    - ##### *단어(word)
        - CPU에 의해 한 번에 처리 될 수 있는 비트들의 그룹
