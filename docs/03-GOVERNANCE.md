# Governança | Acesso, IA, Custos e Imagem Pessoal
Status: PROPOSTA SUJEITA À HOMOLOGAÇÃO FINAL

## Permissões
Admin da plataforma: configura segurança, tenants, OpenAI/Meta e limites.
Gestor: opera tenants atribuídos, distribui trabalhos e agenda/publica.
Criador: produz e revisa, sem poder aprovar a própria peça em nome do cliente.
Solicitante cliente: abre solicitação, visualiza itens próprios e pode usar Skills habilitadas.
Aprovador: aprova/rejeita versões submetidas ao tenant.
Ações de agendar/publicar somente Admin/Gestor ou delegação explícita auditada. O mesmo usuário pode ter papéis por tenant, com checagem contextual.

## Segurança
RLS deny-by-default; testes usuário A no tenant B; política de acesso a objetos e storage; autorização no backend; criptografia e secret store para tokens; logs sem segredos, prompts sensíveis ou imagens pessoais em claro; signed URLs curtas; proteção contra upload malicioso, tipos e tamanho; proteção contra abuso/rate limits; exclusão e exportação segundo política LGPD; contas conectadas à Meta sob menor privilégio possível.

## Brand Profile
Nome público, negócio, telefone/email profissional, Instagram, segmentos, descrição, produtos/serviços, público, voz, palavras proibidas, cores, fontes e logos, exemplos aprovados. Múltiplas fotos pessoais autorizadas com ângulo/finalidade, biblioteca própria. Versões do perfil não alteram retroativamente peças aprovadas.

## Uso de imagem pessoal
Consentimento verificável por pessoa e finalidade: (a) foto original em peça; (b) envio da foto como referência a provedor externo; (c) geração derivada. Estas opções são independentes e revogáveis. Exigir aviso específico de processamento por IA e revisão humana; sem garantia de semelhança facial; não usar pessoa de um tenant para outro; impedir novas gerações após revogação; definir retenção/exclusão e eventual necessidade de reavaliar peças agendadas.

## Política inicial por tenant (DECISÃO PROVISÓRIA 09/10/2026)
USD 10 por mês calendário UTC; 50 imagens geradas por mês (incluindo variações e descartadas); 3 gerações por solicitação. Alertas ao cruzar 70% e 90% tanto no orçamento como na cota de imagens, sem spam repetido. Bloquear novas operações pagas ao esgotar o orçamento; bloquear geração de imagens ao atingir a cota, sem bloquear textos autorizados quando houver orçamento. Nenhum saldo acumulado para próximo mês. Administrador pode modificar limites com justificativa e auditoria. Sem cliente conseguir alterar seu próprio teto.

### Interpretação operacional para homologar
Uma 'geração por solicitação' é uma tentativa deliberada de geração de imagem/variação pela IA e inclui refazer. Edições de template, crop, layout e texto sem geração de imagem não contam. Tentativas com cobrança do provedor contam no custo e na cota aplicável; falhas pré-validação não. Definir política de reembolso de cota para falha técnica sem imagem e sem custo externo após conciliação. Arredondamentos e precisão monetária em decimal, não floating point. O orçamento cobre texto + imagem + Skills.

### Prevenção de estouro
Pré-flight: user+tenant+skill+consent+orçamento+cota+modelo; reserva de pior custo permitido em transação serializável/lock; tamanho máximo de entrada/saída; timeout; retries estritos; limite por minuto/usuário; medição e conciliação por execução; tratamento de chamadas simultâneas e callbacks duplicados. Se custo máximo não puder ser previsto, limitar a configuração de geração à faixa controlável ou rejeitar antes do processamento. Alertas devem disparar por cruzamento e ter deduplicação por tenant/período/limiar.

## Modelos e custos
Provider adapter OpenAI; catalogo de modelos versionado, preços e câmbio de exibição parametrizados por data; nunca gravar credencial no browser. Benchmark de texto leve versus imagem econômica/alta qualidade com cenários reais e testes de qualidade. Evitar manter nomes/preços de modelos hardcoded sem checar disponibilidade atual, região, modalidade e preços oficiais. Registrar input/output tokens, imagens, solicitações, custo estimado e custo conciliado. Métrica principal: custo por publicação aprovada e publicada.
