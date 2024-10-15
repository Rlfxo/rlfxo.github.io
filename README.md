# Rlfxo's Blog

## 환경 설정
```
which ruby # 현재 사용하는 ruby 확인 (rbenv)
bundle # gemfile 설치
npm install && npm run build # node 패키지 설치
jekyll serve # 로컬 서버 실행
```
> ruby 3.2 이상 사용
> node 설치 필요
- ruby env
  - brew install rbenv
  - rbenv install -l
  - rbenv install 3.2.5
  - rbenv global 3.2.5
  - vi ~/.zshrc
  - [[ -d ~/.rbenv ]] && export PATH=${HOME}/.rbenv/bin:${PATH} && eval "$(rbenv init -)"
  - source ~/.zshrc
- node
  - brew install node

#### commit lint
- build
- ci
- chore
- docs
- feat
- fix
- perf
- refactor
- revert
- style
- test