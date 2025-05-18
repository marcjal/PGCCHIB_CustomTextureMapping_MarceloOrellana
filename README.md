# PGCCHIB_CustomTextureMapping_MarceloOrellana

Uma demo de **texturização avançada** em OpenGL 3.3: agora carregamos um fundo estático e um personagem animado via _spritesheet_ que caminha em múltiplas direções, com bordas _wireframe_ para cada objeto.

> **Ambiente Testado**  
> macOS (Homebrew + CMake + GLFW + GLM + GLAD). Pode ser adaptado para Linux/Windows.

---

## 📂 Estrutura do Repositório

```plaintext
PGCCHIB_CustomTextureMapping_MarceloOrellana/
├── include/              
│   └── glad/             # cabeçalhos da GLAD
│       ├── glad.h
│       └── KHR/
│           └── khrplatform.h
├── common/
│   └── glad.c            # implementação da GLAD
├── resources/            # Texturas usadas pela demo
│   ├── background.png    # imagem de fundo
│   └── Gangsters/        # pastas de animações do personagem
│       ├── Idle.png      # 1×7 frames
│       ├── Walk.png      # 1×10 frames
│       ├── Run.png       # 1×10 frames
│       ├── Jump.png      # 1×10 frames
│       ├── Attack.png    # 1×5  frames
│       ├── Shot.png      # 1×10 frames
│       ├── Recharge.png  # 1×6  frames
│       ├── Hurt.png      # 1×4  frames
│       └── Dead.png      # 1×5  frames
├── src/
│   └── CustomTextureMapping.cpp  # código da demo atualizada
├── build/                # diretório de build (git-ignored)
├── CMakeLists.txt
├── README.md             # este arquivo
└── GettingStarted.md     # guia de configuração
````

---

## ⚠️ GLAD (OpenGL Loader)

Antes de compilar, baixe e extraia manualmente via [GLAD Generator](https://glad.dav1d.de/):

* **API:** OpenGL
* **Version:** 3.3+
* **Profile:** Core
* **Language:** C/C++

Depois copie:

```text
glad.h           → include/glad/
khrplatform.h    → include/glad/KHR/
glad.c           → common/
```

---

## 🚀 Como Compilar e Executar

### 1. Instalar dependências (macOS)

```bash
brew install cmake glfw
```

### 2. Build com CMake

```bash
git clone <este-repo>
cd PGCCHIB_CustomTextureMapping_MarceloOrellana
mkdir build && cd build
cmake ..
cmake --build .
```

### 3. Executar a demo

```bash
./CustomTextureMapping
```

---

## 🎯 Sobre a Demo “CustomTextureMapping”

1. **Plano de fundo**
   A `background.png` é carregada e mapeada em um quad que preenche toda a janela (800×600).

2. **Personagem animado**

   * Várias animações em spritesheets: Idle, Walk, Run, Jump, Attack, Shot, Recharge, Hurt e Dead.
   * Cada atlas é subdividido em 1 linha × N colunas de frames.
   * Switch automático de animação ao pressionar **W/A/S/D**:

     * **W/S/A/D** → animação *Walk* e movimenta o personagem na direção correspondente.
     * Sem tecla → animação *Idle*.

3. **Controle de transformação**

   * **Translação**: posição do personagem atualizada a `speed = 200 px/s`.
   * **Escala**: personagem dimensionado para 64×64 px no mundo.

---

## 🔧 Parâmetros Principais

Em `CustomTextureMapping.cpp`, você pode ajustar:

```cpp
const unsigned int SCR_W = 800;      // largura da janela
const unsigned int SCR_H = 600;      // altura da janela

const float speed = 200.0f;          // velocidade do personagem (px/s)
glm::vec2 playerScale = {64, 64};    // dimensão do personagem
```

---

## 📖 GettingStarted.md

Consulte [GettingStarted.md](GettingStarted.md) para:

* Instalar e configurar CMake, GLFW e GLM
* Solução de problemas comuns de build
* Dicas de integração com VS Code
