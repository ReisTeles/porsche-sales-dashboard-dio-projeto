# Porsche Sales Intelligence — Dashboard

Dashboard interativa em **HTML de arquivo único**, criada para o desafio de transformar a planilha de vendas da Porsche em uma visão executiva publicável no GitHub Pages.

## Perguntas de negócio escolhidas

1. **Quais modelos Porsche geram mais receita estimada?** Ajuda a priorizar os modelos que representam maior valor financeiro no conjunto analisado. O gráfico mostra os oito primeiros dentro dos filtros aplicados.
2. **Como a receita estimada evolui mês a mês?** Ajuda a observar períodos de maior ou menor valor registrado. A série utiliza somente registros com data saneada e válida.
3. **Quais formas de pagamento concentram mais receita estimada?** Ajuda a comparar a contribuição financeira das diferentes formas de pagamento.

## O que a dashboard inclui

- Indicadores de registros no recorte, receita estimada, ticket médio estimado e registros cancelados.
- Filtros por modelo Porsche, estado, cidade e ano da venda.
- Três gráficos que se atualizam com os filtros.
- Layout responsivo com identidade visual escura e detalhes em vermelho/dourado; gráficos desenhados com SVG/HTML, sem dependências externas.

## Tratamento dos dados

A dashboard incorpora apenas as colunas sanitizadas da planilha original. Os nomes de clientes e vendedores, assim como outras colunas cruas, **não são embutidos no HTML**.

- Foram incorporados 100 registros.
- Preço foi convertido para número decimal em USD e quilometragem para número inteiro.
- Modelo, forma de pagamento, cidade, estado e status usam suas versões sanitizadas.
- **24 datas** estão marcadas como `INVALID`. Elas são omitidas somente da série mensal, porque não é possível atribuí-las com segurança a um mês. Nos indicadores e nos gráficos por modelo/pagamento, seus registros continuam considerados quando os filtros não exigem um ano específico.
- **7 registros** estão com status `Cancelled`. Para não tratar cancelamentos como receita realizada, eles são excluídos da receita estimada e do ticket médio. O indicador de quantidade de registros ainda os inclui.
- Os valores de receita são apresentados em dólares americanos (USD), conforme os valores da base.
- A base contém datas saneadas até **2027-10-01**; a dashboard mantém as datas da planilha e não tenta adivinhar ou corrigir datas marcadas como inválidas.

## Prompt usado e refinamentos

### Prompt inicial

> Crie uma dashboard de vendas Porsche em um único arquivo HTML, com indicadores principais, três perguntas de negócio respondidas por gráficos e filtros interativos. Use um visual premium inspirado na marca, com boa leitura em computador e celular.

### Refinamentos aplicados

1. Especifiquei os campos que deveriam ser usados: `PorscheModelSanitized`, `SalesPriceSanitized`, `SaleDateSanitized`, `PayMethodSanitized`, `CitySanitized`, `StateSanitized` e `DeliveryStatusSanitized`.
2. Limitei a incorporação às colunas sanitizadas e excluí nomes de clientes e vendedores para não publicar dados pessoais.
3. Defini a regra de negócio da receita: excluir registros `Cancelled` da receita estimada e do ticket médio.
4. Defini a regra da série temporal: datas `INVALID` não entram no gráfico mensal, mas não são removidas silenciosamente dos demais indicadores quando não há filtro por ano.
5. Pedi gráficos responsivos e sem bibliotecas externas para que o projeto continue em um único HTML.

## Ferramenta utilizada

Construção assistida pelo **ChatGPT**, com geração e refinamento do HTML/JavaScript diretamente para este projeto. Não foi utilizado um agente personalizado com skill própria.

## Como publicar no GitHub Pages

1. Crie um repositório **público** no GitHub com nome simples, por exemplo `porsche-sales-dashboard`.
2. Envie `index.html` e `README.md` para a raiz do repositório (branch `main`).
3. No repositório, abra **Settings → Pages**.
4. Em **Build and deployment**, selecione **Deploy from a branch**; escolha `main` e a pasta `/ (root)` e salve.
5. Aguarde o GitHub Pages publicar. O endereço normalmente seguirá o formato `https://SEU-USUARIO.github.io/porsche-sales-dashboard/`.
6. Atualize esta seção com o endereço real e inclua uma captura de tela da dashboard com ao menos um filtro aplicado, como evidência do funcionamento.

**Endereço da dashboard publicada:** *preencha após habilitar o GitHub Pages.*

**Repositório:** *adicione aqui o link do seu repositório público.*

## Como testar antes de entregar

- Abra `index.html` no navegador.
- Altere modelo, estado, cidade e ano; confirme que os quatro indicadores e os gráficos atualizam.
- Use **Limpar filtros** para voltar à visão completa.
- Confira que os arquivos enviados existem na raiz e que o link informado na entrega é o do repositório, conforme solicitado pelo desafio.
