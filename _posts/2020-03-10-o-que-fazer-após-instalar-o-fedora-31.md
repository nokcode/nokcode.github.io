---
layout: post
title: O que fazer após instalar o Fedora 31
subtitle: Complementando a instalação de seu Desktop
date: 2020-03-10 17:00:00 -0300
permalink: o-que-fazer-após-instalar-o-fedora-31
tags: gnu linux fedora codecs dnf post-install rpmfusion skype spotify
---

Primeiro, parabéns por utilizar uma distribuição tão consolidada quanto esta. Sem dúvidas, é uma das distribuições mais importante na comunidade **GNU/Linux**, que inclusive, leva seus direitos de liberdade e privacidade da maneira mais séria possível. 

Tanto é, que para garantir seus direitos, esta distribuição precisa deixar de fora alguns softwares que possam ser incompativeis com as licenças utilizadas no projeto ou ferirem sua privacidade de algum modo. 

Um dos princípios do **Fedora** é ser uma distribuição livre, composta apenas por softwares livres, assim ela garante que você fique livre para fazer o que bem entender, em outras palavras, ela lhe garante sua liberdade.

# Pós-instalação

Após a instalação do **Fedora**, o próximo passo é certamente a atualização do sistema. O **Fedora 31** foi lançado em Outubro de 2019 e até o dia deste artigo não houve outro lançamento.

Do tempo da publicação até o momento, o kernel já foi atualizado diversas vezes, e muitos outros softwares e componentes do sistema também. É imprescindível em um sistema **GNU/Linux** a atualização dos pacotes em um intervalo de tempo regular, para que haja a correção de bugs e falhas de segurança.

Para atualizar o sistema utilizamos o **DNF** *(Dandified YUM)*:

```
sudo dnf -y update
```

Este comando em conjunto com a flag **-y** aceita todas as atualizações dos repositórios atuais *(Todos os repositórios descritos nos arquivos **\*.repo** dentro do diretório **/etc/yum.repos.d/**)*.

# Habilitando o repositório RPMFusion

Infelizmente, nem todos os softwares são livres. Como por exemplo alguns **Codec's** *(Codificadores e decodificadores de áudio e vídeo)*. Apesar de existirem alternativas, muitas vezes precisamos ou queremos utilizar algum específico. Para utilizarmos estes em nosso sistema, precisamos recorrer aos repositórios alternativos de software. 

O **[RPMFusion]** é um repositório de softwares fora das diretrizes do **Fedora**, ou como eles mesmos se descrevem, é um repositório que o **Fedora** ou a **Red Hat** não querem disponibilizar em seus produtos. Tenha em mente, que ao utilizar o **RPMFusion** você não possui a mesma curadoria dos repositórios oficiais do **Fedora**. O **RPMFusion** é a junção dos sites Dribble, [FreshRPM's] e [Livna].

Na verdade no **RPMFusion** existem dois repositórios, o **free** e o **non-free**. Como você deve ter suposto o **free** contém softwares livres, mas que não podem ser distribuídos pelo **Fedora** por algum outro motivo *(incompatibilidade de licenças por exemplo)*. E o **non-free** possui softwares que não são **open-source** *(não garantem sua privacidade por esconderem o código fonte)* ou softwares **open-source** que não podém ser utilizados comercialmente *(softwares que não lhe garantem liberdade de uso)*.

Instalando o repositório **free**:

```
curl -O https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-31.noarch.rpm
sudo rpm -Uvh rpmfusion-free-release-31.noarch.rpm
```

Instalando o repositório **non-free**:

```
curl -O https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-31.noarch.rpm
sudo rpm -Uvh rpmfusion-nonfree-release-31.noarch.rpm
```

Após a instalação de novos repositórios é sempre bom atualizar o **cache**:

```
sudo dnf makecache
```

# Atualizando os pacotes de multimídia, audio e vídeo

Uma vez que o **RPMFusion** foi instalado, podemos utilizar os grupos pré-definidos deste para atualizar um conjunto de pacotes de multimídia, audio e vídeo.

Atualizando os pacotes multimídia:

```
sudo dnf -y groupupdate multimedia
```

Atualizando os pacotes de audio e vídeo:

```
sudo dnf -y groupupdate sound-and-video
```

# Instalando softwares adicionais

Neste ponto, seu sistema já está pronto para uso no cotidiano, daqui em diante vou apenas indicar alguns softwares que utilizo para complementar minha experiência desktop no **GNU/Linux**.

**Okular** é um software em **Qt** para leitura de arquivos **PDF**, está disponível no repositório oficial do **Fedora**:

```
sudo dnf -y install okular
```

**VLC** é um software para assistir vídeos, também muito utilizado no **Windows**, está disponível no repositório do **RPMFusion** no grupo de audio e vídeo:

```
sudo dnf -y install vlc
```

# Instalando o Skype

Eu utilizo o **Skype** tanto para uso profissional quanto pessoal, é uma ferramenta indispensável inclusive no mundo corporativo. A **Microsoft** disponibiliza um pacote em formato **RPM** *(Red Hat Package Manager)* no site do **Skype**, o pacote além de possuir o programa, também possui o repositório responsável por atualizações posteriores via **DNF**.

Para instalar o **Skype**:

```
curl -OL https://go.skype.com/skypeforlinux-64.rpm
sudo rpm -Uvh skypeforlinux-64.rpm
```

# Instalando o Spotify

Para instalar o **Spotify** utilizamos o gerenciador de pacotes **Flatpak**, mas antes, precisamos adicionar o repositório **[Flathub]** a ele com o comando abaixo:

```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

Após adicionar o repositório, basta instalar o **Spotify**:

```
flatpak -y install spotify
``` 

# Conclusão

Mesmo existindo inúmeras distribuições **GNU/Linux**, nem todas são livres ou respeitam sua privacidade. Apesar do **Fedora** levar estes princípios a risca, muitas vezes precisamos recorrer a softwares proprietários ou fora dos repositórios oficiais. Independente do motivo, agora você sabe como fazer para instalar aquele **Codec** de vídeo que estava faltando. 

[Flathub]: https://flathub.org/
[Livna]: http://rpm.livna.org/
[RPMFusion]: https://rpmfusion.org/
[FreshRPM's]: https://freshrpms.net/