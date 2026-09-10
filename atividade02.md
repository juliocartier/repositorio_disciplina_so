## Desafio de Pesquisa 1 - A Invasão (Defacement)

Enquanto o servidor sofre sob carga (ou logo após o ataque), seu próximo passo como atacante é conseguir acesso interno ao servidor alvo e desfigurar a página web.

* **Sua Missão:** Pesquise na documentação do Docker qual é o comando utilizado para executar um processo interativo (abrir um terminal `/bin/sh`) dentro de um container que já está rodando (como o `alvo-02`).
* **O Ataque Final:** Ao conseguir entrar no terminal do container, navegue até a pasta do servidor web (`cd /usr/share/nginx/html`) e sobrescreva o arquivo `index.html` com a frase *"FUI HACKEADO"*.
* **Verificação:** Acesse [http://localhost:8081](http://localhost:8081) no navegador para confirmar o sucesso da invasão.

---

## Desafio de Pesquisa 2 - A Defesa (Hardening e Cgroups)

O ataque foi um sucesso duplo: O servidor sofreu esgotamento de recursos (DoS) e teve seus arquivos sequestrados (Invasão). Como profissionais de segurança, vocês devem recriar esse servidor de forma blindada.

* **Missão de Defesa 1 (Protegendo a CPU):** Pesquise qual parâmetro do comando `docker run` permite limitar o container a usar no máximo 30% de um núcleo de CPU (0.3).
* **Missão de Defesa 2 (Protegendo os Arquivos):** Se um atacante conseguir o shell novamente, ele não pode ter permissão de alterar o arquivo `index.html`. Pesquise qual parâmetro do comando `docker run` transforma todo o sistema de arquivos do container em Somente Leitura (Read-Only).
* **Validação:** Exclua o container comprometido e suba ele novamente aplicando essas duas regras de defesa. Tente realizar a invasão do Desafio 1 novamente e veja a barreira de segurança funcionar!
