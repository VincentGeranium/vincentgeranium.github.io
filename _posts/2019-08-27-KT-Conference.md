---
layout: post
title:  "KT S/W Conferance 2019"
date:   2019-08-27
categories: Study, Conferance
---

# KT Conference 2019

---

## Track 2

### 경로탐색엔진 처리과정

- 경로탐색?
    - 경로를 찾기 위해 수행하는 일련의 전체 과정
    - GPS를 이용 -> 출발지와 목적지 설정 -> 경로가 GPS를 통해 설정
    - 출발지, 목적지 도로 맵매칭 -> 도로 설정 (제일 중요한 경로 탐색의 첫 과정)
    - 경로 선정 -> 여러 경로가 나올 수 있음 -> 비용 낮은 경로 선정
    - 경로 안내 -> 교차로 이미지, 음성안내, 안전정보등을 사용자에게 안내함
    
- 도로 맵매칭
    - 경로를 찾기 위한 첫 단계
    - 출발지에 대한 정확한 선정은 경로에 영향을 미친다
    - 도로 맵매칭은 즉시성도 중요
    
- 도로 맵매칭을 위한 전처리
    - 공간인덱스 생성 -> 공간 트리 구축(K-D Tree) -> 인접링크 k개 후보선성 -> 필터링 -> 정렬 및 선정
    - GPS 정보를 통하여 좌표를 가져옴, 인접 링크를 선정, 필터링을 하고 출발지에 대한 정확한 장소를 선정

- 최적 경로
    - 비용이 최소인 경로
        - 비용 = 거리 가중치, 시간 가중치, 교차로 가중치, 톨비 가중치
        - 시간으로 환산 (모든 가중치들)
        - 가중치의 조합을 미리 제공 ->  ex) 최단거리 = 거리가중치 퍼센테이지가 가장 높은것
        
    - 최적 경로 선정
        - Dijkstra algorithm
        - Astar algorithm

- 경로 선정 개선
    - 응답속도 개선
        - leveling cutting
            - 장거리 경로 주행
            - 작은 도로도 고려
            - 도로 밀도 고려

- 앞으로의 경로탐색
    - 응답속도는 도전 과제 (계속해서 연구 필요) -> 기존의 알고리즘은 한계가 있음 -> 새로운 알고리즘 필요
    - Contraction Hierachies
    - Hub Labeling -> 분산처리 가능, 이전의 알고리즘은 분산처리 x

- 경로 가중치의 한계
    - 모두를 만족시키는 하나의 경로는 없음
        - 다각도로 판단하여 가중치 분석 -> 가중치 조정 -> 테스트
        - 사용자 로그를 기반으로 데이터를 축적, 데이터를 가지고 학습시켜 운전자 성향 분석, 성향에 따른 가중치 개선

- 여전히 해결되지 않는 과제
    - GPS 를 가지고도 애매한 길에 대한 정확한 측정이나 출발지, 목적지 설정과 경로 설정

---

## Track 3

### 기가지니는 왜 Web app을 사용하는가??

- Front-end 영역은 점점 복잡해짐
    - Package Manager : 공통 라이브러리 재활용 -> 개발 리소스 감소
    - SPA : 최초 한번 페이지 전체 로드 이후는 부분적으로 갱신, 사용자 경험 / 데이터통신 최적화, 초기 구동 오래걸림, 검색엔진최적화 어려움
    - component 기반
    - 모듈 번들러, Lint 등 빌드 툴 사용
    
- Web Application의 활용 범위가 다양해지기 때문

- Web App 의 장점
    - 실행 환경의 자유로움 -> 브라우저만 있다면 실행 가능
    - 설치과정 필요 없고 업뎃 손쉬움 -> 브라우저에 URL 입력하면 사용가능, 웹서버에 바로 배포 가능
    - UI컴포넌트화 + 공통기능모듈화
        - 서비스당 개발 기간이 짧아짐
    - 통합 버전 관리 -> 단말별 버전 관리
    - 서비스 유지 관리의 비용 감소 -> 개발 퍼포먼스 향상
    - 버그 fix는 빠르게

---