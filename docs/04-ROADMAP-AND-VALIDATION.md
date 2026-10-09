# Roadmap, Dependências e Human Validation
Status: PLANO PROPOSTO

| SPEC | Foco | Saída |
|---|---|---|
| 01 | Auditoria legado, arquitetura, contratos e governança | Documentos e critérios homologados |
| 02 | Shell visual no padrão 7Commander | UI responsiva e navegação |
| 03 | Tenants, identidade de marca, logos, dados e fotos autorizadas | Brand Profile e acesso |
| 04 | Biblioteca, templates e estúdio | Produção editável de arte |
| 05 | OpenAI Gateway, Skills, custos e limites | IA com governança |
| 06 | Solicitações e aprovação versionada | Portal cliente e trilha de aceite |
| 07 | Calendário, Meta connector e publicações | Agendamento, conciliação e logs |
| 08 | Relatórios operacionais, métricas e custos | Dashboard |
| 09 | Skills analíticas e otimização editorial | Recomendações medidas |

## Políticas de execução
Cada SPEC inicia em branch feat/spec-NN-..., com SHA base registrado; PR draft; testes/checagens automatizados; Human Validation do PO; aprovação explícita; merge após homologação. Nunca iniciar SPEC subsequente silenciosamente. Separar simulador de integração Meta real, mantendo identificação visível de simulação.

## Casos mínimos Human Validation
HV-01: cliente A não acessa dados/arte/arquivo do B por URL, id ou consulta.
HV-02: aprovador só aprova peça e versão submetidas.
HV-03: mudança material depois da aprovação exige novo aceite.
HV-04: criador ou cliente não publica sem permissão.
HV-05: orçamento de US$ 10, cota de 50 imagens e 3 gerações por solicitação funcionam.
HV-06: alertas 70/90 sem repetições e bloqueios 100% independentes.
HV-07: duas requisições simultâneas não ultrapassam orçamento.
HV-08: tentativas com erro geram reconciliação, sem custo fictício.
HV-09: sem consentimento não há uso de foto ou imagem derivada.
HV-10: revogação impede novas gerações e revisa fila pendente.
HV-11: logos/textos exatos preservados nos templates.
HV-12: agendamento sem aprovação é rejeitado.
HV-13: retry/timeout não duplica post na Meta.
HV-14: imagens do carrossel mantêm ordem e validação.
HV-15: regressão documentada dos fluxos legados antes da migração.
HV-16: logs/URLs não expõem tokens, imagens privadas ou dados pessoais.
HV-17: calendário e job lidam com fuso horário tenant, persistência UTC e horário de verão.
HV-18: cliente não acessa configurações globais nem aumenta limite.

## Condições de Go/No-Go
Go SPEC 01: inventário técnico real, matriz de risco, ERD e políticas aprovadas e testes de desenho estabelecidos. No-Go: dúvidas de tenancy/RLS, consentimento de fotos não definido, falha no plano de migração ou custos sem guarda.
Go publicação real: permissões Meta confirmadas em conta de teste, token válido, todos os estados testados, ausência de duplicações e conciliação observável.
