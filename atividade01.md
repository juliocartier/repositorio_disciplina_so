# Roteiro de Laboratório: Conteinerização e Gestão de Recursos

**Objetivo:** Consolidar os conhecimentos de criação de imagens Docker (`Dockerfile`) e administração de recursos limitados (CPU e Memória) de containers em execução.

## Passo 1: O Código-Fonte
Crie um diretório na sua estação de trabalho para esta prática. Dentro dele, desenvolva um arquivo `index.html` autoral. 
* **Requisito:** O HTML deve conter uma breve apresentação sua (um mini-currículo ou portfólio simples) e uma mensagem explicando o objetivo deste laboratório. Sinta-se à vontade para adicionar o estilo CSS que preferir.

## Passo 2: O Arquivo de Configuração (Dockerfile)
No mesmo diretório, crie um arquivo chamado `Dockerfile` (sem extensão). Escreva as instruções necessárias para:
1. Utilizar uma imagem base leve de um servidor web (ex: `nginx:alpine` ou `debian:11-slim` com instalação manual do Nginx).
2. Adicionar uma `LABEL` com o seu nome como mantenedor e a versão da imagem.
3. Definir o diretório de trabalho correto (`WORKDIR`).
4. Copiar o seu arquivo `index.html` local para o diretório padrão de páginas do servidor web dentro do container (`COPY`).
5. Expor a porta 80 (`EXPOSE`).
6. Garantir que o serviço rode em primeiro plano (`CMD`).

## Passo 3: Build e Execução
Utilizando o terminal, execute os comandos para:
1. Construir a imagem com a tag `meu-site-nginx:v1`.
2. Iniciar um container a partir dessa imagem, rodando em background (`-d`) e mapeando a porta 80 do container para a porta 8080 da sua máquina local.
3. Acesse `http://localhost:8080` no navegador para validar se o seu HTML autoral está sendo exibido corretamente.

## Passo 4: Escalabilidade e Limites de Recursos
Nesta etapa final, vamos simular um ambiente restrito onde os recursos são finitos e precisam ser controlados dinamicamente, sem derrubar a aplicação.

1. Com o container rodando, abra o terminal e inicie o monitoramento de consumo:
   ```bash
   docker stats
   ```
2. Em outra janela do terminal, aplique uma restrição dinâmica ao seu container usando o comando `docker update`. 
   * **Regra:** Limite a memória do container a **256 Megabytes** e restrinja o processamento a no máximo **0.5 (meio núcleo)** de CPU.
3. Observe o terminal onde o `docker stats` está rodando e comprove a mudança do limite de memória (`MEM LIMIT`) em tempo real.