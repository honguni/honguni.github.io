---
layout: post
title: Hadoop 기초 & 명령어 모음
---

# Hadoop Configuration 파일
* conf/masters : 세컨더리 네임노드가 동작하는 노드르 ㄹ명시
* conf/slaves : 데이터노드와 태스크트래커가 동작하는 노드를 명시
* conf/core-site.xml : 하둡 분산 파일 시스템과 하둡 맵리듀스 모두에 적용할 수 있는 스크립트
* conf/hdfs-site.xml : 하둡 분산 파일 시스템 설정 스크립트
* conf/mapred-site.xml : 하둡 맵리듀스 설정 스크립트

# Hadoop 명령어
* namenode -format : 하둡 분산 파일 시스템 포맷 수행
* hadoop fs -cat [path]			// 경로의 파일 읽기 (리눅스의 cat 명령어)
* hadoop fs -count [path]			// 경로상의 폴더, 파일, 파일사이즈를 보여줌
* hadoop fs -cp [소스 경로] [복사 경로]	// hdfs 상에서 파일 복사
* hadoop fs -df /user/hadoop		// 디스크 공간 확인
* hadoop fs -du /user/hadoop		// 파일별 사이즈 확인
* hadoop fs -dus /user/hadoop		// 폴더의 사이즈 확인
* hadoop fs -get [소스 경로] [로컬 경로]	// hdfs 의 파일 로컬로 다운로드
* hadoop fs -ls [소스 경로]		// 파일 목록 확인
* hadoop fs -mkdir [생성 폴더 경로]	// 폴더 생성
* hadoop fs -put [로컬 경로] [소스 경로]	// 로컬의 파일 hdfs 상으로 복사
* hadoop fs -rm [소스 경로]		// 파일 삭제, 폴더는 삭제 안됨
* hadoop fs -rmr [소스 경로]		// 폴더 삭제
* hadoop fs -setrep [값] [소스 경로]	// hdfs 의 replication 값 수정
* hadoop fs -text [소스 경로]   // 파일의 정보를 확인하여 텍스트로 반환 (gz, lzo 같은 형식을 확인후 반환해줌)
