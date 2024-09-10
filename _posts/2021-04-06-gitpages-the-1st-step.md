---
title: "[GitHub Pages] Mac 환경에서 첫 걸음 내딛기"
excerpt: "> GitHub Pages를 선택한 이유, 지킬(Jekyll) 설치하기, 테마 선택, 로컬에서 테스트하는 방법까지"
categories:
- Experience
tags:
  - GitHub Pages
  - blog
  - troubleshooting
  - jekyll
  - IT
last_modified_at: 2021-04-18 18:24:00 +0900
---

GitHub Pages로 이 공간을 만들면서 많은 검색을 했다. 장단점이 무엇이냐부터 시작해서 세팅 과정, GA 적용 방법, 테마 수정하고 싶은데 CSS에서 막히는 부분이 있을 때 등등 별의 별 검색을 다 해보았다. 그러다보니 나도 기여를 해야겠다는 엉뚱한 생각이 들었다. 혹시 아는가? 누군가 GitHub Pages로 블로그 만들다가 막혀서 검색을 했는데 내 글이 도움이 될지. 그래서 나의 GitHub Pages 삽질기를 써보기로 결심했다. 이는 그 첫 번째 글이다.

본 글은 Mac에서의 트러블슈팅을 위주로 다루고자 합니다. 제가 참고한 내용에 대해서는 링크로 대체합니다.<br>
또한 독자는 git/GitHub와 shell에 대한 기본적인 지식이 있다고 가정하고 작성합니다.
{: .notice--warning}

{% include toc %}

# 왜 GitHub Pages 인가?

그 이유에 대해서는 이미 이 블로그의 [`첫 글`]({% post_url 2021-03-07-hello-world %})에 언급한 바 있다. 하지만 해당 글에는 다른 이야기도 섞여있고, 그 글에서 다루지 못한 내용도 있어 다시 정리해보면 다음과 같다:

- 댓글 기능을 별도로 추가해야 한다.
- <span class="comment">(댓글, SNS 공유 등 독자 반응에 대한)</span> 푸시가 오지 않는다.
- markdown, html 등으로 써야 한다.
- git 커밋 작업이 필요하다.
- 자체적으로 통계 기능을 제공하지 않아 별도로 구축해야 한다.
- 검색 노출을 원하면 각 엔진마다 세팅해줘야 한다.

위 특징은 주로 GitHub Pages 단점을 검색할 때 나오는 말이다. 그러나 나는 저런 허들(?)이 맘에 들어서 선택하게 됐다. 즉 나에게 저 특징들은 GitHub Pages가 갖고 있는 장점이었던 것이다. 결론적으로:

내가 손수 이런 저런 경험을 해보고 싶다면 GitHub Pages 만한 것이 없다.
{: .notice}

# GitHub Pages 시작하기

기본적인 내용은 아래 링크한 블로그에서 매우 잘 설명하고 있다. 나도 첫 시작은 저 링크를 보고 따라했다.

- <a href="https://thdev.net/644" target="_blank">[링크] Github 페이지를 이용하여 개인 페이지 구성하기</a>

사실 저 내용만 따라해도 그럴듯한 GitHub Pages가 완성이 되며, `난 더 이상 굳이 진행할 필요 없어!` 라고 생각하면 이 아래 내용을 보지 않아도 좋다.

# Jekyll 설치하기

사실 markdown을 이용해서 블로그 글을 작성하려면 `Jekyll`<span class="comment">(이하 **지킬**로 칭함)</span>이라는 것을 PC에 설치해야 한다. 지킬은 markdown을 웹 페이지로 생성해주는 역할을 한다고 생각하면 된다.

`아니 깃헙에서 이미 멀쩡히 잘 돌아가고 있는데 이걸 왜 내 PC에 설치해야 해?` 라고 생각할 수 있고 나도 처음에는 그렇게 생각했다. 그럼 지킬을 설치해야 하는 이유는 무엇인가? 내가 생각하는 가장 큰 이유는 이것이다.

작성한 글에 markdown 등의 오류가 있을 수 있다. 커밋 전 로컬에서 오류를 미리 확인하려면 내 PC에서 지킬이 돌아가야 한다.
{: .notice}

지킬의 매뉴얼이 포함된 공식 사이트는 <a href="https://jekyllrb.com/" target="_blank">https://jekyllrb.com/</a> 이다. 영어 사이트이지만 다행히 한국어 사이트도 있다.

- <a href="https://jekyllrb-ko.github.io/" target="_blank">[링크] jekyll 한국어 사이트</a>

지킬 v4.0.0을 기준으로 번역된 내용이고, 일부 페이지는 원본(영문)으로 나오지만 전반적으로 이해하는데 큰 무리는 없다. 지킬 설치 이후에도 블로그를 운영하다보면 참고할 일이 생기므로 즐겨찾기 해두기를 권장한다.

한국어 지킬 사이트에 들어가면 아래와 같은 내용이 눈에 띈다.

![image-center]({{ '/images/experience/2021-04-06-jekyll-quick-start.png' | relative_url }}){: .align-center}

사실 저게 전부다. 저 내용대로 아무 에러 없이 모든 게 잘 흘러가면 끝이다. 하지만 내 경우 약간의 문제를 겪었고 그 해결책을 공유하고자 하는 게 이 글을 쓰는 목적이니 소개하겠다. 나는 두 대의 맥북에 지킬을 설치했고, 서로 다른 두 유형의 permission error를 겪었다.

## 사례 1. sudo로 해결

```shell
$ gem install bundler jekyll
```

터미널을 열고 위와 같이 입력했는데 퍼미션 에러가 떴다. 루비 폴더에 쓰기 권한이 없단다.  
그래도 이 케이스는 해결이 간단하다. 무적의 `sudo`만 붙여주면 된다.

```shell
$ sudo gem install bundler jekyll
```

문제 해결!

## 사례 2. rbenv로 해결

다른 맥북에 설치할 때에는 아예 처음부터 sudo를 붙여서 실행했다. 그런데...? 순조로이 설치가 진행되는듯 했는데 이상한 에러가 난다.

```shell
$ gem install bundler jekyll
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.x.x directory.
```

해당 에러 메시지로 검색을 해보니 주로 코코아팟<span class="comment">(CocoaPods)</span> 에러 해결책이 나온다. 이런 류의 트러블슈팅을 몇 가지 시도해보았으나 되지 않았다.

결론적으로 성공한 방법은 `rbenv`를 통해 해결하는 것이었다. 이에 대해 간략히 설명하자면, 기본적으로 system ruby를 global ruby로 바라보고 있는데, rbenv를 통해서 별도 버전의 ruby를 global로 설정하여 위 문제를 회피할 수 있게 하는 것이다. 도움을 받은 링크는 아래와 같다.

- <a href="https://jojoldu.tistory.com/288" target="_blank">[링크] Mac에서 Gem::FilePermissionError 에러 발생시 해결 방법</a>

# Jekyll 테마

GitHub에서 몇 가지 테마를 적용해주긴 하지만 각자의 원하는 바를 백 퍼센트 만족하지는 못할 것이다. 물론 정말 백 퍼센트 만족시킬 테마는 없을 것이고 그런 것은 손수 만들어야 할 것이다. 내 경우는 가장 내 취향에 가까운 것을 고르고 조금씩 내 입맛에 맞게 커스터마이징하는 방법을 썼다.

## 테마 고르기

테마를 제공하는 대표적인 사이트는 다음과 같다. 들어가보면 너무 많아서 고르기 힘들 수도 있다.

- <a href="http://jekyllthemes.org/" target="_blank">http://jekyllthemes.org/</a>
- <a href="https://jekyllthemes.io/free" target="_blank">https://jekyllthemes.io/free</a>
- <a href="http://themes.jekyllrc.org/" target="_blank">http://themes.jekyllrc.org/</a>
- <a href="https://github.com/topics/jekyll-theme" target="_blank">https://github.com/topics/jekyll-theme</a>

이 중에 내가 고르고 적용한 테마는 `So Simple` 이라는 테마이며, 해당 테마의 git repository<span class="comment">(이하 **저장소**로 칭함)</span>는 <a href="https://github.com/mmistakes/so-simple-theme" target="_blank">https://github.com/mmistakes/so-simple-theme</a> 이다.

## 테마 적용하기

So Simple 테마의 저장소를 보면 설치하고 세팅하는 방법에 대해 매우 상세하게 알려주고 있다. 설치의 경우 `Ruby Gem Method`와 `GitHub Pages Method` 두 가지 방법을 가이드한다. 뭘 해야할지 모르는 상황에서 `나는 GitHub Pages를 만들었으니까!` 라는 단순한 생각으로 GitHub Pages Method를 시도했다.

1. GitHub Pages를 만든 저장소의 Settings에서 임의의 GitHub Pages 테마를 선택
2. 저장소 메인에 `_config.yml` 파일이 생성됨
3. 빈 파일을 하나 생성해서 `Gemfile`로 이름을 붙여주고 가이드대로 내용을 채움
    ```shell
    gem "github-pages", group: :jekyll_plugins
    ```
4. 2번의 `_config.yml` 파일에 역시 가이드대로 내용을 업데이트
    ```shell
    remote_theme: "mmistakes/so-simple-theme@3.2.0"
    ```

이렇게 하니 깔끔하게 적용된 모습을 확인할 수 있었다.

하지만 문제가 있었으니... 위 단계의 4번에서 보다시피 테마를 리모트로 적용하는 것이다보니 내 저장소에 있는 파일은 `Gemfile`, `_config.yml` 정도 밖에 없었다. 즉, 테마에 해당하는 파일들은 없다보니 내 입맛대로 커스텀하기 어렵겠다 생각이 들었다.

결론적으로 So Simple 테마의 저장소를 fork 했고, fork한 경우 지워야할 파일들<span class="comment">(해당 테마의 도움말을 참고했다)</span>을 정리한 후 현재의 블로그 테마를 유지하고 있다.
{: .notice}

내 GitHub Pages 저장소를 로컬 환경에 clone하고, Gemfile에 아래와 같은 내용으로 기입했다. 이는 So Simple 테마에 해당하므로 다른 테마를 이용중이라면 해당 테마의 매뉴얼을 살펴보고 적절한 내용으로 바꾸어줘야 한다.

```shell
gem "jekyll-theme-so-simple"
```

터미널에서 `$ bundle install` 실행하여 <span class="comment">(잘 안되면 당연히 앞에 sudo를 붙인다.)</span> gem을 설치한다. 성공했다면 로컬에서 테스트할 준비가 완료된다.

# 로컬 환경에서 테스트

설명이 필요 없다면 하위 제목 두 가지만 기억하면 된다.

## 터미널에서 bundle exec jekyll serve

로컬 테스트가 필요할 때마다 터미널에서 **저장소의 클론이 있는 디렉토리로 이동**해서 `$ bundle exec jekyll serve` 명령어를 입력한다. 아래는 내 로컬에서 실행했을 때의 모습이다.

```shell
$ bundle exec jekyll serve
Configuration file: /Users/olvikim/Documents/GitHub/olvimama.github.io/_config.yml
            Source: /Users/olvikim/Documents/GitHub/olvimama.github.io
       Destination: /Users/olvikim/Documents/GitHub/olvimama.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 0.752 seconds.
 Auto-regeneration: enabled for '/Users/olvikim/Documents/GitHub/olvimama.github.io'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```

위 메시지를 보면 지킬에서 사이트를 생성할 때 어떻게 돌아가는지 알 수 있는 점이 있다.

1. **설정에 관한 내용은 `_config.yml` 파일을 바라본다.**
2. **사이트를 생성하는 소스<span class="comment">(Source)</span>는 저장소의 클론이 있는 디렉토리이다.**<br>위 메시지에선 `/Users/olvikim/Documents/GitHub/olvimama.github.io`이다.
3. **로컬에서 가상으로 생성한 사이트 결과물은 저장소의 클론이 있는 디렉토리 하위에 `_site` 라는 디렉토리에 있다.**<br>위 메시지에선 `/Users/olvikim/Documents/GitHub/olvimama.github.io/_site`이다. 해당 디렉토리에 가서 어떻게 이뤄졌는지 여기저기 살펴보면 블로그 내의 문서 파일들은 md 파일이 아닌 html 파일로 생성된 걸 알 수 있다.

## 브라우저에서 http://localhost:4000

성공적으로 구동한 후에는 아래와 같이 사용하면 된다.

- `http://127.0.0.1:4000` 혹은 `http://localhost:4000` 으로 브라우저를 통해 들어간다.
- 만약 내가 만든 마크다운 파일에 문제가 있다면 터미널을 통해 에러 메시지가 출력된다.
- 또한 더 이상 작업할 내용이 없어 로컬 서버를 중지하려면 `ctrl-c`를 눌러 종료한다.

# GitHub Pages 관련글

- [[GitHub Pages] So Simple 테마를 통해 구조 살피기]({% post_url 2021-04-18-gitpages-about-so-simple-theme %})
- 그 외 추가 등록 예정 :)