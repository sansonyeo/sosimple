---
title: "[GitHub Pages] So Simple 테마를 통해 구조 살피기"
excerpt: "> 지킬 테마 중 하나인 So Simple 테마를 통해 구조 및 기본 설정 방법을 살펴봅니다."
categories:
- Experience
tags:
  - GitHub Pages
  - blog
  - jekyll
  - IT
last_modified_at: 2021-04-19 09:52:00 +0900
---

GitHub Pages 삽질기 두 번째 글이다. 이번 글에서는 `Jekyll`<span class="comment">(이하 **지킬**로 칭함)</span> 기반 사이트의 구조와 기본적인 설정을 하는 방법을 기술하고자 한다.

본 글은 제가 2021년 4월 현재 사용하고 있는 So Simple 테마를 예시로 사용합니다.<br>
<a href="https://github.com/mmistakes/so-simple-theme" target="_blank">[링크] So Simple Jekyll Theme</a>
{: .notice--warning}

{% include toc %}

# 지킬 사이트 공식 문서 (한국어)

So Simple 테마를 예시로 설명하기 전에 지킬 공식 사이트의 문서를 소개한다.  
일반적인 내용에 대해서는 아래 링크를 참고하면 좋다. 모두 한국어 사이트로 링크를 걸었다.

- <a href="https://jekyllrb-ko.github.io/docs/step-by-step/01-setup/" target="_blank">[링크] 단계별 튜토리얼</a>
  - 설명만 읽기보다는 기초부터 따라하면서 배워보고 싶으면 이쪽을 추천한다.
  - 테마를 적용하지 않고 루비만 설치한 상태에서 시작해야 한다.
- <a href="https://jekyllrb-ko.github.io/docs/configuration/" target="_blank">[링크] 환경설정</a>
- <a href="https://jekyllrb-ko.github.io/docs/structure/" target="_blank">[링크] 디렉토리 구조</a>
- <a href="https://jekyllrb-ko.github.io/docs/variables/" target="_blank">[링크] 변수</a>
- <a href="https://jekyllrb-ko.github.io/docs/themes/" target="_blank">[링크] 지킬 테마에 대하여</a>

# So Simple 테마

사실 이 테마는 가이드 문서가 매우 잘 만들어져 있다. 하지만 영어로 되어 있기도 하고, 읽는 것만으로는 완전히 이해하기는 어려운 점이 좀 있어서 헤메기도 했다. 그 삽질 이야기를 이 글을 통해 정리해보고자 한다.  
아래 링크의 문서, 사이트를 참고삼아 같이 보면 좋다.

- <a href="https://mmistakes.github.io/so-simple-theme/" target="_blank">[링크] So Simple 테마의 데모 사이트</a>
- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/README.md" target="_blank">[링크] So Simple 테마 가이드 문서</a>

## 구조(Structure)

So Simple 테마는 아래와 같은 디렉토리 및 파일로 구성되어 있다.

```
├── _data               # data files
|  ├── navigation.yml   # navigation bar links
|  └── text.yml         # theme text
├── _includes           # theme includes
├── _layouts            # theme layouts (see below for usage)
├── _sass               # Sass partials
├── assets
|  ├── css
|  |  └── main.scss
|  └── js
|     └── main.min.js
├── _config.yml         # sample configuration
└── index.md            # sample home page (recent posts/not paginated)
```

- 출처: <a href="https://github.com/mmistakes/so-simple-theme/blob/master/README.md#structure" target="_blank">[링크] So Simple 가이드 문서 중 Structure 항목</a>

가이드 문서에 있는 내용에 따르면 `_data`, `_includes`, `_layouts` 및 `_sass`의 디렉토리와 파일들은 기본 위치<span class="comment">(default location)</span>에 위치한다고 한다. 지킬 공식 사이트에 있는 <a href="https://jekyllrb-ko.github.io/docs/structure/" target="_blank">`디렉토리 구조`</a> 내용과 비교해보면 실제로 그러하다는 걸 알 수 있다. 각 디렉토리에 대한 설명도 그곳에서 찾을 수 있으니 여기서는 내가 이 테마를 뜯어보다가 깨달은 내용으로 적어본다.

- `_layouts`: 말 그대로 큰 뼈대이다.
- `_includes`: _layouts 디렉토리에 있는 파일들은 _includes 디렉토리에 있는 파일들로 구성되어 있다.
- `_sass`: 각 html 파일에 있는 class의 스타일 정의는 _sass 디렉토리에 있는 파일들에서 찾을 수 있다.

*(참고) 테마를 커스터마이즈 하려면 `_layouts`, `_includes`, 그리고 `_sass` 디렉토리의 파일들을 수정해야 하는 경우가 많다.*
{: .notice--accent}

## 기본 설정

So Simple 가이드 문서에도 적혀있듯이, 최소 4개의 파일을 수정해야 한다.

- `_config.yml`
- `_data/navigation.html`
- `_data/text.yml`
- `index.md`

### _config.yml

전반적인 환경설정 정보를 담고 있는 파일이다. 그래서 가장 고칠 게 많다.  
하지만 파일 내에 주석으로 간략한 설명이 있고, 가이드 문서도 잘 되어 있으니 참고하면 된다.  
지킬 공식 사이트에 있는 <a href="https://jekyllrb-ko.github.io/docs/configuration/" target="_blank">`환경설정`</a> 문서도 도움이 될 것이다.

- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/README.md#configuring" target="_blank">[링크] So Simple 가이드 문서 중 Configuring 항목</a>

설명으로 부족하거나 이해되지 않는다면 예시를 보는 게 도움이 된다.

- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/example/_config.yml" target="_blank">[링크] So Simple 데모 사이트의 _config.yml</a>
- <a href="https://github.com/olvimama/olvimama.github.io/blob/master/_config.yml" target="_blank">[링크] 본 사이트의 _config.yml</a>
  - `by olvi`로 검색하면 내가 수정한 내용을 알 수 있다.
  - 변경한 내용 중 일부는 아래 [문제 해결](#문제-해결)에서 보다 상세히 설명한다. 단, `google_fonts`와 `google_analytics` 관련해서는 별도의 글에서 다룬다.
  - 댓글은 비허용으로 두고자 `disqus` 항목은 사용하지 않았다.

### _data/navigation.yml

GNB<span class="comment">(Global Navigation Bar)</span> 설정 파일이라고 볼 수 있다.  
내 경우는 다음의 절차에 따라 수정했다.

1. So Simple 데모 사이트의 navigation 파일을 그대로 복사
2. 사용하지 않을 메뉴는 주석처리
3. 첫 화면으로 이동하는 `Home` 메뉴를 추가
4. 포스트, 카테고리, 태그 메뉴의 메뉴명(`title`)과 경로(`url`) 수정

아래 링크를 통해 원본과 본 사이트의 차이를 확인할 수 있다.

- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/example/_data/navigation.yml" target="_blank">[링크] So Simple 데모 사이트의 navigation.yml</a>
- <a href="https://github.com/olvimama/olvimama.github.io/blob/master/_data/navigation.yml" target="_blank">[링크] 본 사이트의 navigation.yml</a>

*두 링크의 내용을 비교해보면 `title` 및 `url` 값이 다르다. 이에 대해서는 아래 [404 error](#404-error)에서 설명한다.*
{: .notice--accent}

사이트 내부에 생성할 메뉴는 루트<span class="comment">(root)</span> 디렉토리에 해당 md 파일도 만들어줘야 한다. 본 사이트의 경우는 다음의 md 파일이 존재한다.

- `categories.md` : GNB의 CATEGORY 메뉴에 해당
- `posts.md` : GNB의 POST 메뉴에 해당
- `search.md` : GNB의 SEARCH 메뉴에 해당
- `tags.md` : GNB의 TAG 메뉴에 해당

### _data/text.yml

각 언어에 따른 문자열<span class="comment">(string)</span>을 설정하는 파일이다. 테마 내에서 나오는 단어를 변수화하고, 각 변수를 영어, 독일어, 스페인어 등등 언어에 따른 정의를 한다. 그래서 `_config.yml` 파일에 있는 `locale` 설정에 따라 그에 맞는 단어가 보인다고 생각하면 된다.

꼭 언어별 설정을 하지 않더라도 코드 내에는 최대한 문자열을 바로 넣지 않고 이 파일 내에서 변수화하는 편이 좋다. 그 이유는 훗날 테마 커스터마이징을 다루는 글에서 소개하도록 하겠다.

- <a href="https://github.com/olvimama/olvimama.github.io/blob/master/_data/text.yml" target="_blank">[링크] 본 사이트의 text.yml</a>

내 경우는 `_config.yml` 파일의 `locale` 값을 `ko-KR`로 했다. 하지만 `text.yml` 파일에 한국어 설정을 별도로 하지는 않았고, 아래와 같이 영어를 따르게 했다.

```yml
# _data/text.yml
ko-KR:
  <<: *DEFAULT_EN
```

### index.md

홈 화면, 즉 가장 처음에 보이는 화면에 대해 정의하는 파일이다.  
내 경우는 페이지 나누기<span class="comment">(pagination)</span> 이슈 때문에 `md` 파일이 아닌 `html` 파일로 구성했다.

- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/index.md" target="_blank">[링크] So Simple 테마의 기본 index.md</a>
- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/example/index.html" target="_blank">[링크] So Simple 데모 사이트의 index.html</a>
- <a href="https://github.com/olvimama/olvimama.github.io/blob/master/index.html" target="_blank">[링크] 본 사이트의 index.html</a>

세 파일을 비교해보면 `paginate` 값을 `true`로 정의한 경우 `html` 파일로 한다는 걸 알 수 있다. 이에 대한 보다 자세한 내용은 아래 [페이지 나누기](#페이지-나누기)에서 설명한다.

# 문제 해결

기본 설정을 적용하다가 겪은 문제와 해결법을 소개한다.

## 404 error

GNB 메뉴를 변경하다 만난 에러로, `_config.yml` 파일 중 `Taxonomy pages` 관련 내용이다. 우선 가이드 문서를 보자.

> By default, category and tags added to a post are not linked to taxonomy archive pages. To enable this behavior and link to pages with posts grouped by category or tag, add the following:

- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/README.md#taxonomy-pages" target="_blank">[링크] So Simple 가이드 문서 중 Taxonomy Pages 항목</a>

가이드 문서에서 알 수 있듯이, 카테고리 및 태그 모음 페이지는 기본적으로 생성되지 않고 수동으로 만들어야 한다. So Simple 테마의 경우는 가이드 문서와 동일한 링크를 갖고 있다.

```yml
# So Simple 데모의 _config.yml
category_archive_path: "/categories/#"
tag_archive_path: "/tags/#"
```

- 데모 사이트의 카테고리 모음 url: `https://mmistakes.github.io/so-simple-theme/categories/`
- 데모 사이트의 태그 모음 url: `https://mmistakes.github.io/so-simple-theme/tags/`

하지만 본 사이트의 경우는 단수형으로 사용했다.

```yml
# 본 사이트의 _config.yml
category_archive_path: "/category/#"
tag_archive_path: "/tag/#"
```

- 본 사이트의 카테고리 모음 url: `https://olvimama.github.io/category/`
- 본 사이트의 태그 모음 url: `https://olvimama.github.io/tag/`

영어권에서는 이런 경우 일반적으로 복수형을 쓴다는 것은 알지만, 한국인 입장에서는 사전상에서 보이는 단수형 단어를 쓰는 게 더 친숙하다는 점 때문에 이와 같이 변경한 것이었다. 그런데 처음에 이렇게 바꾸고 사이트를 들어가보니 `404 Not Found` 에러가 발생했다.

그 이유는 내가 가이드를 제대로 읽지 않은 탓이었다. 가이드의 아래 내용을 다시 한 번 읽어보자.

> These paths should mimic the permalinks used for your categories and tags archive pages. The # at the end is necessary to target the correct taxonomy section on the pages.

즉, `_config.yml` 파일에서 `category_archive_path` 및 `tag_archive_path`를 본인이 원하는대로 바꾸었다면, `_data/navigation.yml`, `categories.md`, `tags.md` 파일에 있는 경로도 바꿔야 한다.  
같은 맥락에서 `_data/navigation.yml` 파일에서 내가 원하는 url 값을 정의했다면, 그 url 값에 맞게 관련된 경로 또한 변경해야 한다.

```yml
# 본 사이트의 _data/navigation.yml
- title: Post
  url: /post/
- title: Category
  url: /category/
- title: Tag
  url: /tag/

# 본 사이트의 posts.md
layout: posts
permalink: /post/

# 본 사이트의 categories.md
layout: categories
permalink: /category/

# 본 사이트의 tags.md
layout: tags
permalink: /tag/
```

요약하면 다음 항목의 값<span class="comment">(경로)</span>를 동일하게 해야 한다.

1. 카테고리
   - **category_archive_path** (_config.yml)
   - `title: {카테고리}`의 **url** (navigation.yml)
   - **permalink** (categories.md)
2. 태그
   - **tag_archive_path** (_config.yml)
   - `title: {태그}`의 **url** (navigation.yml)
   - **permalink** (tags.md)
3. 포스트
   - `title: {포스트}`의 **url** (navigation.yml)
   - **permalink** (posts.md)
4. 검색
   - `title: {검색}`의 **url** (navigation.yml)
   - **permalink** (search.md)

## 페이지 나누기

`_config.yml` 파일 중 `Pagination` 관련 내용이다.

우선 pagination이 뭔지 설명하자면 말 그대로 페이지 나누기로 이해하면 된다. 사이트에 많은 글이 있는 경우 한 화면에 너무 많은 글을 보여주는 걸 피하기 위해 한 페이지 당 특정 개수의 글만 보여주는 식으로 정의하고, 특정 개수를 넘어가면 다른 페이지에서 보여주는 식이다.

- <a href="https://jekyllrb-ko.github.io/docs/pagination/" target="_blank">[링크] 지킬 공식 사이트의 `페이지 나누기` 문서</a>
- <a href="https://github.com/mmistakes/so-simple-theme/blob/master/README.md#pagination" target="_blank">[링크] So Simple 가이드 문서 중 Pagination 항목</a>

지킬 공식 사이트의 문서에 따르면 **"페이지 나누기는 오직 HTML 파일에서만 작동합니다"** 라고 강조하고 있다. 그래서 pagination을 적용한 So Simple 데모 사이트나 본 사이트의 경우 `index.md`가 아닌 `index.html` 파일로 초기 화면을 구성한 것이다.

가이드 문서에 보면 `Gemfile`, `_config.yml`, 그리고 `index.html` 등 세 개의 파일을 수정하라고 하는데 그대로 하면 되고, 만약을 대비하여 `_config.yml` 파일 중 `plugins` 항목에 `jekyll-paginate` 값이 있는지 또한 확인해봐야 한다.

```yml
# Gemfile
group :jekyll_plugins do
  gem "jekyll-paginate"
end
```
- <a href="https://github.com/olvimama/olvimama.github.io/blob/master/Gemfile" target="_blank">[링크] 본 사이트의 Gemfile</a>

```yml
# _config.yml
paginate: 6
paginate_path: /page:num/
plugins:
  - jekyll-paginate
```
- <a href="https://github.com/olvimama/olvimama.github.io/blob/master/_config.yml" target="_blank">[링크] 본 사이트의 _config.yml</a>

```yml
# index.html
layout: home
paginate: true
```
- <a href="https://github.com/olvimama/olvimama.github.io/blob/master/index.html" target="_blank">[링크] 본 사이트의 index.html</a>

## 개별 글의 고유 url 정의

`_config.yml` 파일을 수정하던 중, 가이드 문서에서 찾지 못한 내용을 발견했다.

```yml
# So Simple 테마 _config.yml에 정의된 기본값
# Build settings
permalink: /:categories/:title/
```

`permalink` 값의 정체는 바로 특정 글의 url 값 정의였다. So Simple 테마의 경우 `https://{_config.yml에 정의한 url}/{해당 글의 카테고리}/{해당 글의 파일명에 있는 제목}` 식으로 정의된 것이다.

So Simple 데모 사이트를 통해 예를 들어보면 이해가 쉽다.

- **`Post: Future Date`**
  - 카테고리: `Post`
  - 파일명: `2010-10-25-post-future-date.md`
  - url: `https://mmistakes.github.io/so-simple-theme/post/post-future-date/`
- **`MathJax Example`**
  - 카테고리: 없음
  - 파일명: `2015-08-10-mathjax-example.md`
  - url: `https://mmistakes.github.io/so-simple-theme/mathjax-example/`

이를 깨달은 후 나는 개별 글에 어떤 url을 갖게 할까 고민했다. 그대로 둘까 생각하기도 했지만 아무래도 개별 글이 특정 카테고리에 속한 느낌을 주는 게 내키지 않았고, 그 글 자체로 독립적인 url을 갖기를 원하여 아래와 같이 바꾸었다.

```yml
# 본 사이트의 _config.yml
# Build settings
permalink: /blog/:title
```

위와 같이 정의하면 `https://olvimama.github.io/blog/{해당 글의 파일명에 있는 제목}` 형식으로 경로가 정의된다.

# GitHub Pages 관련글

- [[GitHub Pages] Mac 환경에서 첫 걸음 내딛기]({% post_url 2021-04-06-gitpages-the-1st-step %})
- 그 외 추가 등록 예정 :)