<h2>Bot de Seguidores do GitHub</h2>&nbsp;<img align="right" width="35%" src="logo.png">

<h2> Sumário</h2>

- [Aviso Legal](#aviso-legal)
- [Primeiros Passos](#primeiros-passos)
	- [Instalação dos Requisitos](#instalação-dos-requisitos)
	- [Autenticação](#autenticação)
		- [Obter um Token de Acesso Pessoal do GitHub](#obter-um-token-de-acesso-pessoal-do-github)
		- [Adicionar seu nome de usuário e PAT do GitHub ao arquivo `.env`](#adicionar-seu-nome-de-usuário-e-pat-do-github-ao-arquivo-env)
- [Como Usar](#como-usar)
	- [Seguir](#seguir)
		- [Seguidores do usuário-alvo](#seguidores-do-usuário-alvo)
		- [Seguidores dos usuários mais populares de um país](#seguidores-dos-usuários-mais-populares-de-um-país)
		- [De um arquivo](#de-um-arquivo)
	- [Deixar de Seguir](#deixar-de-seguir)
		- [Todos](#todos)
		- [Seguidores](#seguidores)
		- [Não Seguidores](#não-seguidores)
		- [De um arquivo](#de-um-arquivo-1)
	- [Opções](#opções)
		- [Número máximo de seguidas/deixar de seguir](#número-máximo-de-seguidasdeixar-de-seguir)
		- [Velocidade](#velocidade)
- [Implementações Futuras](#implementações-futuras)
- [Contribuindo](#contribuindo)
- [Recursos](#recursos)

## Aviso Legal

**Esta é uma prova de conceito e foi desenvolvida apenas para fins educacionais. Você pode ter sua conta banida. Use por sua conta e risco.**

> ### Spam e Atividade Inautêntica no GitHub
>
> Atividades automatizadas excessivas e coordenadas inautênticas, como spam, são proibidas no GitHub. As atividades proibidas incluem:
>
> - (...)
> - interações inautênticas, como contas falsas e atividades automatizadas inautênticas
> - abuso de classificação, como estrelar ou seguir automatizados
>
>[De Políticas de Uso Aceitável do GitHub (em inglês)](https://docs.github.com/en/github/site-policy/github-acceptable-use-policies#4-spam-and-inauthentic-activity-on-github)

## Primeiros Passos

### Instalação dos Requisitos

```
pip install -r requirements.txt
```

### Autenticação

#### Obter um Token de Acesso Pessoal do GitHub

Certifique-se de habilitar o escopo `user` e todos os subsescopos dentro dessa permissão.

[Como obter seu PAT do GitHub (em inglês)](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)

#### Adicionar seu nome de usuário e PAT do GitHub ao arquivo `.env`

Crie um arquivo `.env` no diretório raiz do projeto ou edite o arquivo `.env.sample` (renomeie para `.env`) e adicione seu nome de usuário e PAT.

```
GITHUB_USER=SEU_NOME_DE_USUÁRIO_DO_GITHUB
TOKEN=SEU_TOKEN_DE_ACESSO_PESSOAL_DO_GITHUB
```

## Como usar

### Seguir

#### Seguidores do usuário-alvo

```
python bot_follow.py -t <USUÁRIO_ALVO>
```

#### Seguidores dos usuários mais populares de um país

([lista de países válidos](https://github.com/gayanvoice/top-github-users#readme))

```
python bot_follow.py -p <NOME_DO_PAÍS>
```

#### De um arquivo

Siga usuários a partir de um arquivo pré-gerado (JSON)

```
python bot_follow.py -f <NOME_DO_ARQUIVO>
```

### Deixar de seguir

Nota: A ordem de deixar de seguir é FIFO, ou seja, o usuário mais recentemente seguido será o último a ser deixado de seguir.

#### Todos

Deixar de seguir todos os usuários que você segue

```
python bot_unfollow.py -a
```

#### Seguidores

Deixar de seguir apenas os usuários que já o seguem

```
python bot_unfollow.py -fo
```

#### Não seguidores

Deixar de seguir apenas os usuários que não o seguem de volta

```
python bot_unfollow.py -nf
```

#### De um arquivo

Deixar de seguir usuários a partir de um arquivo pré-gerado (JSON)

```
python bot_unfollow.py -f <NOME_DO_ARQUIVO>
```

### Opções

#### Máximo de seguidores/deixar de seguir

Defina o número máximo de ações de seguir/deixar de seguir

```
-m 300
```

#### Velocidade

Um atraso aleatório (em segundos) é realizado após as ações de seguir/deixar de seguir ou quando a conta está limitada pela taxa.
Você pode alterar esses atrasos de acordo com sua preferência com os seguintes argumentos:

- Atraso mínimo entre ações
  ```
  -smin 20
  ```
- Atraso máximo entre ações
  ```
  -smax 120
  ```
- Atraso mínimo quando limitado pela taxa
  ```
  -slmin 600
  ```
- Atraso máximo quando limitado pela taxa
  ```
  -slmin 1500
  ```

## Implementação futura

- Programação - Bot realiza ações apenas entre um horário definido e dorme fora do horário
- Máximo de seguidores por fonte - Seguir no máximo `n` por usuário popular
- Adicionar fonte de seguimento - Seguir usuários por tópico
- Adicionar fonte de seguimento - Pegar seguidores de usuários listados em um arquivo
- Enviar e-mails para usuários seguidos - Enviar um e-mail para usuários seguidos com modelos (colaboração, seguir de volta ou personalizado)
- Favoritar `n` repositórios dos usuários seguidos

## Contribuindo

Contribuições são bem-vindas! Leia primeiro as [diretrizes de contribuição](https://github.com/isyuricunha/.github/blob/main/CONTRIBUTING.md#contributing).

Deseja que haja outra funcionalidade? Sinta-se à vontade para abrir um [problema de solicitação de recurso](/../../issues/new?assignees=isyuricunha&labels=enhancement&template=feature-request.md&title=%5BREQUEST%5D) com sua sugestão!

Se encontrar um bug, abra gentilmente um [problema de relatório de bug](/../../issues/new?assignees=isyuricunha&labels=bug&template=bug_report.md&title=%5BBUG%5D) conforme descrito nas diretrizes de contribuição.

## Recursos

- [API do GitHub](https://docs.github.com/en/rest)
- [Usuários principais do GitHub por país](https://github.com/gayanvoice/top-github-users)
- [GitHub-Follow-Bot](https://github.com/TheDarkAssassins/Github-Follow-Bot)