# Prévia C6 — prévia diária de pagamentos

App simples para a equipe comercial (43 vendedores: 15 próprios (internos) + 28 Corban (terceirizadas)) registrar, 3 vezes ao dia,
o acumulado pago no banco C6, no lugar das mensagens no grupo do WhatsApp.

## O que tem

- **Login** com usuário e senha, ou "Primeiro acesso: criar minha conta" (nome, próprio/Corban, senha).
- **Enviar prévia**: valor total pago (acumulado do dia), contratos pagos, seguros pagos.
  O horário é registrado sozinho. Prazos: 1ª até 10:40 · 2ª até 14:40 · 3ª até 17:10.
  Envio depois do limite fica marcado como **atrasado**.
- **Painel geral** (todos veem): total do dia, contratos, seguros, quem já enviou e quem falta,
  tabela vendedor × 3 prévias com horário de cada envio, filtro Próprios/Corban, busca, dia anterior,
  botão "Copiar resumo pro WhatsApp".
- **Gerência** (só o gerente): total produzido por dia (próprios × Corban), ritmo do dia por prévia, comparativo próprios × Corban, pontualidade dos envios por prévia,
  quem mais atrasa, quem precisa de atenção, ranking do dia, detalhe por vendedor, cadastro/desativação de vendedores.

## Como abrir

- Online (demonstração): link do Artifact publicado pelo Claude Code.
- Local: `powershell -ExecutionPolicy Bypass -File serve.ps1` e abrir http://localhost:8790

Senha de demonstração de todos os usuários pré-cadastrados: `1234`
(ex.: `ana.souza`, `rafael.teixeira`, `gerente`). Aceita também o nome completo no campo de usuário.

## Importante sobre esta versão

É uma **demonstração**: os dados ficam salvos no navegador de cada aparelho (localStorage).
O que uma pessoa preenche no celular dela **não aparece** no celular de outra.
Os 43 vendedores e o histórico de 12 dias são fictícios, gerados na primeira abertura.

## Próximo passo para uso real (todos vendo a mesma coisa)

1. Criar um projeto gratuito no Supabase (banco Postgres + autenticação).
2. Tabelas: `vendedores (id, nome, login, tipo, papel, ativo)` e
   `envios (id, vendedor_id, data, previa, valor, contratos, seguros, hora, atrasado)`.
3. Trocar o objeto `Store` no `index.html` (leitura/gravação em localStorage) por chamadas ao Supabase.
   Toda a tela já está pronta; só a camada de dados muda.
4. Publicar o `index.html` em qualquer hospedagem estática gratuita (Cloudflare Pages, Netlify, GitHub Pages).
