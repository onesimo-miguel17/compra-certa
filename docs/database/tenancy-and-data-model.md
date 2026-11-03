# Base de dados — tenancy e modelo

## Regras antes de criar migrations

1. Toda a entidade pertencente a uma loja deve ter store_id e uma chave primária estável.
2. Relações entre entidades tenant-scoped devem impedir referências a registos de outra loja.
3. RLS deve ser activado por tabela e acompanhado por testes positivos e negativos.
4. A aplicação não deve usar a chave service role em operações normais de utilizadores.
5. Operações de plataforma devem ter permissões explícitas, auditáveis e limitadas.
6. Dados financeiros e estados de pagamento devem ter histórico imutável de eventos relevantes.

## Entidades a modelar

- profiles
- stores
- store_domains
- store_members
- store_settings
- roles e permissions
- categories, products, product_variants e product_images
- inventory e stock_movements
- customers e customer_addresses
- carts e cart_items
- orders e order_items
- payment_accounts, payments, payment_events e refunds
- shipping_methods, shipping_zones, shipments e shipping_events
- discounts e discount_redemptions
- notifications, audit_logs e webhook_events

## Decisões ainda necessárias

- Política de eliminação/anonimização de contas e clientes.
- Retenção de eventos de pagamento e auditoria.
- Modelo de variantes, SKU e reservas de stock.
- Regras fiscais e de facturação por mercado.
- Estratégia de numeração pública de encomendas.

Não criar tabelas de produção até as relações, constraints, índices e políticas RLS serem revistos.
