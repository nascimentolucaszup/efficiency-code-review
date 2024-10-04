# Treinamento - Remote Quick Commands


Este projeto apresenta uma solução para otimizar o processo de revisão de Pull Requests, utilizando a StackSpot AI para automatizar tarefas repetitivas e garantir maior agilidade na entrega de novas funcionalidades. A integração desenvolvida utiliza o recurso "Remote Quick Command" da StackSpot AI para gerar automaticamente descrições detalhadas para os Pull Requests, realizar análises de segurança e adicionar comentários de revisão quando necessário. Isso reduz a dependência de revisões manuais, sem eliminar a necessidade de validação humana, permitindo que o time de engenharia se concentre em tarefas mais estratégicas e aumente a produtividade.

---

## Clonagem do projeto

```
git clone git@github.com:nascimentolucaszup/efficiency-code-review.git
```

## Criem um novo projeto no github pessoal
Assim você podem ter toda liberdade para alterar qualquer aspecto do projeto para adaptar para o cenário que vocês querem testar.

## Configurações das `Secrets` e `Vars`

**Precisamos configurar informações de `secrets` e `vars` utilizadas em nossos workflows do GitHub Actions.**  
Essas configurações são essenciais para **abstrair a necessidade de incluir dados sensíveis diretamente no código**, evitando que informações confidenciais fiquem acessíveis a pessoas que não deveriam visualizá-las.

Autenticação da API da StackSpot
```
STACKSPOT_AUTH_TOKEN=$(curl -X POST ${{vars.AUTH_URL}} \
-H "Content-Type: application/x-www-form-urlencoded" \
--data-urlencode 'client_id=${{secrets.CLIENT_ID}}' \
--data-urlencode 'grant_type=${{vars.GRANT_TYPE}}' \
--data-urlencode 'client_secret=${{secrets.CLIENT_SECRET}}')
```

URL de chamada para Remote Quick Command
```
execution_id_description=$(curl -X POST ${{vars.GENAI_CODE_BUDDY_URL}}/create-execution/ADICIONAR AQUI O SLUG DO SEU QUICK COMMAND \
-H "Authorization: Bearer $access_token"  \
-H "Content-Type: application/json" \
-d "$json_payload")
```
