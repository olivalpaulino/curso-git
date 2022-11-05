# Anotações do Git e Github #
Neste arquivo você encontrará dados referentes ao Git (versão 2.38.1) e Github (), tal como, comandos, conceitos e exemplos.  

**Autor**
* Olival Paulino.  
* Acesse meu: [Github](https://github.com/olivalpaulino)

**Comandos Git Bash**  
* cd /nome_da_pasta: Navegar entre diretórios(repositórios)  
* dir: Lista as pastas e arquivos  
* mkdir: cria a pasta  
* del: Remove o arquivo dentro da pasta  
* rmdir /S /Q: Remove todos os arquivos e a pasta  
  
**Dados Git**  
* Versão 2.30 ou Superior
* A branch principal é chamada de master (repositórios antigos) ou main (repositórios novos)
  
**Conceitos Envolvidos**
* SHA1 e Segurança
* Objetos Fundamentais
* Sistema Distribuido
  
**Usando o SHA1 para gerar o Hash do Arquivo a ser Compartilhado de Forma Segura**  
* Facilita na identificação de alterações do arquivo
* Observação: Deve-se ter cuidado com a forma de gerar o hash utilizando o SHA1, pois, pode-se utilizar o SHA1 com comandos do git, ou sem comandos do git, e isso muda o valor do HASH.
* Exemplo sem comandos Git: openss1 sha1 Git.sh
* Exemplo com comandos Git: echo 'conteudo' | git hash-object --stdin
  
**Objetos Internos do Git**  
* Commit objects
* Annotaded tag Objects
* Blobs
* Trees
  
**Blobs:**  
* echo 'conteudo' | git hash-object --stdin
* Cada arquivo no git é armazenado como um objeto Blob que tem o hash
* Diretórios são representados como árvores (Trees Objects). Ele trabalha com o mapa, que relaciona o arquivo ao hash (Trees Objects)
* Atrás do hash pode existir um simples arquivo, armazenado como blob, ou outro tree object (hash aponta para blob, hash aponta para tree)
* Snapshot - Foto do estado atual do arquivo do git que contém:
* O hash contém 40 caracteres.
* Outra forma de gerar o hash do arquivo sem os comandos do git: 
* echo -e 'conteudo' | openssl1 sha1

**Trees**
* Armazena Blobs e relaciona os blobs e as Trees
* Contém os metadados:
* \0
* tamanho
* blob | hash
* tree | hash
* nome do arquivo

**Commit**
* Commit é o objeto que vai juntar tudo.
* Commit aponta para a Tree, para um parente que é o último commit, aponta para o autor e para a mensagem
* Tem os metadados:
* Árvore e sha1
* autor
* mensagem
* timestamp (carimbo de tempo)
  
**Chaves SSH e Tokens**
* Chave Pública: Adiciona no github para ele reconhecer a nossa máquina (Nas configurações, SSH e Tokens)
* Chave Privada: Utilizada no git da máquina local para descriptografar os arquivos recebidos pelo repositório online (github)

**Gerar Chaves Pública no CLI**
* Gerar par de chaves (pública e privada): ssh-keygen -t ed25519 -C meu_email@gmail.com
* As chaves ssh ficam armazenadas na pasta/diretório oculta gerada dentro do diretório onde o código acima é executado. Exemplo: 
* /c/Users/Núcleo/.ssh/ed25519
* Ao executar o comando ssh-keygen -t ed25519 -C meu_email@gmail.com e precionar enter, será requisitada uma senha

**Adicionando Chave Pública ao Github (Repositório Online)**
* Acesse o menu configurações e a sessão SSH and GPG Keys e clique em News
* Adicione um título (title) e a chave pública gerada pelo comando ssh-keygen -t ed25519 -C meu_email@gmail.com, em Key
* Finalizado esse processo, basta executar o comando: eval $(ssh-agent -s) autenticando com a mesma senha e o respositório já estará disponível para uso via chaves ssh.
* Ao finalizar esse processo é informado o pid. Algo como: Agent pid 1445

**Demais Informações**  
* Essa foi a versão completa de configuração básica do git
* Os primeiros comandos para identificar status, preparar conteúdo para commitar, commitar, linkar o respositório local com o repositório remoto, clonar repositório, identificar erros e enviar arquivos ao respositório pode ser encontrados no arquivo Git.txt