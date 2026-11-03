# Checklist de segurança

## Identidade e autorização
- [ ] Sessões validadas no servidor.
- [ ] Associação activa utilizador-loja validada em cada operação.
- [ ] Permissões verificadas no servidor, nunca apenas na interface.
- [ ] Operações de plataforma separadas das operações de comerciante.

## Isolamento multi-tenant
- [ ] RLS activa em todas as tabelas tenant-scoped.
- [ ] Testes de leitura cruzada entre duas lojas.
- [ ] Testes de escrita, actualização e eliminação cruzadas.
- [ ] Domínio/subdomínio nunca tratado como prova de autorização.

## Pagamentos e webhooks
- [ ] Segredos apenas no servidor.
- [ ] Autenticidade do webhook validada segundo documentação do fornecedor.
- [ ] Idempotência e prevenção de replay.
- [ ] Valores e estado final reconciliados com o fornecedor.
- [ ] Nenhum dado sensível de cartão armazenado pela aplicação.

## Aplicação e operações
- [ ] Validação de payloads e limites de tamanho.
- [ ] Rate limiting em autenticação, checkout e endpoints públicos.
- [ ] Registos sem tokens, passwords ou segredos.
- [ ] Backups e procedimento de recuperação testados.
- [ ] Dependências e vulnerabilidades revistas antes de produção.
