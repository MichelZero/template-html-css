# 📚 Guia Completo: Como Formatar HTML com CSS

Este guia explica como usar CSS para formatar e estilizar documentos HTML, baseado no template criado neste projeto.

## 📋 Índice

1. [Introdução](#introdução)
2. [Estrutura Básica](#estrutura-básica)
3. [Seletores CSS](#seletores-css)
4. [Propriedades Fundamentais](#propriedades-fundamentais)
5. [Layout e Posicionamento](#layout-e-posicionamento)
6. [Responsividade](#responsividade)
7. [Boas Práticas](#boas-práticas)
8. [Exemplos Práticos](#exemplos-práticos)

---

## 🎯 Introdução

CSS (Cascading Style Sheets) é a linguagem usada para descrever a apresentação de documentos HTML. Ele controla cores, fontes, layout, espaçamento e muito mais.

### Como o CSS se conecta ao HTML?

```html
<!-- 1. CSS Inline (não recomendado) -->
<p style="color: blue; font-size: 16px;">Texto azul</p>

<!-- 2. CSS Interno -->
<head>
    <style>
        p { color: blue; font-size: 16px; }
    </style>
</head>

<!-- 3. CSS Externo (recomendado) -->
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

---

## 🏗️ Estrutura Básica

### Anatomia de uma regra CSS

```css
seletor {
    propriedade: valor;
    propriedade2: valor2;
}
```

**Exemplo:**
```css
h1 {
    color: #007bff;           /* Cor do texto */
    font-size: 2rem;          /* Tamanho da fonte */
    margin-bottom: 1rem;      /* Margem inferior */
}
```

### Reset CSS

Sempre comece removendo os estilos padrão do navegador:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

---

## 🎯 Seletores CSS

### Tipos de Seletores

| Seletor | Sintaxe | Exemplo | Descrição |
|---------|---------|---------|-----------|
| **Elemento** | `elemento` | `p` | Seleciona todos os elementos `<p>` |
| **Classe** | `.classe` | `.btn` | Seleciona elementos com `class="btn"` |
| **ID** | `#id` | `#header` | Seleciona elemento com `id="header"` |
| **Atributo** | `[atributo]` | `[type="text"]` | Seleciona por atributo |
| **Descendente** | `pai filho` | `.nav a` | Seleciona `<a>` dentro de `.nav` |
| **Filho direto** | `pai > filho` | `.nav > li` | Seleciona `<li>` filhos diretos de `.nav` |
| **Pseudo-classe** | `:pseudo` | `:hover` | Estados especiais |

### Exemplos Práticos

```css
/* Seletor de elemento */
h1 {
    color: #2c3e50;
}

/* Seletor de classe */
.btn {
    padding: 12px 24px;
    border-radius: 5px;
}

/* Seletor de ID */
#hero {
    height: 100vh;
}

/* Seletor combinado */
.nav .nav-link:hover {
    color: #007bff;
}

/* Pseudo-seletor */
.btn:hover {
    transform: translateY(-2px);
}
```

---

## ⚡ Propriedades Fundamentais

### 1. Tipografia

```css
.texto {
    font-family: 'Inter', sans-serif;    /* Família da fonte */
    font-size: 1.2rem;                   /* Tamanho */
    font-weight: 600;                    /* Peso (negrito) */
    line-height: 1.6;                    /* Altura da linha */
    text-align: center;                  /* Alinhamento */
    text-decoration: none;               /* Decoração */
    letter-spacing: 1px;                 /* Espaçamento entre letras */
}
```

### 2. Cores e Fundos

```css
.elemento {
    color: #333;                         /* Cor do texto */
    background-color: #f8f9fa;           /* Cor de fundo */
    background-image: url('imagem.jpg'); /* Imagem de fundo */
    background-size: cover;              /* Tamanho da imagem */
    background-position: center;         /* Posição da imagem */
}
```

### 3. Espaçamento (Box Model)

```css
.caixa {
    margin: 20px;          /* Margem externa */
    padding: 15px;         /* Espaçamento interno */
    border: 2px solid #ddd; /* Borda */
    width: 300px;          /* Largura */
    height: 200px;         /* Altura */
}

/* Espaçamento específico por lado */
.exemplo {
    margin-top: 10px;
    margin-right: 15px;
    margin-bottom: 10px;
    margin-left: 15px;
    
    /* Ou de forma abreviada */
    margin: 10px 15px 10px 15px; /* top right bottom left */
    margin: 10px 15px;           /* top/bottom left/right */
}
```

### 4. Bordas e Sombras

```css
.card {
    border: 1px solid #e9ecef;          /* Borda simples */
    border-radius: 10px;                /* Bordas arredondadas */
    box-shadow: 0 5px 20px rgba(0,0,0,0.1); /* Sombra */
}

/* Bordas específicas */
.elemento {
    border-top: 2px solid #007bff;
    border-bottom-left-radius: 5px;
}
```

---

## 📐 Layout e Posicionamento

### 1. Display

```css
/* Tipos principais de display */
.inline { display: inline; }           /* Em linha */
.block { display: block; }             /* Em bloco */
.inline-block { display: inline-block; } /* Híbrido */
.none { display: none; }               /* Oculto */
```

### 2. Flexbox (Layout Flexível)

```css
.container {
    display: flex;
    justify-content: center;    /* Alinhamento horizontal */
    align-items: center;        /* Alinhamento vertical */
    flex-direction: row;        /* Direção dos itens */
    gap: 1rem;                  /* Espaçamento entre itens */
}

.item {
    flex: 1;                    /* Cresce para preencher espaço */
    flex-shrink: 0;             /* Não diminui */
    flex-basis: 200px;          /* Tamanho base */
}
```

### 3. Grid (Layout em Grade)

```css
.grid-container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;  /* 3 colunas iguais */
    grid-template-columns: repeat(3, 1fr); /* Mesmo resultado */
    grid-gap: 2rem;                       /* Espaçamento */
    
    /* Grid responsivo */
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}

.grid-item {
    grid-column: 1 / 3;         /* Ocupa 2 colunas */
    grid-row: 1 / 2;            /* Primeira linha */
}
```

### 4. Posicionamento

```css
.elemento {
    position: static;    /* Padrão */
    position: relative;  /* Relativo à posição original */
    position: absolute;  /* Absoluto ao pai posicionado */
    position: fixed;     /* Fixo na tela */
    position: sticky;    /* Híbrido relative/fixed */
    
    top: 10px;
    right: 20px;
    bottom: 15px;
    left: 25px;
    z-index: 1000;      /* Ordem de empilhamento */
}
```

---

## 📱 Responsividade

### Media Queries

```css
/* Desktop First */
.elemento {
    font-size: 2rem;
}

/* Tablets */
@media (max-width: 768px) {
    .elemento {
        font-size: 1.5rem;
    }
}

/* Smartphones */
@media (max-width: 480px) {
    .elemento {
        font-size: 1.2rem;
    }
}

/* Orientação */
@media (orientation: landscape) {
    .hero {
        height: 70vh;
    }
}
```

### Unidades Responsivas

```css
.responsivo {
    width: 50%;           /* Porcentagem */
    font-size: 2rem;      /* Relativo ao root */
    padding: 2em;         /* Relativo ao elemento pai */
    margin: 5vw;          /* Viewport width */
    height: 100vh;        /* Viewport height */
    font-size: 4vmin;     /* Menor dimensão do viewport */
    width: clamp(200px, 50%, 800px); /* Valor mínimo, preferido, máximo */
}
```

---

## ✨ Boas Práticas

### 1. Nomenclatura (BEM)

```css
/* Bloco */
.card { }

/* Elemento */
.card__title { }
.card__content { }

/* Modificador */
.card--featured { }
.card__title--large { }
```

### 2. Organização do CSS

```css
/* ===== VARIÁVEIS ===== */
:root {
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --border-radius: 5px;
}

/* ===== RESET ===== */
* { margin: 0; padding: 0; }

/* ===== BASE ===== */
body { font-family: sans-serif; }

/* ===== COMPONENTES ===== */
.btn { }
.card { }

/* ===== LAYOUT ===== */
.header { }
.main { }
.footer { }

/* ===== UTILITÁRIOS ===== */
.text-center { text-align: center; }
.mb-2 { margin-bottom: 2rem; }
```

### 3. Performance

```css
/* Use transform em vez de top/left para animações */
.animado {
    transform: translateX(100px);
    transition: transform 0.3s ease;
}

/* Evite seletores muito específicos */
/* ❌ Ruim */
div.container .header .nav ul li a { }

/* ✅ Bom */
.nav-link { }
```

---

## 💡 Exemplos Práticos

### 1. Botão Estilizado

```html
<button class="btn btn--primary">Clique aqui</button>
```

```css
.btn {
    padding: 12px 24px;
    border: none;
    border-radius: 5px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    text-decoration: none;
    display: inline-block;
}

.btn--primary {
    background-color: #007bff;
    color: white;
}

.btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0,123,255,0.3);
}
```

### 2. Card de Conteúdo

```html
<div class="card">
    <div class="card__image">
        <img src="imagem.jpg" alt="Descrição">
    </div>
    <div class="card__content">
        <h3 class="card__title">Título</h3>
        <p class="card__text">Descrição do conteúdo...</p>
    </div>
</div>
```

```css
.card {
    background: white;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 5px 20px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
}

.card:hover {
    transform: translateY(-5px);
}

.card__image img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.card__content {
    padding: 1.5rem;
}

.card__title {
    margin-bottom: 1rem;
    color: #2c3e50;
}

.card__text {
    color: #6c757d;
    line-height: 1.6;
}
```

### 3. Menu de Navegação Responsivo

```html
<nav class="nav">
    <div class="nav__brand">Logo</div>
    <ul class="nav__list">
        <li><a href="#" class="nav__link">Home</a></li>
        <li><a href="#" class="nav__link">Sobre</a></li>
        <li><a href="#" class="nav__link">Contato</a></li>
    </ul>
    <div class="nav__toggle">☰</div>
</nav>
```

```css
.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.nav__list {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.nav__link {
    text-decoration: none;
    color: #333;
    font-weight: 500;
    transition: color 0.3s ease;
}

.nav__link:hover {
    color: #007bff;
}

.nav__toggle {
    display: none;
    font-size: 1.5rem;
    cursor: pointer;
}

/* Responsivo */
@media (max-width: 768px) {
    .nav__list {
        position: fixed;
        top: 70px;
        left: -100%;
        width: 100%;
        height: calc(100vh - 70px);
        background: white;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        padding-top: 2rem;
        transition: left 0.3s ease;
    }
    
    .nav__list.active {
        left: 0;
    }
    
    .nav__toggle {
        display: block;
    }
}
```

---

## 🎨 Dicas Avançadas

### 1. Variáveis CSS (Custom Properties)

```css
:root {
    --primary-color: #007bff;
    --font-size-base: 1rem;
    --spacing-unit: 1rem;
}

.elemento {
    color: var(--primary-color);
    font-size: calc(var(--font-size-base) * 1.2);
    margin: calc(var(--spacing-unit) * 2);
}
```

### 2. Animações

```css
@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.animado {
    animation: fadeIn 0.5s ease-out;
}
```

### 3. Gradientes

```css
.gradiente {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    background: radial-gradient(circle, #667eea 0%, #764ba2 100%);
}
```

---

## 🔧 Ferramentas Úteis

- **VS Code Extensions**: Live Server, CSS Peek, Autoprefixer
- **Browsers**: DevTools (F12) para debug
- **Online**: CodePen, JSFiddle para testes
- **Preprocessors**: Sass, Less para CSS avançado
- **Frameworks**: Bootstrap, Tailwind CSS
- **Tools**: Autoprefixer, PostCSS, CSS Minifiers

---

## 📚 Recursos Adicionais

- [MDN CSS Reference](https://developer.mozilla.org/docs/Web/CSS)
- [CSS Tricks](https://css-tricks.com/)
- [Flexbox Froggy](https://flexboxfroggy.com/) - Jogo para aprender Flexbox
- [Grid Garden](https://cssgridgarden.com/) - Jogo para aprender Grid
- [Can I Use](https://caniuse.com/) - Compatibilidade de navegadores

---

## ✅ Checklist para Projetos

- [ ] Reset CSS aplicado
- [ ] Fontes carregadas corretamente
- [ ] Layout responsivo testado
- [ ] Estados de hover/focus implementados
- [ ] Acessibilidade considerada
- [ ] Performance otimizada
- [ ] Cross-browser testado
- [ ] Código comentado e organizado

---

*Este guia fornece uma base sólida para começar a estilizar suas páginas HTML com CSS. Pratique criando diferentes layouts e experimente com as propriedades mencionadas!*
