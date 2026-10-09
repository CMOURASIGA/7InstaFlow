# Modelo de Dados e Contratos | 7InstaFlow
Status: PROPOSTA, não é migration executável.

## Entidades
tenants(id,slug,name,status,timezone,created_at)
users(id,auth_user_id,email,status)
tenant_memberships(id,tenant_id,user_id,role,status,permissions_override)
brand_profiles(id,tenant_id,name,segment,audience,tone,voice_rules,colors,fonts,logo_asset_id,version)
brand_assets(id,tenant_id,kind,storage_key,mime,size,checksum,visibility,created_by)
person_references(id,tenant_id,subject_id,asset_id,angle,purpose,status,consent_id)
image_consents(id,tenant_id,subject_id,scope,allowed_original,allowed_derivative,granted_at,revoked_at,expires_at,evidence_asset_id)
social_accounts(id,tenant_id,platform,external_account_id,status,token_secret_ref,connected_at)
campaigns(id,tenant_id,title,objective,status,start_at,end_at,created_by)
content_requests(id,tenant_id,campaign_id,requester_id,brief,status)
content_items(id,tenant_id,campaign_id,request_id,type,status,current_version_id)
content_versions(id,tenant_id,content_id,version_no,caption,hashtags,media_manifest,render_spec,content_hash,created_by,created_at)
approval_submissions(id,tenant_id,content_id,version_id,status,submitted_by,submitted_at)
approval_decisions(id,tenant_id,submission_id,version_id,decision,comment,actor_id,decided_at)
skills(id,code,status,scope)
skill_versions(id,skill_id,version,input_schema,output_schema,prompt_template,model_policy,status)
ai_budgets(id,tenant_id,period_utc,usd_limit,image_limit,request_generation_limit)
ai_reservations(id,tenant_id,execution_id,estimated_usd,reserved_images,status)
ai_executions(id,tenant_id,user_id,request_id,skill_version_id,model,provider_request_id,input_tokens,output_tokens,image_count,estimated_usd,actual_usd,status,created_at)
publication_jobs(id,tenant_id,content_id,version_id,social_account_id,idempotency_key,scheduled_at,status,attempts,external_container_id,external_post_id)
audit_events(id,tenant_id,actor_id,action,object_type,object_id,created_at,metadata_safe)

## Integridade
UNIQUE(tenant_id,content_id,version_no); UNIQUE(tenant_id,publication_jobs.idempotency_key); FK tenant-consistente em objetos filhos (constraints compostas ou validações server-side + testes). Preferir UUIDs; timestamptz UTC. Histórico e aprovações append-only; revogação de consentimento limita usos futuros e dispara análise de conteúdo ainda não publicado.

## State machine
RASCUNHO -> REVISAO_INTERNA -> PENDENTE_CLIENTE -> APROVADA -> AGENDADA -> PUBLICADA.
PENDENTE_CLIENTE -> AJUSTES_SOLICITADOS -> RASCUNHO (nova versão); alternativas CANCELADA, ERRO_PUBLICACAO. Mudança material de arte/legenda/mídia após aprovação cria versão e exige novo aceite. Agendamento não equivale a publicação. Falha inconclusiva Meta: RECONCILIACAO, sem republicar cegamente.

## API (proposta)
GET /api/me/tenants
GET/POST /api/tenants/:tenantId/brands
POST /api/tenants/:tenantId/requests
POST /api/tenants/:tenantId/content
POST /api/tenants/:tenantId/content/:id/versions
POST /api/tenants/:tenantId/content/:id/submit
POST /api/tenants/:tenantId/approvals/:id/decision
POST /api/tenants/:tenantId/skills/:skillCode/execute
GET /api/tenants/:tenantId/ai/usage
POST /api/tenants/:tenantId/publications/schedule
GET /api/tenants/:tenantId/publications/:jobId
Toda chamada com auth, tenant membership, checagem de ação e logs; mutações idempotentes onde necessário.

## Eventos de domínio
ContentRequested; VersionCreated; ApprovalRequested; VersionApproved; ChangesRequested; AIBudgetWarning; AIBudgetExhausted; PublishScheduled; PublishStarted; PublishSucceeded; PublishFailed; ConsentRevoked.
Outbox transactional para eventos externos futuros; não prometer entrega exatamente uma vez na Meta.
