# Despesas Viagem

Aplicativo web colaborativo para divisão de despesas em viagens em grupo. Qualquer pessoa com o link pode adicionar despesas, registrar pagamentos e acompanhar saldos em tempo real.

**Acesse:** [indianaralopess.github.io/despesas_viagem](https://indianaralopess.github.io/despesas_viagem/)

---

## Funcionalidades

### Participantes
- Cadastro de pessoas que participam da viagem
- Cada participante tem avatar com iniciais e cor própria
- Remoção só permitida sem lançamentos vinculados

### Despesas
- Cadastro com descrição, valor total e número de parcelas
- **Data de vencimento** (opcional) — aparece como "Todo dia X" nas listagens
- Quem pagou e quem participa da divisão
- 3 modos de divisão:
  - **Igualmente** — valor dividido por número de participantes
  - **Por percentual** — cada um define sua porcentagem
  - **Por valor** — cada um define quanto paga
- Edição e exclusão de despesas

### Divisão de Dívidas
- Cálculo automático de quem deve para quem
- **Simplificação de dívidas** — reduz o número de pagamentos necessários usando algoritmo de minimização de transferências
- Visualização **total** (todas as despesas) ou **mensal** (apenas do mês selecionado)

### Saldos por Participante
- Aba **Pagar 1x** — valor total pendente por contra-partida
- Aba **Por vencimento** — saldos agrupados por data de vencimento
- Indicador de datas atrasadas (vermelho)
- **Detalhes da dívida** — clique em uma linha para ver quais despesas compõem o valor, com divisão por participante
- Botão "Quitar" para registrar pagamentos
- Navegação por gestos (arrastar para trocar abas)

### Visão Mensal
- Navegação entre meses
- Lista de despesas do mês com valor de cada parcela
- Pendências do período

### Pagamentos
- Registro de pagamentos entre participantes
- Valor pago parcial ou total
- Exclusão de pagamentos (valor volta ao saldo pendente)

### Exportação
- Exportar dados em CSV para análise em planilhas

### Sincronização
- Dados salvos automaticamente na nuvem (JSONBin.io)
- Botão flutuante de sincronização
- Backup automático a cada 10 salvamentos
- Atualização automática ao voltar à aba

---

## Arquitetura

- **Frontend:** HTML + CSS + JavaScript (arquivo único `index.html`)
- **Backend:** JSONBin.io (API REST para persistência)
- **Hospedagem:** GitHub Pages (estático, sem servidor)

### Estrutura de dados

```
state = {
  people: [{ id, name, c (cor) }],
  expenses: [{ id, d (descrição), amount, inst, month, payer, participants, splitMode, splits, dueDate }],
  payments: [{ id, from, to, amount, month }]
}
```

###_bins JSONBin
| Bin | ID | Função |
|-----|-----|--------|
| Primária | `6a959f71...` | Estado atual |
| Backup | `6a959f90...` | Backup periódico |

---

## Como usar

1. Acesse o link do app
2. Adicione participantes na aba "Participantes"
3. Registre despesas na aba "Despesas" ou pelo botão "+"
4. Acesse "Saldo por participante" no resumo para ver quem deve quem
5. Registre pagamentos conforme forem feitos

---

## Desenvolvimento

### Rodar localmente

```bash
# Clone o repositório
git clone https://github.com/indianaralopess/despesas_viagem.git

# Abra o index.html no navegador
open index.html
```

### Publicar alterações

```bash
git add index.html
git commit -m "sua mensagem"
git push
```

O GitHub Pages atualiza automaticamente em ~1-2 minutos.

---

## Stack

- HTML5 / CSS3 / JavaScript ES6+
- Google Fonts (Noto Sans)
- JSONBin.io API
- GitHub Pages
