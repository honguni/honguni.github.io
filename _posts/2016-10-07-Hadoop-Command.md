---
layout: post
title: Hadoop 기초 & 명령어 모음
---

# Hadoop configuration 파일
* conf/masters : 세컨더리 네임노드가 동작하는 노드르 ㄹ명시
* conf/slaves : 데이터노드와 태스크트래커가 동작하는 노드를 명시
* conf/core-site.xml : 하둡 분산 파일 시스템과 하둡 맵리듀스 모두에 적용할 수 있는 스크립트
* conf/hdfs-site.xml : 하둡 분산 파일 시스템 설정 스크립트
* conf/mapred-site.xml : 하둡 맵리듀스 설정 스크립트

# Hadoop 명령어
* namenode -format : 하둡 분산 파일 시스템 포맷 수행
