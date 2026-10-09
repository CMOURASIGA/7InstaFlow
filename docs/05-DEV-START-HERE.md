# DEV START HERE | Handoff para desenvolvimento
Situação: SÓ DOCUMENTAÇÃO. Não desenvolver, não configurar credenciais e não fazer deploy até autorização explícita.

## Leitura obrigatória
README -> docs/00-PRODUCT-VISION -> docs/01-SPEC-01-FOUNDATION -> docs/02-DATA-AND-CONTRACTS -> docs/03-GOVERNANCE -> docs/04-ROADMAP-AND-VALIDATION.

## Primeiro trabalho a submeter ao PO (sem código de produto)
1. Registrar SHA de main do 7InstaFlow e do legado webapppublicinsta.
2. Inventariar componentes, endpoints, conectores, Supabase/RLS e contas Meta do legado (sem imprimir segredos).
3. Classificar: reaproveitar, adaptar, substituir; justificar custo/risco.
4. Diagramar fluxo de dados, fluxos de aprovação e fluxo Meta real/simulação.
5. Elaborar ERD e migrations propostas, com preservação de dados e rollback.
6. Demonstrar política de permissões e matriz de teste cross-tenant.
7. Propor benchmark oficial de modelos/preços OpenAI, 3 casos por Skill e geração de imagem, incluindo custo médio e pior caso.
8. Preparar Acceptance Criteria e Human Validation da SPEC 01 para homologação.

## Proibições
Não copiar application secrets; não criar conteúdo com fotos pessoais sem autorização; não presumir API Meta permite qualquer interação; não usar browser como única barreira de segurança; não ativar publicação real em testes; não mexer no legado de produção; não alterar main sem PR; não inferir que telas presentes equivalem a feature aprovada.

## Entrega esperada do desenvolvedor
Relatório com SHA, riscos P0/P1/P2, inventário, arquitetura atual x alvo, lacunas técnicas, proposta de branches, cronograma estimado por SPEC, critérios de aceite e perguntas de negócio ainda abertas. Somente após decisão do PO, emitir autorização de implementação da SPEC 01 ou da primeira fatia técnica delimitada.
