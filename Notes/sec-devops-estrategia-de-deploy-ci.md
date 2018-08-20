# Estratégia de Deploy
  **1. Canary Development**
  
  **2. Blue/Green Deployment**

### Task de build em docker:

docker build --tag node-sample-test:$BUILD_NUMBER .
docker stop node-sample-test && docker rm node-sample-test
docker run -d --name node-sample-test -p 1337:1337 -e PORT=1337 node-sample-test:$BUILD_NUMBER


# Processo de um deploy

**Commit** --- hook ---> **Jenkins** -- job --> **Workspace**

## Problemas que essa estratégia causa:

**1. Commits simultâneos:**
  - conflito de merge;
  - conflito na versão de produção;

**2. Alteração de env de Produção:**
  - "A quente": "trocar a turbina do avião com ela quente";

**3. Testes:**
  - Unitário e de integração;

**4. Rollback:**
  - Rollback manual; 