# Backlog do Viveiro

> Documento herdado. Escrito ao longo do 1º semestre de 2026 pela equipe anterior.
> Última alteração: 2026-05-28.
>
> **Aviso de quem escreveu:** algumas destas histórias passaram pela revisão do
> cliente e outras não. Não me lembro quais. Boa sorte. — R.M.

---

## Histórias escritas

### V-01 — Página da pessoa

**Como** aluno que encontrou uma ideia interessante,
**quero** ver a página de quem a publicou,
**para** saber se temos interesses em comum antes de procurá-la.

Pronto quando:
- clicar no nome do autor, em qualquer cartão, abre a página dessa pessoa;
- a página mostra nome, tipo (aluno ou professor), curso e interesses;
- a página lista as ideias publicadas por essa pessoa, com o título clicável;
- se a pessoa não publicou nenhuma ideia, aparece a frase "ainda não publicou ideias" no lugar da lista vazia;
- existe um caminho de volta ao mural sem usar o botão do navegador.

---

### V-02 — Filtro por curso

Implementar filtro por curso na barra lateral do mural.

Pronto quando:
- o filtro estiver funcionando.

---

### V-03 — Publicar uma ideia

**Como** aluno com uma ideia na cabeça,
**quero** publicá-la sem depender de ninguém,
**para** que ela exista antes de eu esquecer.

Pronto quando:
- existe um formulário com título, resumo e tags;
- ao enviar, a ideia aparece no topo do mural imediatamente, sem recarregar a página;
- a ideia criada traz, como autor, o nome de quem está navegando, e a data de hoje;
- título vazio impede o envio e mostra uma mensagem dizendo o que falta;
- a contagem total de ideias exibida no mural aumenta em um.

---

### V-04 — Encontrar ideias que combinam comigo

**Como** visitante do mural,
**quero** encontrar rapidamente as ideias que combinam comigo,
**para** não perder tempo.

Pronto quando:
- a interface estiver amigável;
- a busca for rápida;
- o resultado for relevante.

---

### V-05 — Entrar e sair de um grupo

**Como** aluno que quer se aproximar de um tema,
**quero** entrar num grupo,
**para** acompanhar o que se discute ali.

Pronto quando:
- a lista de grupos mostra, em cada grupo, se estou dentro ou fora;
- entrar acrescenta meu nome à lista de membros e o contador sobe;
- sair remove meu nome e o contador desce;
- a lista mostra os nomes dos membros, não apenas o número;
- trocar a pessoa em "navegando como" muda corretamente o que aparece como "meus grupos".

---

### V-06 — Estados da ideia

**Como** usuário,
**quero** que as ideias tenham estados,
**para** que os estados das ideias fiquem registrados.

Pronto quando:
- os estados estiverem implementados.

Obs.: falamos em três estados — semente, germinando, proposta.

---

### V-07 — Registrar interesse em participar

**Como** aluno que quer entrar num projeto,
**quero** declarar interesse numa ideia,
**para** que quem a propôs saiba que pode me chamar.

Pronto quando:
- cada cartão tem um controle "tenho interesse em participar";
- ao acionar, meu nome passa a constar na lista de interessados daquela ideia;
- a mesma pessoa não consegue se registrar duas vezes na mesma ideia;
- é possível desfazer o interesse, e o nome sai da lista;
- o número de interessados exibido no cartão corresponde ao tamanho da lista.

---

### V-08 — Não perder o que foi escrito

**Como** usuário,
**quero** não perder o que escrevi,
**para** não ter que digitar tudo de novo.

Pronto quando:
- os dados forem salvos em `localStorage` usando `JSON.stringify`, e recuperados no carregamento da página.

---

### V-09 — Aviso de novo interessado

**Como** aluno com uma ideia publicada,
**quero** receber uma notificação no celular quando alguém demonstrar interesse,
**para** não perder a chance de formar grupo.

Pronto quando:
- ao registrar interesse, o autor recebe uma notificação no celular em até um minuto;
- a notificação mostra o nome de quem se interessou e o título da ideia;
- tocar na notificação abre a ideia correspondente.

---

## Caixa de entrada

Anotações de conversa. Ninguém escreveu direito ainda.

- **V-10** — ideias paradas
- **V-11** — relatório por curso
- **V-12** — exportar / importar o estado

---

## Defeitos conhecidos

Nenhum destes foi priorizado. Estão aqui para não serem esquecidos.

- **B-01** — depois de clicar numa tag, não há como desfazer o filtro; só recarregando a página.
- **B-02** — quando a busca não encontra nada, o mural fica em branco, sem nenhuma explicação.
- **B-03** — a data aparece como `2026-03-14` em vez de `14/03/2026`.
- **B-04** — buscar `robotica` não encontra "Robótica"; buscar `Musica` não encontra "música".
- **B-05** — o número de apoios no cartão só muda depois que se refaz a busca.
- **B-06** — título comprido vaza para fora do cartão e atravessa o cartão vizinho.

     
    | História | Situação em que foi recebida | O que foi alterado | Justificativa |
    |---|---|---|---|
    | V-01 | História bem definida, porém faltavam detalhes sobre permissões e comportamento da página do usuário | Adicionados critérios sobre visualização de perfis, tratamento de usuário sem ideias e navegação de retorno | Evita dúvidas sobre o funcionamento da página e garante uma experiência completa |
    | V-02 | História incompleta: apenas informa que deve existir um filtro por curso | Definidos critérios sobre onde o filtro aparece, como funciona e como os resultados devem mudar | Filtro funcionando" é muito genérico e não permite validar se foi concluído |
    | V-03 | História completa, mas faltava especificar validações e comportamento após criação | Incluída validação de campos obrigatórios, atualização dinâmica do mural e associação correta do autor | Garante que a publicação funcione sem erros e mantenha os dados corretos |
    | V-04 | Continha apenas os critérios "interface amigável", "busca rápida" e "resultado relevante". |Foram definidos campos pesquisáveis, comportamento da busca, normalização de maiúsculas/minúsculas e acentos, limpeza da busca e estado sem resultados.  |Os critérios originais eram subjetivos e não permitiam testes objetivos. A nova definição transforma a intenção da história |
    | V-05 | Já definia entrada, saída, contagem de membros, lista de nomes e mudança do usuário em "navegando como".|Foram acrescentadas regras contra duplicidade e contra remoção de usuários que não pertencem ao grupo. |Evitar inconsistências nos dados dos grupos e tornar explícitas regras necessárias para manter a integridade das listas e contadores. |
    | V-06 |Informava apenas que os estados deveriam ser implementados e mencionava os três estados: semente, germinando e proposta. |Foram definidos os estados como valores controlados, sua exibição, alteração, persistência e validação. |A descrição original não estabelecia como os estados deveriam funcionar. O detalhamento permite implementação e testes objetivos.|
    | V-07 |Já apresentava o controle de interesse, inclusão e remoção do usuário, prevenção de duplicidade e contador. |Foram organizados os critérios e explicitada a atualização imediata da lista e do contador.| Melhorar a clareza da relação entre a lista de interessados e o contador apresentado no cartão, facilitando implementação e testes.|
    | V-08 |Determinava diretamente o uso de localStorage e JSON.stringify para salvar e recuperar dados. |O requisito principal passou a ser a persistência dos dados, mantendo localStorage e JSON como decisão técnica do protótipo. Também foram incluídos critérios para ausência e  |Separar o comportamento que o sistema deve oferecer da tecnologia utilizada para implementá-lo. Também é necessário evitar que dados inválidos  |
    | V-09 |Exigia notificação no celular em até um minuto, contendo o interessado e a ideia, com acesso à ideia correspondente. |Foram acrescentados critérios de prevenção de notificações duplicadas, tratamento de falhas e dependências de infraestrutura. |A funcionalidade depende de recursos que não existem em uma aplicação puramente local. Registrar essas dependências evita subestimar a complexidade da implementação. |
    | V-10 |Recebida apenas como anotação: "ideias paradas". |Foi mantida como item em descoberta, com perguntas sobre definição de inatividade, período e comportamento esperado. |Ainda não existem informações suficientes para transformar a anotação em uma história pronta para desenvolvimento.|
    | V-11 |Recebida apenas como anotação: "relatório por curso". |Foi mantida como item em descoberta e foram identificadas informações que precisam ser definidas. |Não é possível implementar corretamente um relatório sem saber quais dados, usuários e filtros serão necessários.|
    | V-12 |Recebida apenas como anotação: "exportar / importar o estado". |Foram levantadas questões sobre formato, conteúdo, validação e comportamento da importação.|Foram levantadas questões sobre formato, conteúdo, validação e comportamento da importação. |
    | B-01 | Defeito descrito como a impossibilidade de|Foram definidos os comportamentos esperados para  |Transformar o relato do problema em uma condição objetiva |
    | B-02 |desfazer o filtro sem recarregar a página. |remover o filtro e restaurar o mural.| para validação da correção.
    | B-03 |A data era exibida como 2026-03-14.  |Foi definido o formato visual 14/03/2026, mantendo a ordenação cronológica dos dados.  |Adequar a apresentação ao formato esperado para o contexto brasileiro sem prejudicar o tratamento interno das datas. |
    | B-04 |Termos sem acento não encontravam palavras com acento, como robotica e Robótica.  |Foi definida a normalização de maiúsculas/minúsculas e acentos.  |Melhorar a tolerância da busca e garantir que diferenças de escrita que não alteram o significado não impeçam a localização de uma ideia.  |
    | B-05 |O contador só era atualizado depois que uma nova busca era realizada.  |Foi definido que o contador deve ser atualizado imediatamente após a ação.  |Corrigir a inconsistência entre o estado real dos dados e o estado visual apresentado ao usuário.  |
    | B-06 | Títulos longos ultrapassavam os limites do cartão e invadiam o espaço  |Foram definidos critérios para quebra ou truncamento do texto e manutenção  |Garantir a integridade visual do layout independentemente  |
    | História | Situação em que foi recebida | O que foi alterado | Justificativa |
    
