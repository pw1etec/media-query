## 📱💻 CSS Media Queries: `min-width` vs `max-width` e muito mais 🚀

Media queries são regras CSS que permitem aplicar estilos **condicionalmente**, com base nas características do dispositivo, como **largura da tela**, **resolução**, **orientação**, **modo de cor** e muito mais.
Elas são o coração do **design responsivo**, garantindo que um mesmo site se adapte perfeitamente a **celulares, tablets e desktops**.

---

### 🔍 Revisando os tipos mais comuns

| Propriedade | Significado                          | Quando é aplicada         | Exemplo de uso              | Abordagem típica   |
| ----------- | ------------------------------------ | ------------------------- | --------------------------- | ------------------ |
| `min-width` | **"A partir de tal largura"** 📱➡️💻 | Para **larguras maiores** | `@media (min-width: 768px)` | ✅ *Mobile First*   |
| `max-width` | **"Até tal largura"** 💻➡️📱         | Para **larguras menores** | `@media (max-width: 768px)` | 🔁 *Desktop First* |

---

### 🧠 Como interpretar?

| Largura da tela | `@media (min-width: 768px)` | `@media (max-width: 768px)` |
| --------------- | --------------------------- | --------------------------- |
| `500px`         | ❌ *Não se aplica*           | ✅ *Se aplica*               |
| `768px`         | ✅ *Se aplica*               | ✅ *Se aplica*               |
| `1024px`        | ✅ *Se aplica*               | ❌ *Não se aplica*           |

---

### 🚀 Qual usar?

#### ✅ `min-width` — A abordagem moderna (*Mobile First*)

* Comece criando estilos para telas pequenas.
* À medida que a tela aumenta, **você adiciona melhorias**.
* **Mais performático** e amplamente adotado (Bootstrap, Tailwind, etc).

```css
/* Base: Mobile */
.card {
  font-size: 16px;
}

/* A partir de 768px */
@media (min-width: 768px) {
  .card {
    font-size: 18px;
  }
}
```

#### 🔁 `max-width` — A abordagem tradicional (*Desktop First*)

* Comece com o layout de **telas grandes**.
* Depois, reduza ou simplifique para telas menores.

```css
/* Base: Desktop */
.card {
  font-size: 18px;
}

/* Até 768px */
@media (max-width: 768px) {
  .card {
    font-size: 16px;
  }
}
```

---

## 🧩 Outras características que você pode controlar

Media queries não se limitam à largura.
Você pode reagir a diversas **condições do ambiente do usuário**, por exemplo:

| Tipo de Query          | O que verifica                    | Exemplo                               | Descrição                                               |
| ---------------------- | --------------------------------- | ------------------------------------- | ------------------------------------------------------- |
| `orientation`          | Orientação da tela                | `@media (orientation: landscape)`     | Aplica estilos quando o dispositivo está na horizontal. |
| `prefers-color-scheme` | Modo claro/escuro do sistema      | `@media (prefers-color-scheme: dark)` | Altera estilos conforme o modo do sistema.              |
| `resolution`           | Densidade de pixels               | `@media (min-resolution: 2dppx)`      | Ideal para imagens nítidas em telas Retina.             |
| `hover`                | Suporte a hover (passar o mouse)  | `@media (hover: hover)`               | Detecta se o dispositivo possui ponteiro de mouse.      |
| `pointer`              | Tipo de ponteiro (preciso ou não) | `@media (pointer: coarse)`            | Detecta se o toque é grosseiro (ex: dedo).              |

---

### 🎨 Exemplo prático: modo escuro e claro

```css
/* Modo claro (padrão) */
body {
  background: #fff;
  color: #111;
}

/* Modo escuro */
@media (prefers-color-scheme: dark) {
  body {
    background: #111;
    color: #fff;
  }
}
```

---

## 💡 Boas práticas para Media Queries

1. **Evite exagerar:** mantenha apenas os *breakpoints* realmente necessários.
2. **Organize os pontos de corte:** use nomes significativos ou variáveis.

   ```css
   @media (min-width: 640px) { ... } /* sm */
   @media (min-width: 768px) { ... } /* md */
   @media (min-width: 1024px) { ... } /* lg */
   ```
3. **Agrupe lógicas semelhantes:** evite espalhar media queries do mesmo tamanho por vários arquivos.
4. **Teste em dispositivos reais:** simuladores ajudam, mas nem sempre refletem o toque, brilho e densidade de tela.
5. **Prefira unidades relativas (`em`, `rem`)** em vez de `px`, quando possível — isso ajuda na acessibilidade.

---

## 🧭 Dica mental

* 🔓 **`min-width`** → “a partir de...”
* 🔒 **`max-width`** → “até...”
* ⚖️ **Combine conscientemente:** se for misturar, mantenha uma hierarquia clara (ex: `min-width` para layout e `prefers-color-scheme` para tema).

---

## 📌 Resumo rápido

* 🔹 `min-width` → *mobile first*, melhora conforme o tamanho aumenta.
* 🔹 `max-width` → *desktop first*, adapta conforme o tamanho diminui.
* 🔹 Existem media queries para **modo escuro**, **orientação**, **resolução**, etc.
* 🔹 Mantenha os *breakpoints* organizados e consistentes.
* 🔹 Teste sempre — responsividade é mais sobre **experiência real** do que números fixos.
