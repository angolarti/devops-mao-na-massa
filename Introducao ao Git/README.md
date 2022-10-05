# Git

- Definir a branch principal global

```bash
git config --global init.defaultBranch main
```

- Criar repositório

```bash
git init
```

- Definir a branch do projecto

```bash
git branch -m main
```

- Adicionar mudanças para o stage de commit

```bash
git add files
```

- Salvar mudanças no repositório locaç

```bash
git commit -m "msg" files
```

- Sincronizar repositório local com  o remoto

```bash
git remote add origin https://github.com/angolarti/devops-mao-na-massa.git
```

- Enviar mudança para repositório remoto

```bash
git push -u origin main
```

## Criar um token de acesso pessoal

- Acessa o github
- Settings
- Developer Settings
- Personal access tokens
- Generate new token

## Adicionar suporte ao lfs - Large File Support

```bash
sudo pacman -S git-lfs
```

- Activar no projecto

```bash
git lfs install Git LFS initialized.
```

- Clone projecto com LFS

```bash
git lfs clone <repo>
```

- Pull com LFS

```bash
git lfs pull
```

- Speeding up pulls

```bash
git -c filter.lfs.smudge= -c filter.lfs.required=false pull && git lfs pull
```

- Criar alias

```bash
git config --global alias.plfs "\!git -c filter.lfs.smudge= -c filter.lfs.required=false pull && git lfs pull"
git plfs
```

~ Tracking files with Git LFS

```bash
git lfs track "*.ogg"
```

```bash


# track all .ogg files in any directory
$ git lfs track "*.ogg"

# track files named music.ogg in any directory
$ git lfs track "music.ogg"

# track all files in the Assets directory and all subdirectories
$ git lfs track "Assets/"

# track all files in the Assets directory but *not* subdirectories
$ git lfs track "Assets/*"

# track all ogg files in Assets/Audio
$ git lfs track "Assets/Audio/*.ogg"

# track all ogg files in any directory named Music
$ git lfs track "**/Music/*.ogg"

# track png files containing "xxhdpi" in their name, in any directory
$ git lfs track "*xxhdpi*.png
```

```bash
git add .gitattributes
```

```bash
git lfs untrack "*.ogg"
```

- Moving a Git LFS repository between hosts

```bash
# create a bare clone of the GitHub repository
$ git clone --bare git@github.com:kannonboy/atlasteroids.git
$ cd atlasteroids

# set up named remotes for Bitbucket and GitHub
$ git remote add bitbucket git@bitbucket.org:tpettersen/atlasteroids.git
$ git remote add github git@github.com:kannonboy/atlasteroids.git

# fetch all Git LFS content from GitHub
$ git lfs fetch --all github

# push all Git and Git LFS content to Bitbucket
$ git push --mirror bitbucket
$ git lfs push --all bitbucket
```
