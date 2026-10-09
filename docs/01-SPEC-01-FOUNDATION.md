# SPEC 01 | Foundation, Multi-Tenant e Governança
Status: PROPOSTA, AGUARDANDO HUMAN VALIDATION E HOMOLOGAÇÃO. Implementação NÃO autorizada.

## Objetivo
Auditar o legado webapppublicinsta, desenhar fundação de 7InstaFlow e preparar arquitetura, contratos, segurança, migração e critérios das SPECs futuras. Sem substituir a aplicação existente.

## Evidência inicial do legado
Repositório CMOURASIGA/webapppublicinsta: React 19/Vite/TypeScript/Tailwind, Express, Supabase, Vercel Blob, Google GenAI, FFmpeg; componentes ApproveList, CreatePost, Dashboard, HistoryList, UsersManagement, VideoEditor; perfis CRIADOR/APROVADOR/ADMIN; estados RASCUNHO/PENDENTE/APROVADA/REJEITADA/AGENDADA/PUBLICADA/ERRO. Há documento de fluxo de carrossel, uploads, ordem de mídia e Graph API. Dados observados em arquivos, não homologados em ambiente real.

## Arquitetura-alvo
Web/PWA React atual como hipótese de preservação; shell de design 7Commander. API backend modular: Identity/Tenancy; Brands; Requests/Campaigns; Content/Versions; Approvals; Skills/AI Gateway; Media; Meta Connector; Scheduler/Jobs; Audit/Usage. PostgreSQL/Supabase Auth/RLS; mídia privada em storage com URLs assinadas, com entrega temporária à Meta quando necessário. Provedores desacoplados. Segredos só no servidor. Migração para Next.js não autorizada por padrão.

## Sequência de trabalho
1. Congelar referência de versões, SHA do HEAD e ambiente do legado.
2. Inventariar endpoints, UI, schema, migrações, Auth/RLS, storage, publicação real e simulador.
3. Elaborar matriz de reutilização versus refatoração e riscos.
4. Contratar entidades/serviços, regras de tenancy, contratos de eventos, status e autorizações.
5. Projetar migração e rollback sem perda; identificar dados órfãos antes de vincular tenants.
6. Definir catálogo Skills, roteamento de modelos e controle financeiro.
7. Descrever fluxos de aprovação/Meta e reconciliação de publicação.
8. Preparar matriz de testes, Human Validation e plano de SPECs.

## Restrições de arquitetura
Cada requisição identifica usuário autenticado e tenant autorizado. tenant_id obrigatório em entidade isolável, com FK/índices/constraints e RLS. Nunca confiar no tenant enviado pelo frontend. Access token externo e service role não enviados ao browser. Aprovação de content_version imutável com hash de payload, mídias, legenda e parâmetros editoriais. Jobs assíncronos idempotentes; não publicar em retry sem conciliar estado Meta. IA não aciona ferramentas destrutivas diretamente.

## Critérios de saída
Inventário com evidências e lacunas; arquitetura documentada; matriz RBAC/ABAC; esquema relacional e plano de migração reversível; orçamento e autorização de imagem pessoal definidos; state machine; API contracts; plano de testes automatizados; Human Validation assinada; relatório de riscos. Implementação das SPECs seguintes somente após aprovação explícita.

## Pendências de decisão
Modo de entrada/convite do cliente; delegação de aprovadores; política de prazo de aprovação; definição de formatos e limites Meta por conta; retenção de fotos pessoais; seleção final de modelos OpenAI com benchmark e preços vigentes; storage padrão e scheduler; integração futura HUB/7Service.
