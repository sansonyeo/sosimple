---
title: "Oracle v. Google, 10년 자바 전쟁의 결말"
excerpt_separator: "<!--more-->"
categories:
  - Research
tags:
  - IT
  - google
  - oracle
  - java
  - 저작권
---

> 본 글은 사내 게시판에 공유한 글에 약간의 살을 붙이고 다듬어 옮긴 것입니다.

<!--more-->

{% include toc %}

# 자바 전쟁에 대하여

## 누가 왜 시작했는가?

`10년 자바 전쟁`으로 불리기도 하는 이 소송은 오라클이 구글을 제소하면서 시작했습니다.  
구글이 안드로이드를 개발하면서 자바를 가져다 쓴 것이 계기가 되었는데요,  
자바는 썬마이크로시스템즈가 개발했으며, 오라클은 2010년에 썬마이크로시스템즈를 인수했습니다.  

이 소송의 쟁점은 크게 두 가지입니다.

1. 오라클에게 자바 API의 **저작권**이 있는가?
2. 구글의 Java API 사용은 **공정 이용(fair use)**으로 볼 수 있는가?

이중 1번은 이미 오라클에게 저작권이 있다고 결론이 났고, 2번에 대해 판결을 기다리던 상황이었습니다.  
보다 자세한 히스토리는 본 글 하단에 있는 [타임라인](#타임라인)을 참고해주세요.

## 공정 이용(fair use)이란?

간단히 말해, `저작권이 있는 저작물이라고 해도, 저작권 침해 혐의로부터 면제받을 수 있는 예외 경우`라고 설명할 수 있습니다.  
미국 저작권법 107조에서 규정하고 있는 독특한 조항이며, 판단 기준은 다음과 같습니다.

1. 이용의 목적과 성격 <span class="comment">(비영리 목적이나 보도, 학술 인용)</span>
2. 저작물의 특성
3. 이용 분량 및 전체 저작물에서 어느 정도로 핵심적인 부분인지 여부
4. 저작물 이용이 시장에 미치는 영향

# 자바 전쟁의 결말

이 소송은 2020년 이내에 마무리될 것으로 보였으나, COVID-19로 인해 판결이 지연되었습니다.  
예상한 것보다 몇 달의 시간이 지나고 드디어! 지난 4월 5일<span class="comment">(미국 현지 시간 기준)</span> 판결이 났습니다.

"자바는 오라클에게 저작권이 있다. 그러나 구글의 Java API 사용은 공정 이용(fair use)으로 본다."
{: .notice--info}

공정 이용으로 인정됨에 따라, 구글은 배상의 책임을 면하게 되었습니다.  
또한 판결을 기다리던 안드로이드 생태계 및 소프트웨어 업계 전반에도 평화가 찾아오게 되었습니다.

*마이크로소프트(MS) 같은 기업이나 전자프론티어재단(EEF) 같은 시민단체들은 API까지 저작권의 대상으로 삼을 경우 소스 코드를 기반으로 소프트웨어를 개발하는 관행을 바꿔야 할 가능성이 높고, 개발자 커뮤니티가 직접 영향을 받을 것으로 우려하여 구글을 지지하던 상황이었습니다.*

# 판결 근거

공정 이용으로 인정한 근거에 대해서는 CIO Korea에서 게시한 기사를 통해 짐작할 수 있습니다.

* 출처: <a href="https://www.ciokorea.com/news/189053" target="_blank">CIO Korea, <구글, 오라클과의 ‘자바 분쟁’서 승소…미 연방대법원 "공정 이용" 최종 판결></a>

연방대법원은 최종 판결에서 "컴퓨터 프로그램은 원래부터 기능적(functional)이기 때문에 전통적인 저작권 개념을 적용하기가 어렵다"라고 말했다. <span class="comment">(중략)</span>
연방대법원은 구글이 안드로이드를 개발하는 과정에서 자바SE, 특히 자바 API에서 약 1만 1,500줄의 코드를 차용했다고 설명했다. 그러나 해당 API의 코드 286만줄 중 0.4%에 불과하다는 점을 최종 판결에 참작했다고 덧붙였다.
{: .notice--info}

`나는 전체 판결문이 궁금하다!` 하는 분은 아래의 판결문 링크를 눌러주세요.  

* 판결문: <a href="https://www.supremecourt.gov/opinions/20pdf/18-956_d18f.pdf" target="_blank">https://www.supremecourt.gov/opinions/20pdf/18-956_d18f.pdf</a>

# 타임라인

이 사건이 항소와 상고를 거듭하며 10년이나 갈 줄 누가 알았을까요?  
복잡한 이 10년 전쟁의 타임라인을 최대한 간략하게 정리해보았습니다.

* 2005년. Google, Sun Microsystems와 자바 이용 협상 결렬
* 2007년. Google, 37개 자바 API 일부 복제해 Android 플랫폼 출시
* 2009년. Oracle, Sun Microsystems 인수
* 2010년, Oracle이 Google에 저작권, 특허 소송 제기
* **2012년, 1심 Google 승, Oracle 항소**
    * 저작권은 "공정 이용"으로 면책, 특허는 무혐의
* **2014년, 2심 Oracle 승, Google 상고**
    * 37개 Oracle 자바 API 저작권 인정
    * 단, Android 플랫폼에서 자바 API를 사용한 것이 "공정 이용(fair use)" 에 해당되는지 다시 논의하라고 판결
    * 소송이 두 개로 나뉨: `(1) 저작권 침해` / `(2) 공정 이용`
    * `(1) 저작권 침해` 관련하여 Google이 상고신청
* **2015년, 연방대법원이 Google 상고 기각**
    * `(1) 저작권 침해`에 대해서는 Oracle 측의 승리로 종료
* **2016년, 파기환송심 Google 승, Oracle 항소**
    * `(2) 공정 이용` 관련으로, Google의 자바 API 사용은 "공정 이용(fair use)" 이라 판결
* **2018년 3월 항소법원, Oracle 승, Google 연방대법원에 상고 신청**
    * 구글의 자바 API 이용은 공정이용으로 인정할 수 없다고 판결
* 2020년, 연방대법원이 Google의 상고를 받아들여 상고심 소송 진행
    * COVID-19로 인해 지연
* **2021년 4월, Google 승**
    * 구글이 안드로이드에 자바 API를 사용한 것은 ‘공정 이용’에 해당된다면서 구글의 저작권 침해를 인정할 수 없다고 판결

# 참고

## 관련기사

ZDNet Korea에서 관련 기사를 잘 묶어 정리했습니다. 그 중 일부를 소개합니다.

* <a href="https://zdnet.co.kr/view/?no=20210406064737" target="_blank">구글, '10년 자바전쟁' 오라클에 최종 승리 (2021년 4월)</a>
* <a href="https://zdnet.co.kr/view/?no=20201007155645" target="_blank">구글/오라클, 물량공세로 '자바전쟁' 우군 모았다 (2020년 10월)</a>
* <a href="https://zdnet.co.kr/view/?no=20200709164139" target="_blank">코로나19로 밀린 자바전쟁, 어떻게 되고 있나 (2020년 7월)</a>
* <a href="https://zdnet.co.kr/view/?no=20200221153253" target="_blank">구글-오라클 자바전쟁... 美 정부 "오라클 지지" (2020년 2월)</a>
* <a href="https://zdnet.co.kr/view/?no=20180328163651" target="_blank">'자바전쟁' 패배한 구글, 어떤 선택할까? (2018년 3월)</a>
* <a href="https://zdnet.co.kr/view/?no=20160527090535" target="_blank">'자바 늪' 벗어난 구글... 공정이용 뭐길래? (2016년 5월)</a>

## Android 플랫폼이 사용한 Java API 37개 목록

* java.awt.font
* java.beans
* java.io
* java.lang
* java.lang.annotation
* java.lang.ref
* java.lang.reflect
* java.net
* java.nio
* java.nio.channels
* java.nio.channels.spi
* java.nio.charset
* java.nio.charset.spi
* java.security
* java.security.acl
* java.security.cert
* java.security.interfaces
* java.security.spec
* java.sql
* java.text
* java.util
* java.util.jar
* java.util.logging
* java.util.prefs
* java.util.regex
* java.util.zip
* javax.crypto
* javax.crypto.interfaces
* javax.crypto.spec
* javax.net
* javax.net.ssl
* javax.security.auth
* javax.security.auth.callback
* javax.security.auth.login
* javax.security.auth.x500
* javax.security.cert
* javax.sql
