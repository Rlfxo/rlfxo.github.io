---
title: Error - The current runner was detected as self-hosted because the platform does not match a GitHub-hosted runner image
author: Rlfxo
date: 2024-10-15 13:42:00 +0900
categories: [Blog]
tags: [JEKYLL, ERROR]
pin: false
image:
  path: /img/241015/solv0.png
---

## Main Title
> Run ruby/setup-ruby@8575951200e472d5f2d95c625da0c7bec8217c42  
Error: The current runner (ubuntu-24.04-x64) was detected as self-hosted because the platform does not match a GitHub-hosted runner image (or that image is deprecated and no longer supported).

### Related Link
[Failed in ubuntu-24.04 runner](https://github.com/ruby/setup-ruby/issues/595)

#### Contents

1. [Issue](#1-issue)
2. [Solution](#2-solution)

### 1. Issue
![img1](/img/241015/prov1.png){: .normal }

Jekyll을 이용해 GitHub 블로그를 편집한 후, "Deploy Jekyll site to Pages" 과정에서 빌드 실패 문제가 발생하였다.

![img2](/img/241015/prov2.png){: .normal }

GitHub Actions에서 빌드 에러의 원인을 조사하고, 해결 방법을 검색하였다.

### 2. Solution

링크된 이슈에서 설명된 대로, 문제는 `Faild in ubuntu-24.04 runner`로 인해 발생하였으며, 이는 루비(Ruby) 버전이 오래되어 발생한 오류였다.

![img3](/img/241015/solv0.png){: .normal }

이를 해결하기 위해 `.github` 폴더 내 워크플로우 파일에서 Ruby 설정을 `v1.161.0`에서 `v1.195.0`으로 수정하였다.

![img4](/img/241015/solv1.png){: .normal }

수정 후, Jekyll 사이트를 GitHub Pages에 정상적으로 배포할 수 있었으며, 문제가 해결되었음을 확인하였다.

---