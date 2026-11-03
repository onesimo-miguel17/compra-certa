# Backlog inicial

Este backlog é uma sequência de trabalho proposta. Nenhuma integração externa é considerada concluída apenas por constar nesta lista.

## CC-01 — Fundação
- [ ] CC-001 Validar instalação, lint, typecheck e build.
- [ ] CC-002 Definir convenções de código e commits.
- [ ] CC-003 Configurar CI para pull requests.
- [ ] CC-004 Definir estratégia de testes.
- [ ] CC-005 Configurar validação de ambiente.

## CC-02 — Supabase
- [ ] CC-010 Criar projecto Supabase após autorização.
- [ ] CC-011 Definir migrations versionadas.
- [ ] CC-012 Criar clientes server/browser com sessão segura.
- [ ] CC-013 Definir políticas de Storage.
- [ ] CC-014 Configurar backups e ambientes.

## CC-03 — Tenancy e identidade
- [ ] CC-017 Modelar stores, domains e store_members.
- [ ] CC-018 Definir papéis e permissões.
- [ ] CC-019 Implementar resolução de subdomínio.
- [ ] CC-020 Implementar autorização server-side.
- [ ] CC-021 Activar RLS e testes de isolamento.
- [ ] CC-022 Implementar onboarding de comerciante.

## CC-04 — Administração e catálogo
- [ ] CC-031 Painel do comerciante.
- [ ] CC-032 CRUD de categorias e produtos.
- [ ] CC-033 Variantes, imagens e preços.
- [ ] CC-034 Inventário e movimentos de stock.
- [ ] CC-035 Painel administrativo da plataforma.

## CC-05 — Compra e encomendas
- [ ] CC-039 Storefront público por subdomínio.
- [ ] CC-040 Carrinho persistente.
- [ ] CC-041 Checkout e validação de morada.
- [ ] CC-042 Criar encomenda com totais calculados no servidor.
- [ ] CC-043 Gestão de estados e histórico.

## CC-06 — Pagamentos
- [ ] CC-048 Confirmar requisitos comerciais e técnicos AppyPay.
- [ ] CC-049 Definir interface PaymentProvider.
- [ ] CC-050 Implementar sandbox após validação.
- [ ] CC-051 Validar autenticação e idempotência de webhooks.
- [ ] CC-052 Implementar reconciliação e tratamento de falhas.
- [ ] CC-053 Avaliar reembolsos e liquidação.

## CC-07 — Logística e comunicação
- [ ] CC-057 Fluxo logístico manual.
- [ ] CC-058 Definir interface ShippingProvider.
- [ ] CC-059 Seleccionar transportador e validar API.
- [ ] CC-060 Notificações transaccionais.

## CC-08 — Segurança e lançamento
- [ ] CC-063 Testes de acesso cruzado entre lojas.
- [ ] CC-064 Rate limiting e protecção de endpoints.
- [ ] CC-065 Auditoria de operações administrativas.
- [ ] CC-066 Testes end-to-end de checkout.
- [ ] CC-067 Revisão de privacidade e retenção de dados.
- [ ] CC-068 Backups e recuperação.
- [ ] CC-069 Staging e checklist de produção.
- [ ] CC-070 Revisão final de segurança.
