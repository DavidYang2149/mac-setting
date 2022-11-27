# mac-setting

## Homebrew

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Warning: /opt/homebrew/bin is not in your PATH 메세지가 나타나는 경우
echo 'export PATH=/opt/homebrew/bin:$PATH' >> ~/.zshrc
```

### Homebrew 설정

```sh
brew install git
brew install fnm
brew install npm
brew install neovim
brew install gpg
brew install gitmoji

brew tap johngrib/homebrew-johngrib
brew install fav

brew install fzf

brew install localtunnel
# localtunnel 사용법 예시
# lt --port 3000 --subdomain david

# python 
brew install pyenv

brew install mongosh

# node canvas 설치 방법
npm install -g node-gyp
brew install pkg-config cairo pango libpng jpeg giflib librsvg pixman

# 이제 필요한 곳에서 하단 canvas를 설치할 수 있다
# npm install canvas
```

## iTerm2

[iTerm2](https://iterm2.com/) 다운로드

### oh my zsh 설치

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### iTerm2 설정

```sh
brew install zsh-syntax-highlighting
brew install zsh-autosuggestions
```

### .zshrc

```sh
# zsh Name Setting
prompt_context() {
  if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
    prompt_segment black default "%(!.%{%F{yellow}%}.)$USER"
  fi
}

# zsh Highlighting Setting
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# zsh autosuggestions
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh


# Homebrew PATH
export PATH=/opt/homebrew/bin:$PATH

# VSCode Setting - Command: code .
export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"

# NEOVIM
alias vi='nvim'
alias vim='nvim'
alias vimdiff='nvim -d'
export EDITOR='/usr/local/bin/nvim'

# git
alias gpso='git push --set-upstream origin'

# fnm
eval "$(fnm env --use-on-cd)"

# gpg
export GPG_TTY=$(tty)

# fav
source $(which fav.sh)

# python
if which pyenv > /dev/null; then
    eval "$(pyenv init --path)"
    eval "$(pyenv init -)"
fi

```

### .oh-my-zsh/themes/agnoster.zsh-theme

줄바꿈 설정

```sh
build_prompt() {
  RETVAL=$?
  prompt_status
  prompt_virtualenv
  prompt_context
  prompt_dir
  prompt_git
  prompt_bzr
  prompt_hg
  prompt_newline # 새로 추가하기
  prompt_end
}

# 하단 코드 추가하기
prompt_newline() {
  if [[ -n $CURRENT_BG ]]; then
    echo -n "%{%k%F{$CURRENT_BG}%}$SEGMENT_SEPARATOR
%{%k%F{blue}%}$SEGMENT_SEPARATOR"
  else
    echo -n "%{%k%}"
  fi
  echo -n "%{%f%}"
  CURRENT_BG=''
}
```

### 드라큘라 테마 설치

```sh
# downloads 폴더 위치
git clone https://github.com/dracula/iterm.git
```

Dracula.itermcolors 파일 클릭 후, iTerm2에서 설정 - Profiles - Colors - Dracula 변경

### 폰트 설치
```sh
brew tap homebrew/cask-fonts
brew install --cask font-jetbrains-mono
```

폰트 설치 완료 후, iTerm2에서 설정 - Profiles - Text - Font - JetBrains Mono 변경

### fnm

```sh
# 사용법
# fnm use {버전}
```

### neovim

```sh
brew install neovim
```

상세 설정은 다음과 같다.

```sh
mkdir ~/.config/nvim
touch ~/.config/nvim/init.vim
```

### spacevim

설치 및 설정하기

```sh
curl -sLf https://spacevim.org/install.sh | bash
# 설치 완료 후 vim 실행 & 에디터로 접속하면 플러그인을 자동 설치한다
```

에디터를 사용하면서 문제가 생길 경우 vi로 접속하여 다음을 실행해본다.

```vi
# vi 접속
:checkhealth
```

### python

설정하기

```sh
 # 설치가 안되었다면 다음과 같이 할 것
brew install pyenv

 # 업그레이드
brew upgrade pyenv

 # 버전 확인
pyenv --version
```

이후 `.zshrc`에서 다음과 같이 설정한다.

```sh
# python
if which pyenv > /dev/null; then
    eval "$(pyenv init --path)"
    eval "$(pyenv init -)"
fi
```

설치 및 버전 관리하기

```sh
# 설치 가능한 버전 확인
pyenv install --list

 # 3.10.8 버전 설치
pyenv install 3.10.8

 # 3.10.8 버전을 사용한다
pyenv global 3.10.8

 # 3.10.8 버전 삭제
pyenv uninstall 3.10.8

 # 설치된 버전들 확인
pyenv versions
```

## Hammerspoon

Hammerspoon을 [설치](https://www.hammerspoon.org/)한다.

이후 `.Hammerspoon` 폴더에 다음과 같은 파일을 만든다.

```sh
cd .Hammerspoon
vi init.lua

# 직접 설정
mkdir modules
# modules
vi inputsource_aurora.lua

# 혹은 하단 상세 설정을 참조
```

상세 설정은 [다음](https://github.com/DavidYang2149/hammerspoon-config)을 참조한다.

추가로 한영 전환 설정은 [다음](https://www.philgineer.com/2021/01/m1-hammerspoon.html)을 참조한다.

## Git

```sh
# 선행조건
brew install git
brew install gpg
```

```sh
# .gitconfig

```

```sh
# .gitmessage.txt

# --- 제목(title) - 50자 이내로 ---
# <타입(type)> <제목(title)>
# 예시(ex) : Docs(Add) Commit docs Add
# --- 본문(content) - 72자마다 줄바꾸기  ---
# 예시(ex) :
# - Workflow
# 1. 커밋 메시지에 대한 문서 제작 추가.
# 2. commit message docs add.
# --- 꼬리말(footer) ---
# <타입(type)> <이슈 번호(issue number)>
# 예시(ex) : Fix #122
# --- COMMIT END ---
# <타입> 리스트
#   init    : 초기화
#   add     : 기능 추가
#   update  : 기능 보완 (업그레이드)
#   fix     : 버그 수정
#   refactor: 리팩토링
#   style   : 스타일 (코드 형식, 세미콜론 추가: 비즈니스 로직에 변경 없음)
#   docs    : 문서 (문서 추가(Add), 수정, 삭제)
#   test    : 테스트 (테스트 코드 추가, 수정, 삭제: 비즈니스 로직에 변경 없음)
#   chore   : 기타 변경사항 (빌드 스크립트 수정 등)
# ------------------
```

## GPG

https://www.44bits.io/ko/post/add-signing-key-to-git-commit-by-gpg

