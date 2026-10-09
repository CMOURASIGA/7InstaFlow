# 7InstaFlow

Plataforma multi-cliente para planejamento, criação de artes, Skills de IA, aprovação versionada e publicação em Instagram. Modelo B (híbrido): operação interna cria e governa, clientes solicitam conteúdo, fornecem referências, usam Skills autorizadas e aprovam versões.

**Status:** BLUEPRINT DOCUMENTAL, PENDENTE DE HOMOLOGAÇÃO. Nenhum desenvolvimento autorizado. Data base: 09/10/2026.

## Comece por aqui
1. [Visão de produto e roadmap](docs/00-PRODUCT-VISION.md)
2. [SPEC 01, fundação e arquitetura](docs/01-SPEC-01-FOUNDATION.md)
3. [Modelo de dados e contratos](docs/02-DATA-AND-CONTRACTS.md)
4. [Governança: autorização, mídia, IA e custos](docs/03-GOVERNANCE.md)
5. [Roadmap de SPECs e Human Validation](docs/04-ROADMAP-AND-VALIDATION.md)
6. [Instruções para a equipe](docs/05-DEV-START-HERE.md)

## Legado
Sistema de referência: https://github.com/CMOURASIGA/webapppublicinsta . A existência de componentes não é evidência de homologação funcional. Migrar somente depois de inventário de dados, infraestrutura, segurança, APIs e regressão. Não copiar segredos.

## Restrições
- Sem publicação sem aprovação humana da versão específica da peça.
- Sem acesso entre tenants; RLS e autorização no servidor.
- Teto inicial por tenant de US$ 10/mês, 50 imagens/mês e 3 gerações por solicitação; alertas em 70% e 90%, bloqueio em 100%. Sujeito a homologação.
- Uso de fotografias pessoais somente com autorização específica e controle de privacidade.
- Identidade visual inspirada no 7Commander; não é autorização para migração de framework.
- Branch documental: docs/project-blueprint; revisão antes de integração em main.
