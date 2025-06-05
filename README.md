# Game-Controller-Virtual-ESP32

## Controle Virtual Responsivo para ESP32 (Offline)

Este projeto apresenta um design de controle virtual (**gamepad**) totalmente responsivo, criado utilizando **HTML**, **CSS puro** e uma pequena quantidade de **JavaScript** para feedback de toque.  
O objetivo principal é fornecer uma interface de controle visual que funcione offline, servida localmente por um **ESP32**, e que se adapte a diferentes tamanhos de tela — oferecendo uma experiência de "console" em desktops e uma visualização otimizada para tela cheia em dispositivos móveis e tablets.

---

## Funcionalidades

- **D-Pad Moderno**: Um direcional digital (**D-Pad**) circular com botões para cima, baixo, esquerda e direita.

- **Botões de Ação (Diamond Layout)**: Quatro botões de ação principais (Y, X, B, A) dispostos em um formato de losango:
  - **Y**: Amarelo  
  - **X**: Azul  
  - **B**: Vermelho  
  - **A**: Verde

- **Botões Centrais**: Dois botões menores para funções como _"View"_ (ícone de menu hambúrguer) e _"Menu"_ (ícone de três linhas).

---

## Design Responsivo Inteligente

- **Desktop ("Consolezinho")**: Em telas maiores (geralmente acima de `768px`), o controle é exibido como um elemento centralizado.

- **Celular/Tablet (Tela Cheia)**: Em telas menores (≤ `768px`), o controle ocupa toda a tela, com redimensionamento usando `vmin` e `clamp()`.

---

## Feedback Visual e de Toque

- Efeitos de `hover` e `active` nos botões em desktops.
- JavaScript captura eventos `touchstart` e `touchend`, aplicando efeitos de toque (escala, cor, brilho).
- `user-scalable=no` na meta tag evita zoom acidental.
- `user-select: none;` e `-webkit-tap-highlight-color: transparent;` melhoram a experiência em toque.

---

## Estilização para Uso Offline

- **CSS Puro e Autocontido**: Estilos definidos na própria `<style>` do HTML.
- **Sem Dependências Externas**: Sem Tailwind, Google Fonts ou qualquer CDN.
- **Fontes Padrão**: Arial, Helvetica, sans-serif.
- Aparência moderna e escura com **sombras** e **transições suaves** usando apenas CSS.

---

## Como Funciona

### Estrutura

- Corpo principal (`.controller-body`)
- Cluster do D-Pad (`.controls-cluster-left`)
- Cluster dos botões de ação (`.controls-cluster-right`)
- Botões centrais (`.center-buttons-container`)

### Responsividade

- `media queries` com `max-width: 768px`
- `.controller-body` vira `width: 100%`, `height: 100%`, e `flex-direction: row`
- `clamp()` usado para tamanhos com base em `vmin`

### JavaScript para Toque

- `touchstart` / `touchend` com `preventDefault()` (usando `{ passive: false }`)
- Estilos de feedback aplicados e removidos no toque

---

## Como Usar / Visualizar

### Para ESP32:

1. Incorpore o HTML ao projeto do ESP32 como página servida localmente.
2. Acesse via IP local do ESP32 no navegador de um dispositivo na mesma rede.

### Para Visualização Local (PC):

1. Salve o arquivo como `.html` (ex: `controle_esp32.html`).
2. Abra em qualquer navegador moderno.
3. Redimensione a janela ou abra em um dispositivo móvel para testar a responsividade.

---

## Tecnologias Utilizadas

- HTML5  
- CSS3  
- **CSS Puro** (sem frameworks)  
- Flexbox  
- Grid Layout  
- Media Queries  
- `clamp()`  
- JavaScript (para toque)

---

## Objetivo Principal

Funcionar como uma interface de controle web para projetos com **ESP32**, acessível via rede local e **totalmente offline**.
