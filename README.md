#  Space Invaders - Paradigma Orientado a Objetos (POO)

Este projeto consiste em uma implementação moderna do clássico jogo **Space Invaders**, desenvolvido como requisito para a disciplina de **Paradigmas de Programação**. O foco principal é demonstrar a aplicação prática dos conceitos de POO em um ambiente de desenvolvimento real utilizando JavaScript (ES6+).

##  Objetivos do Projeto
* Decompor um sistema de software em objetos independentes e colaborativos.
* Aplicar os pilares da POO (Encapsulamento, Abstração e Composição).
* Garantir a padronização do código através de ferramentas de configuração de ambiente.

---

##  Pilares da Orientação a Objetos Aplicados

### 1. Encapsulamento e Abstração
Cada entidade do jogo (`Player`, `Invader`, `Obstacle`, `Star`, `Particle`) possui sua própria classe. A lógica interna de cada objeto é oculta, expondo apenas métodos de interface necessários para o funcionamento do jogo.
* **Exemplo:** O objeto `Player` gerencia internamente sua animação de sprites e estado de vida, enquanto o `index.js` apenas coordena sua movimentação através de métodos simples como `moveLeft()`.



### 2. Composição e Agregação
* **Agregação:** A classe `Grid` atua como um container para uma coleção de objetos `Invader`. Ela gerencia a lógica de grupo (movimento em bloco e colisão com bordas) sem que os invasores individuais precisem conhecer a estrutura da horda.
* **Composição:** O sistema de explosão é composto por múltiplas instâncias da classe `Particle`, cujas trajetórias e decaimento de opacidade são geridos individualmente em cada frame.

### 3. Reutilização de Código
A classe `Projectile` é um exemplo de reuso eficiente. Ela serve tanto para o jogador quanto para os inimigos, alterando seu comportamento dinamicamente através do atributo `velocity` injetado no construtor.

---

##  Arquitetura das Classes

| Classe | Papel no Sistema | Conceito de Paradigma |
| :--- | :--- | :--- |
| **`Player`** | Controla a nave e animações de sprites. | Gestão de Estado e Encapsulamento |
| **`Invader`** | Entidade inimiga com lógica de tiro autônomo. | Autonomia de Objeto |
| **`Grid`** | Orquestrador da horda inimiga. | Agregação de Coleções |
| **`Projectile`**| Entidade cinética de interação. | Reutilização de Código |
| **`Obstacle`** | Barreiras de defesa estáticas. | Detecção de Colisão Geométrica |
| **`Star`** | Simulação de ambiente infinito. | Persistência de Loop |
| **`Particle`** | Efeitos visuais efêmeros. | Ciclo de Vida de Objetos |
| **`SoundEffects`**| Controlador de áudio com pooling. | Gerenciamento de Recursos |

---

##  Destaques Técnicos

###  Animação via Spritesheet (Classe `Player`)
O objeto `Player` gerencia o recorte dinâmico de uma *spritesheet* (`engineSprites`). Através de um contador interno de frames e atributos de posição (`sx`), o objeto decide autonomamente qual quadro exibir, mantendo a lógica de animação separada do loop principal.

### 🔊 Object Pooling de Áudio (Classe `SoundEffects`)
Para evitar latência e interrupções no som durante o combate, a classe `SoundEffects` pré-instancia arrays de objetos de áudio. Utiliza um algoritmo de **Round Robin** (operador de módulo) para alternar entre as instâncias, permitindo sobreposição sonora fluida.



###  Padronização de Ambiente
O projeto utiliza um arquivo `.editorconfig` para garantir a consistência de código (indentação de 4 espaços, charset UTF-8 e finais de linha LF), garantindo que o paradigma de escrita seja mantido independentemente do editor utilizado.

---

##  Estrutura do Repositório

```text
├── .vscode/             # Configurações do editor (VS Code)
├── src/
│   ├── assets/          # Sprites (images) e efeitos sonoros (audios)
│   ├── classes/         # Núcleo da Lógica POO (Entidades)
│   └── utils/           # Constantes e configurações globais
├── .editorconfig        # Padronização de código
├── index.html           # Ponto de entrada HTML
├── index.js             # Orquestrador (Game Loop)
└── style.css            # UI (Estética Retro 8-bit)
```

##  Como Executar
Clone este repositório.

Como o projeto utiliza Módulos ES6 (import/export), ele deve ser aberto via servidor HTTP.

Sugestão: Utilize a extensão do `Live Server` do VS Code. Vá até o `index.html` 
e clique com o botão direito no arquivo, selecione a opção: `Open with Live Server`

Controles:

A / D: Movimentação Lateral.

ENTER: Disparar Projétil.
