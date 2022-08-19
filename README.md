# mac-setting

## Homebrew

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Homebrew 설정

```sh
brew intall git
brew install fnm
brew install npm
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

Dracula.itermcolors 파일 클릭 후 iTerm2에서 설정 - Colors - Dracula 변경

### 폰트 설치
```sh
brew tap homebrew/cask-fonts

brew install --cask font-jetbrains-mono
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

## Hammerspoon

Hammersppon을 설치한다.

이후 `.hammerspoon` 폴더에 다음과 같은 파일을 만든다.

```sh
vi init.lua

mkdir modules
# modules
vi inputsource_aurora.lua
```

상세 설정은 [다음](https://github.com/DavidYang2149/hammerspoon-config)을 참조한다.

추가로 한영 전환 설정은 [다음](https://www.philgineer.com/2021/01/m1-hammerspoon.html)을 참조한다.

## Git

(선행조건) brew install git

```sh
brew install gpg
```

```sh
# .gitconfig

```

```sh
# .gitmessage.txt

```

## GPG

https://www.44bits.io/ko/post/add-signing-key-to-git-commit-by-gpg

