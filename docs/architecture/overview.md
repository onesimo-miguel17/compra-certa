# Visão de arquitectura — Compra Certa

## 1. Produto e limites

O Compra Certa é uma plataforma SaaS multi-tenant para lojas independentes. Não é um marketplace centralizado: cada comerciante administra a sua loja, equipa, catálogo, clientes e encomendas.

## 2. Decisões aprovadas

| Área | Decisão |
|---|---|
| Repositório | Aplicação independente |
| Infraestrutura de dados | Supabase |
| Autenticação | Supabase Auth |
| Alojamento da aplicação | Plataforma Vercel (alvo) |
| Endereçamento | Subdomínios por loja |
| Moeda inicial | AOA (Kz) |
| Idiomas iniciais | Português e Inglês |
| Pagamentos | Conta do comerciante; AppyPay em avaliação |
| Logística | Manual e integrada |

## 3. Componentes

- Next.js App Router: storefronts, painel do comerciante, painel da plataforma e endpoints.
- Supabase Auth: identidade e sessões.
- PostgreSQL: dados transaccionais e políticas RLS.
- Supabase Storage: imagens e ficheiros com políticas de acesso.
- Adaptadores de pagamento: contrato interno independente do fornecedor.
- Adaptadores logísticos: contrato interno com operação manual como fallback.

## 4. Multi-tenancy e autorização

Cada registo pertencente a uma loja deve incluir store_id. A aplicação deve resolver o domínio para uma loja activa, mas a resolução do domínio nunca concede acesso por si só.

Regras obrigatórias:
1. Validar sessão no servidor.
2. Validar associação activa do utilizador à loja.
3. Aplicar permissões por função.
4. Activar RLS em todas as tabelas tenant-scoped.
5. Derivar a loja autorizada da sessão/associação validada, não de um valor arbitrário enviado pelo browser.
6. Testar explicitamente tentativas de leitura e escrita cruzada entre lojas.

## 5. Pagamentos

Fluxo conceptual: checkout → encomenda pendente → adaptador do fornecedor → confirmação por webhook autenticado ou consulta segura → processamento idempotente → actualização da encomenda.

Não implementar credenciais nem endpoints AppyPay por suposição. Confirmar documentação oficial, contrato, sandbox, suporte multi-comerciante, assinatura de webhooks, reembolsos e liquidação antes de codificar a integração.

## 6. Logística

O comerciante pode registar método, custo, estado e referência de expedição manualmente. Integrações futuras seguem o mesmo contrato interno e não podem bloquear o fluxo manual.

## 7. Domínios de negócio previstos

Identity, tenancy, access-control, storefront, catalog, inventory, customers, cart, checkout, orders, payments, shipping, notifications, discounts, analytics e audit.

## 8. Segurança transversal

- Segredos apenas no servidor.
- Validação de entrada e autorização em cada operação.
- RLS e testes de isolamento multi-tenant.
- Webhooks autenticados, idempotentes e auditáveis.
- Limites de taxa nos endpoints sensíveis.
- Preços e totais recalculados no servidor.
- Backups e plano de recuperação antes de produção.

## 9. Fases

1. Fundação e qualidade de código.
2. Supabase, autenticação e tenancy.
3. Painel e catálogo.
4. Carrinho, checkout e encomendas.
5. Pagamentos e reconciliação.
6. Logística e notificações.
7. Segurança, testes e preparação de lançamento.
