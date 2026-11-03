# Integração de pagamentos

## Princípio

O comerciante é o titular da conta de pagamento. A plataforma fornece o fluxo de checkout e a integração técnica, sem assumir que os fundos pertencem à plataforma.

## AppyPay — estado

Fornecedor candidato. A integração não está implementada nem validada.

Antes de desenvolver:
- Obter documentação oficial e actual.
- Confirmar elegibilidade comercial e onboarding de cada comerciante.
- Confirmar se o modelo de subcontas ou credenciais independentes é suportado.
- Obter credenciais de sandbox e processo de produção.
- Confirmar autenticação, assinatura e política de repetição dos webhooks.
- Confirmar pagamentos, consulta de estado, cancelamentos, reembolsos e liquidação.
- Confirmar moedas, taxas e prazos de liquidação.

## Contrato interno proposto

A aplicação deverá depender de uma interface PaymentProvider, não de endpoints específicos espalhados pelos módulos.

Operações a avaliar: createPayment, getPaymentStatus, verifyWebhook e refundPayment.

## Regras de implementação

- Criar a encomenda como pendente antes de iniciar o pagamento.
- Calcular preço, portes, descontos e total no servidor.
- Associar cada pagamento a uma loja e encomenda.
- Verificar autenticidade de notificações.
- Processar eventos de forma idempotente.
- Não marcar uma encomenda como paga apenas com base no redirect do browser.
- Registar eventos e permitir reconciliação de estados.
