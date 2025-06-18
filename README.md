Meu Projeto com GitHub Actions
Este projeto mostra como a gente usa o GitHub Actions para automatizar tarefas. É tipo ter um assistente que garante que tudo funcione bem e com segurança.

O Que Tem Aqui
Aqui você vai encontrar:

.github/workflows/: Aqui ficam os "roteiros" (arquivos .yml) para o nosso assistente do GitHub.

ci.yml: Nosso roteiro de verificação e preparação (CI).

deploy.yml: O roteiro para colocar o projeto no ar (deploy em produção).

run-monitor.yml: Um roteiro de exemplo pra gente ver como usar as configurações.

diagnostic.yml: Um roteiro que ajuda a descobrir se tem alguma configuração faltando.

status-check.sh: Um script simples que usamos para um dos roteiros.

Ajustes Que Você Precisa Fazer no GitHub
Pra tudo funcionar, a gente precisa falar algumas coisas pro GitHub.

Vá em Settings (Configurações) do seu projeto no GitHub.

1. Nossas Configurações (Variáveis e Segredos)
Aqui a gente guarda informações que os roteiros vão usar.

Vá em Secrets and variables > Actions.

Variáveis (Variables tab):

Crie uma chamada APP_ENV com o valor dev.

Crie uma chamada SUPPORT_EMAIL com suporte@appmonitor.io.

Segredos (Secrets tab):

Crie um segredo chamado API_KEY com um valor secreto de verdade (não mostre isso pra ninguém!).

2. Nosso Ambiente de Produção (com Aprovação!)

Vá em Environments.

Clique em New environment e chame de production.

Na tela de configuração do ambiente production:

Marque Required reviewers (Revisores obrigatórios) e coloque seu nome de usuário (ou de quem precisa liberar). Coloque 1 revisor.

Em Environment variables, adicione uma variável chamada PROD_DOMAIN com o valor appmonitor.com.

Nossos Roteiros (Workflows) do GitHub Actions
Cada roteiro faz uma coisa diferente. Veja só:

1. ci.yml
Esse roteiro roda sozinho quando você:

Manda mudanças para a branch main.

Cria um Pull Request para a branch main.

O que ele faz:

validate: Vê se nossos scripts estão escritos certo.

test: Simula uns testes pra ver se está tudo bem.

package: Junta tudo num arquivo report.zip e guarda lá no GitHub pra você baixar.

Pra Entender o Que Aconteceu:

Logs Detalhados: As mensagens são bem completas, fácil de ver tudo.

Avisos e Erros: Se algo der errado, ele mostra avisos ou erros claros.

2. run-monitor.yml
Esse você roda na mão pra testar.

O que ele faz:

Mostra como os roteiros usam as configurações e segredos que você definiu.

3. deploy.yml (Roteiro de Lançamento em Produção)
Esse roda quando você manda mudanças pra branch main.

O que ele faz:

deploy: Simula colocar seu projeto no ar em appmonitor.com.

Precisa de Aprovação: Por segurança, ele vai parar e esperar que alguém aprove manualmente antes de continuar.

4. diagnostic.yml
Esse você também roda na mão.

O que ele faz:

Verifica Tudo: Ele confere se as configurações APP_ENV e API_KEY estão lá.

Mensagens Amigáveis: Se faltar algo, ele te diz o que é e como consertar, com links diretos! Ajuda muito a resolver problemas.

Como Testar Tudo
É simples! Você vai enviar suas mudanças para o GitHub.

Crie o status-check.sh: Faça um arquivo vazio (ou com um echo "OK") chamado status-check.sh na pasta principal do seu projeto.

Rode o ci.yml e deploy.yml:

Mude algo no seu projeto (tipo, adicione uma linha aqui no README.md).

No terminal: git add ., depois git commit -m "Testando os roteiros" e git push origin main.

No GitHub, vá na aba Actions. Você vai ver o CI Workflow e o Deploy to Production rodando.

Importante para o Deploy: Clique na execução do Deploy to Production e aprove manualmente quando pedir.

Rode o run-monitor.yml e diagnostic.yml:

No GitHub, vá na aba Actions.

Na esquerda, clique em Run Monitor Workflow e depois em Run workflow.

Faça o mesmo para Diagnóstico de Variáveis e Segredos.

Enquanto testa, fique de olho:

Nas mensagens detalhadas nos logs.

Nos avisos e erros que aparecerem.

Nos resumos que aparecem na aba Summary de cada execução.


Na hora de aprovar o deploy!

Status do Nosso Assistente (CI Workflow)
Você pode ver como o nosso roteiro de preparação está se saindo aqui:

![image](https://github.com/user-attachments/assets/eac8a398-878b-4074-b948-4dce2ebf7773)

![image](https://github.com/user-attachments/assets/4c34cd1c-da2b-4078-b19c-910ba4b65244)

![image](https://github.com/user-attachments/assets/9a43164a-2cfd-4337-bf8d-a87e12bf13e1)

![image](https://github.com/user-attachments/assets/0e928080-3423-4733-a3b1-5c7ee36ddea1)

![image](https://github.com/user-attachments/assets/d404a06a-9884-48af-84b8-627e84a6dee5)

![image](https://github.com/user-attachments/assets/5602e076-d6e2-4595-8d2e-5fe95bf6ed81)





