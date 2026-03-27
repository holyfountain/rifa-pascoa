# 🐣 Rifa de Páscoa II

Aplicação web para gestão de uma rifa temática de Páscoa, acessível a qualquer pessoa através do browser, sem necessidade de instalação.

**🔗 Acesso directo:** [holyfountain.github.io/rifa-pascoa/rifa2/](https://holyfountain.github.io/rifa-pascoa/rifa2/)

**📘 Página Facebook:** [Arco Íris Cor de Rosa](https://www.facebook.com/arcoiriscorderosa)

---

## Como funciona

### Para os participantes

1. **Abre o link** da rifa no browser (computador, telemóvel ou tablet).
2. **Escolhe um número** de 1 a 100 clicando numa das bolas coloridas.
3. **Introduz o teu nome** na janela que aparece e clica em **Confirmar**.
4. O número fica vermelho com o teu nome e é reservado imediatamente.
5. Faz o pagamento via **MB Way** para o número **964015229** com a nota `Rifa N°... + Teu Nome`.

> Podes comprar quantos números quiseres. Cada número custa **1 €**.

---

## Prémios

| Lugar | Prémio |
|-------|--------|
| 🥇 1.º | 🎁 Gift Box Surprise 25€ |
| 🥈 2.º | 🎁 Gift Box Surprise 20€ |
| 🥉 3.º | 🧢 Boné personalizado com nome |
| 🏅 4.º | 📓 Bloco notas personalizado com nome |

**📅 Data do Sorteio:** 2 de Abril, às 15h, em directo na página de Facebook.

---

## Legenda das cores

| Cor | Significado |
|-----|-------------|
| 🔵🟣🟡🟢🩷 (colorido) | Número disponível — clica para reservar |
| 🟡⏳ (amarelo pulsante) | Número a ser reservado por outra pessoa neste momento |
| 🔴 (vermelho) | Número já vendido |

---

## Funcionamento em tempo real

A aplicação utiliza o **Firebase Realtime Database** (caminho `rifa2/`) para sincronizar o estado entre todos os utilizadores em simultâneo:

- Quando alguém abre o modal para reservar um número, esse número fica **bloqueado** para todos em tempo real.
- Quando a compra é confirmada, o número passa a **vendido** instantaneamente em todos os ecrãs.
- Se alguém fechar o browser ou cancelar sem confirmar, o bloqueio é libertado automaticamente ao fim de **30 segundos**.
- Os dados são guardados permanentemente na base de dados — não se perdem ao fechar o browser.

---

## Notificações por e-mail

Quando um participante compra um ou mais números, é enviado automaticamente um e-mail de notificação ao administrador:

- O envio é feito via **EmailJS** (configurado no código).
- Existe um período de espera de **60 segundos** após a última compra do mesmo participante, para agrupar várias selecções numa única notificação.
- O endereço de destino é configurado pelo admin através do botão **📧 Ativar Notificação** (visível apenas em modo admin).

---

## Funcionalidades de admin

1. Clica no botão **🔒 Admin** no canto inferior direito.
2. Introduz a palavra-passe para activar o modo admin.
3. Em modo admin podes:
   - **Corrigir o nome** de um número vendido (clica no número vermelho).
   - **Libertar um número** vendido (devolver ao estado disponível).
   - **Marcar pagamentos** recebidos nos cartões de participantes.
   - **Configurar o e-mail** de notificações (botão 📧 Ativar Notificação).

---

## Estrutura de ficheiros

```
rifa2/
├── index.html   — aplicação completa (HTML + CSS + JS)
└── README.md    — este ficheiro
```

As imagens (`bg.jpeg`, `logo.png`, `logo.jpeg`) são partilhadas com a primeira rifa, na pasta pai.
