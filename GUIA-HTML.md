# 📖 Guia Completo: HTML Fundamentals

Este guia explica todos os conceitos fundamentais do HTML (HyperText Markup Language), baseado no template criado neste projeto, com exemplos práticos e boas práticas.

## 📋 Índice

1. [Introdução ao HTML](#introdução-ao-html)
2. [Estrutura Básica](#estrutura-básica)
3. [Tags Fundamentais](#tags-fundamentais)
4. [Semântica HTML5](#semântica-html5)
5. [Formulários](#formulários)
6. [Meta Tags e SEO](#meta-tags-e-seo)
7. [Acessibilidade](#acessibilidade)
8. [Boas Práticas](#boas-práticas)
9. [Exemplos Práticos](#exemplos-práticos)

---

## 🌐 Introdução ao HTML

HTML (HyperText Markup Language) é a linguagem de marcação padrão para criar páginas web. Ela descreve a estrutura e o conteúdo de uma página usando elementos (tags).

**Por que HTML é importante?**
- É a **base fundamental** de toda página web
- Define a **estrutura semântica** do conteúdo
- Permite que navegadores **interpretem e exibam** informações corretamente
- É **universalmente suportado** por todos os dispositivos e navegadores
- Serve como **fundação** para CSS (estilo) e JavaScript (interatividade)

### O que é uma Tag?
Uma tag é um elemento HTML que define o início e o fim de um bloco de conteúdo. As tags são escritas entre colchetes angulares `< >`.

```html
<tagname>conteúdo</tagname>
```

**Características das Tags:**
- São **case-insensitive** (não diferencia maiúsculas/minúsculas), mas a convenção é usar minúsculas
- Podem ser **aninhadas** (uma dentro da outra)
- Devem ser **fechadas** na ordem correta (LIFO - Last In, First Out)
- Algumas são **auto-fecháveis** e não precisam de tag de fechamento

### Estrutura de uma Tag
- **Tag de abertura**: `<tagname>` - Marca o início do elemento
- **Conteúdo**: texto ou outros elementos HTML
- **Tag de fechamento**: `</tagname>` - Marca o fim do elemento (note a barra `/`)

**Exemplo com aninhamento:**
```html
<div>
    <h1>Título Principal</h1>
    <p>Este é um <strong>parágrafo</strong> com texto em negrito.</p>
</div>
```

### Tags Auto-fecháveis

```html
<img src="imagem.jpg" alt="Descrição">
<br>
<hr>
<input type="text">
```

**Por que usar Tags Auto-fecháveis?**

As tags auto-fecháveis (também chamadas de "void elements" ou "empty elements") existem por razões técnicas e semânticas importantes:

1. **Não possuem conteúdo interno**: Essas tags não "envolvem" conteúdo como outras tags fazem
2. **Representam elementos únicos**: São elementos que existem por si só (como uma imagem ou quebra de linha)
3. **Maior eficiência**: Não precisam de tag de fechamento, tornando o código mais limpo
4. **Padrão HTML5**: É a forma correta e moderna de escrever esses elementos

**Exemplos práticos do porquê:**

```html
<!-- ❌ ERRADO: Tentar fechar uma tag auto-fechável -->
<img src="foto.jpg" alt="Foto"></img>  <!-- Inválido! -->
<br></br>                              <!-- Inválido! -->

<!-- ✅ CORRETO: Tags auto-fecháveis -->
<img src="foto.jpg" alt="Foto">       <!-- Válido -->
<br>                                   <!-- Válido -->

<!-- Para comparação, tags que TÊM conteúdo: -->
<p>Este parágrafo TEM conteúdo interno</p>  <!-- Precisa fechar -->
<div>Esta div TEM conteúdo dentro</div>     <!-- Precisa fechar -->
```

**Tags auto-fecháveis mais comuns:**

- `<img>` - Exibe imagens (não tem "conteúdo interno")
- `<br>` - Quebra de linha (é um ponto específico, não um "container")
- `<hr>` - Linha horizontal (é uma linha, não contém texto)
- `<input>` - Campos de formulário (o valor está no atributo, não dentro da tag)
- `<meta>` - Metadados da página (informações sobre a página, não conteúdo visível)
- `<link>` - Links para recursos externos (CSS, favicon, etc.)

**Vantagens das tags auto-fecháveis:**

1. **Código mais limpo**: Menos tags para digitar e manter
2. **Menos erros**: Não é possível esquecer de fechar a tag
3. **Melhor performance**: Menos processamento pelo navegador
4. **Semântica clara**: Deixa claro que o elemento não contém conteúdo

### O que é um Atributo?
Um atributo é uma característica adicional que pode ser adicionada a uma tag HTML para fornecer mais informações sobre o elemento. Os atributos são sempre especificados na tag de abertura e consistem em um nome e um valor.

```html
<img src="imagem.jpg" alt="Descrição">
```

**Estrutura dos Atributos:**
- **Nome do atributo**: define que tipo de informação (ex: `src`, `alt`, `class`)
- **Valor do atributo**: a informação específica (entre aspas)
- **Sintaxe**: `nome="valor"`

**Atributos Globais (funcionam em qualquer elemento):**
- `id` - Identificador único do elemento
- `class` - Classe CSS para estilização
- `style` - Estilos CSS inline
- `title` - Texto de ajuda ao passar o mouse
- `lang` - Idioma do conteúdo
- `data-*` - Atributos customizados para dados

---

## 🏗️ Estrutura Básica

### Documento HTML Mínimo

Todo documento HTML segue uma estrutura padrão que garante compatibilidade e funcionalidade adequada:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Título da Página</title>
</head>
<body>
    <h1>Olá, Mundo!</h1>
    <p>Este é meu primeiro parágrafo.</p>
</body>
</html>
```

### Explicação Detalhada dos Elementos

| Elemento | Descrição | Por que é Importante |
|----------|-----------|---------------------|
| `<!DOCTYPE html>` | Declara que é um documento HTML5 | Garante que o navegador interprete o código como HTML5 moderno |
| `<html lang="pt-BR">` | Elemento raiz que contém todo o conteúdo | Define o idioma principal da página para acessibilidade e SEO |
| `<head>` | Metadados não visíveis na página | Contém informações técnicas, links para CSS/JS, e meta tags |
| `<body>` | Conteúdo visível da página | Tudo que o usuário vê e interage na página |

### Seção `<head>` - Metadados Essenciais

A seção `<head>` é crucial para o funcionamento adequado da página:

```html
<head>
    <!-- Obrigatório: Define codificação de caracteres -->
    <meta charset="UTF-8">
    
    <!-- Obrigatório: Configuração para dispositivos móveis -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Obrigatório: Título que aparece na aba do navegador -->
    <title>Minha Página Web</title>
    
    <!-- Recomendado: Descrição para motores de busca -->
    <meta name="description" content="Descrição da página">
    
    <!-- Opcional: Link para folha de estilo -->
    <link rel="stylesheet" href="styles.css">
</head>
```

**Meta Tags Fundamentais:**

- **`charset="UTF-8"`**: Permite caracteres especiais (acentos, emojis, símbolos)
- **`viewport`**: Torna a página responsiva em dispositivos móveis
- **`title`**: Aparece na aba do navegador e é usado pelo Google nos resultados de busca

### Seção `<body>` - Conteúdo da Página

O `<body>` contém todo o conteúdo visível e interativo:

```html
<body>
    <!-- Cabeçalho da página -->
    <header>
        <h1>Título Principal</h1>
        <nav>Menu de navegação</nav>
    </header>
    
    <!-- Conteúdo principal -->
    <main>
        <section>
            <h2>Seção de conteúdo</h2>
            <p>Parágrafo com texto.</p>
        </section>
    </main>
    
    <!-- Rodapé da página -->
    <footer>
        <p>© 2025 Meu Site</p>
    </footer>
</body>
```

### Exemplo do Nosso Template

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <!-- Meta tags obrigatórias para HTML5 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Título da página que aparece na aba do navegador -->
    <title>Template HTML/CSS - Exemplo Completo</title>

    <!-- Meta tags para SEO (Search Engine Optimization) -->
    <meta name="description" content="Template HTML e CSS com estrutura completa e responsiva">
    <meta name="keywords" content="html, css, template, responsivo, web development">
    <meta name="author" content="Seu Nome">
    
    <!-- Links externos -->
    <link rel="stylesheet" href="styles.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
</head>
<body>
    <!-- Conteúdo da página -->
</body>
</html>
```

---

## 🏷️ Tags Fundamentais

### 1. Títulos (Headings)

Os títulos criam uma hierarquia de conteúdo e são fundamentais para SEO e acessibilidade:

```html
<h1>Título Principal</h1>        <!-- Mais importante -->
<h2>Título Secundário</h2>
<h3>Subtítulo</h3>
<h4>Título de Quarto Nível</h4>
<h5>Título de Quinto Nível</h5>
<h6>Título Menor</h6>             <!-- Menos importante -->
```

**Regras importantes:**

- **Use apenas um `<h1>` por página** - Representa o tópico principal
- **Mantenha hierarquia lógica** (h1 → h2 → h3) - Como um sumário de livro
- **Não pule níveis** (h1 → h3) - Pode confundir leitores de tela
- **Use h1 para título da página**, h2 para seções principais, h3 para subseções

**Exemplo de hierarquia correta:**
```html
<h1>Guia de HTML</h1>
    <h2>Introdução</h2>
        <h3>O que é HTML</h3>
        <h3>História do HTML</h3>
    <h2>Tags Básicas</h2>
        <h3>Títulos</h3>
        <h3>Parágrafos</h3>
```

### 2. Parágrafos e Formatação de Texto

```html
<p>Este é um parágrafo normal.</p>

<p>Texto com <strong>negrito semântico</strong> e <em>itálico semântico</em>.</p>

<p>Texto com <b>negrito visual</b> e <i>itálico visual</i>.</p>

<p>Texto <mark>destacado</mark> e <del>riscado</del>.</p>

<p>H<sub>2</sub>O e E=mc<sup>2</sup></p>

<!-- Quebra de linha -->
<p>Primeira linha<br>Segunda linha</p>

<!-- Linha horizontal -->
<hr>
```

**Diferenças importantes:**

- **`<strong>` vs `<b>`**: `<strong>` indica importância semântica, `<b>` é apenas visual
- **`<em>` vs `<i>`**: `<em>` indica ênfase semântica, `<i>` é apenas visual
- **`<mark>`**: Destaca texto como se fosse marcador amarelo
- **`<del>`**: Indica texto removido ou tachado
- **`<sub>` e `<sup>`**: Subscrito e sobrescrito para fórmulas químicas/matemáticas
- **`<br>`**: Quebra de linha (use com moderação)
- **`<hr>`**: Separador horizontal entre seções

### 3. Listas

As listas organizam informações relacionadas de forma estruturada:

#### Lista Não Ordenada (Unordered List)

Use `<ul>` quando a ordem dos itens não importa:

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

**Quando usar:**
- Listas de recursos ou características
- Menu de navegação
- Lista de itens sem ordem específica

#### Lista Ordenada (Ordered List)

Use `<ol>` quando a ordem/sequência importa:

```html
<ol>
    <li>Primeiro item</li>
    <li>Segundo item</li>
    <li>Terceiro item</li>
</ol>
```

**Quando usar:**
- Passos de um tutorial
- Rankings ou classificações
- Instruções sequenciais

**Atributos úteis:**
- `type="1"` - Números (padrão)
- `type="A"` - Letras maiúsculas
- `type="a"` - Letras minúsculas
- `type="I"` - Números romanos maiúsculos
- `start="5"` - Começa no número 5

#### Lista de Definições (Description List)

Use `<dl>` para definir termos e suas descrições:

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
    
    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
    
    <dt>JavaScript</dt>
    <dd>Linguagem de programação para web</dd>
    <dd>Adiciona interatividade às páginas</dd>
</dl>
```

**Quando usar:**
- Glossários e dicionários
- Perguntas e respostas (FAQ)
- Metadados de produtos

#### Listas Aninhadas

Você pode criar listas dentro de listas:

```html
<ul>
    <li>Frontend
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ul>
    </li>
    <li>Backend
        <ol>
            <li>Python</li>
            <li>Node.js</li>
            <li>PHP</li>
        </ol>
    </li>
</ul>
```

### 4. Links (Âncoras)

Os links são fundamentais para conectar páginas e criar navegação:

```html
<!-- Link externo -->
<a href="https://www.google.com">Google</a>

<!-- Link interno (mesma página) -->
<a href="#secao">Ir para seção</a>

<!-- Link para e-mail -->
<a href="mailto:contato@exemplo.com">Enviar e-mail</a>

<!-- Link para telefone -->
<a href="tel:+5511999999999">Ligar</a>

<!-- Link que abre em nova aba -->
<a href="https://www.google.com" target="_blank" rel="noopener">Google</a>
```

**Tipos de Links:**

1. **Links Externos**: Levam para outros sites
   - Sempre use `target="_blank" rel="noopener"` para segurança
   - O `rel="noopener"` previne ataques de tabnabbing

2. **Links Internos**: Navegam dentro da mesma página
   - Use `href="#id-do-elemento"` para ir a uma seção específica
   - Crie âncoras com `id="secao"` nos elementos de destino

3. **Links de Comunicação**:
   - `mailto:` abre o cliente de e-mail padrão
   - `tel:` permite ligar em dispositivos móveis
   - `sms:` abre aplicativo de SMS

**Atributos importantes:**
- `href` - URL de destino (obrigatório)
- `target` - Como abrir o link (_blank, _self, _parent, _top)
- `rel` - Relacionamento com o destino (noopener, nofollow, etc.)
- `title` - Tooltip ao passar o mouse
- `download` - Força download ao invés de navegar

**Exemplo de navegação interna:**
```html
<!-- Menu com links internos -->
<nav>
    <a href="#inicio">Início</a>
    <a href="#sobre">Sobre</a>
    <a href="#contato">Contato</a>
</nav>

<!-- Seções correspondentes -->
<section id="inicio">
    <h2>Bem-vindo</h2>
</section>

<section id="sobre">
    <h2>Sobre Nós</h2>
</section>

<section id="contato">
    <h2>Contato</h2>
</section>
```

### 5. Imagens

```html
<!-- Imagem básica -->
<img src="imagem.jpg" alt="Descrição da imagem">

<!-- Imagem com dimensões -->
<img src="imagem.jpg" alt="Descrição" width="300" height="200">

<!-- Imagem responsiva -->
<img src="imagem.jpg" alt="Descrição" style="max-width: 100%; height: auto;">

<!-- Imagem com diferentes tamanhos -->
<picture>
    <source media="(max-width: 600px)" srcset="imagem-pequena.jpg">
    <source media="(max-width: 1200px)" srcset="imagem-media.jpg">
    <img src="imagem-grande.jpg" alt="Descrição">
</picture>
```

### 6. Tabelas

```html
<table>
    <caption>Vendas por Trimestre</caption>
    <thead>
        <tr>
            <th>Produto</th>
            <th>Q1</th>
            <th>Q2</th>
            <th>Q3</th>
            <th>Q4</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Produto A</td>
            <td>1000</td>
            <td>1200</td>
            <td>1100</td>
            <td>1300</td>
        </tr>
        <tr>
            <td>Produto B</td>
            <td>800</td>
            <td>900</td>
            <td>850</td>
            <td>950</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>1800</td>
            <td>2100</td>
            <td>1950</td>
            <td>2250</td>
        </tr>
    </tfoot>
</table>
```

---

## 🎯 Semântica HTML5

O HTML5 introduziu elementos semânticos que dão significado ao conteúdo, melhorando SEO e acessibilidade.

### Elementos de Layout Semântico

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Página Semântica</title>
</head>
<body>
    <!-- Cabeçalho principal -->
    <header>
        <nav>
            <ul>
                <li><a href="#home">Início</a></li>
                <li><a href="#about">Sobre</a></li>
                <li><a href="#contact">Contato</a></li>
            </ul>
        </nav>
    </header>

    <!-- Conteúdo principal -->
    <main>
        <!-- Artigo principal -->
        <article>
            <header>
                <h1>Título do Artigo</h1>
                <time datetime="2025-01-15">15 de Janeiro, 2025</time>
            </header>
            
            <section>
                <h2>Introdução</h2>
                <p>Conteúdo da introdução...</p>
            </section>
            
            <section>
                <h2>Desenvolvimento</h2>
                <p>Conteúdo do desenvolvimento...</p>
            </section>
        </article>

        <!-- Conteúdo relacionado -->
        <aside>
            <h3>Artigos Relacionados</h3>
            <ul>
                <li><a href="#">Artigo 1</a></li>
                <li><a href="#">Artigo 2</a></li>
            </ul>
        </aside>
    </main>

    <!-- Rodapé -->
    <footer>
        <p>&copy; 2025 Meu Site. Todos os direitos reservados.</p>
    </footer>
</body>
</html>
```

### Elementos Semânticos

| Elemento | Uso | Exemplo |
|----------|-----|---------|
| `<header>` | Cabeçalho da página ou seção | Logo, navegação |
| `<nav>` | Navegação principal | Menu, breadcrumb |
| `<main>` | Conteúdo principal | Área central da página |
| `<article>` | Conteúdo independente | Post, notícia |
| `<section>` | Seção temática | Capítulo, parte |
| `<aside>` | Conteúdo relacionado | Sidebar, widgets |
| `<footer>` | Rodapé | Copyright, links |
| `<figure>` | Conteúdo ilustrativo | Imagem com legenda |
| `<figcaption>` | Legenda do figure | Descrição da imagem |

### Exemplo do Nosso Template

```html
<!-- CABEÇALHO/HEADER -->
<header class="header">
    <div class="container">
        <!-- Logo/Nome do site -->
        <div class="logo">
            <h1>MeuSite</h1>
        </div>
        
        <!-- Menu de navegação -->
        <nav class="nav">
            <ul class="nav-list">
                <li class="nav-item"><a href="#home" class="nav-link">Início</a></li>
                <li class="nav-item"><a href="#about" class="nav-link">Sobre</a></li>
                <li class="nav-item"><a href="#services" class="nav-link">Serviços</a></li>
                <li class="nav-item"><a href="#contact" class="nav-link">Contato</a></li>
            </ul>
        </nav>
    </div>
</header>

<!-- CONTEÚDO PRINCIPAL -->
<main>
    <!-- SEÇÃO HERO (Banner principal) -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1 class="hero-title">Bem-vindo ao Nosso Site</h1>
            <p class="hero-subtitle">Criando experiências digitais incríveis</p>
            <button class="btn btn-primary">Saiba Mais</button>
        </div>
    </section>
</main>
```

---

## 📝 Formulários

Os formulários são essenciais para interação do usuário com a página.

### Estrutura Básica

```html
<form action="/processar" method="POST">
    <fieldset>
        <legend>Informações Pessoais</legend>
        
        <div class="form-group">
            <label for="nome">Nome:</label>
            <input type="text" id="nome" name="nome" required>
        </div>
        
        <div class="form-group">
            <label for="email">E-mail:</label>
            <input type="email" id="email" name="email" required>
        </div>
        
        <button type="submit">Enviar</button>
    </fieldset>
</form>
```

### Tipos de Input

```html
<!-- Texto -->
<input type="text" placeholder="Digite seu nome">

<!-- E-mail (com validação) -->
<input type="email" placeholder="email@exemplo.com">

<!-- Senha -->
<input type="password" placeholder="Sua senha">

<!-- Número -->
<input type="number" min="0" max="100" step="1">

<!-- Data -->
<input type="date">

<!-- Hora -->
<input type="time">

<!-- Telefone -->
<input type="tel" placeholder="(11) 99999-9999">

<!-- URL -->
<input type="url" placeholder="https://exemplo.com">

<!-- Arquivo -->
<input type="file" accept="image/*">

<!-- Checkbox -->
<input type="checkbox" id="aceito" name="aceito">
<label for="aceito">Aceito os termos</label>

<!-- Radio buttons -->
<input type="radio" id="masc" name="genero" value="masculino">
<label for="masc">Masculino</label>

<input type="radio" id="fem" name="genero" value="feminino">
<label for="fem">Feminino</label>

<!-- Range (slider) -->
<input type="range" min="0" max="100" value="50">

<!-- Color picker -->
<input type="color" value="#ff0000">
```

### Textarea e Select

```html
<!-- Área de texto -->
<textarea name="mensagem" rows="5" cols="30" placeholder="Sua mensagem..."></textarea>

<!-- Select simples -->
<select name="cidade">
    <option value="">Escolha uma cidade</option>
    <option value="sp">São Paulo</option>
    <option value="rj">Rio de Janeiro</option>
    <option value="bh">Belo Horizonte</option>
</select>

<!-- Select múltiplo -->
<select name="interesses" multiple>
    <option value="web">Desenvolvimento Web</option>
    <option value="mobile">Apps Mobile</option>
    <option value="design">Design</option>
</select>

<!-- Select com grupos -->
<select name="linguagem">
    <optgroup label="Frontend">
        <option value="html">HTML</option>
        <option value="css">CSS</option>
        <option value="js">JavaScript</option>
    </optgroup>
    <optgroup label="Backend">
        <option value="php">PHP</option>
        <option value="python">Python</option>
        <option value="nodejs">Node.js</option>
    </optgroup>
</select>
```

### Exemplo do Nosso Template

```html
<!-- Formulário de contato -->
<div class="contact-form">
    <form>
        <div class="form-group">
            <label for="name">Nome</label>
            <input type="text" id="name" name="name" required>
        </div>
        
        <div class="form-group">
            <label for="email">E-mail</label>
            <input type="email" id="email" name="email" required>
        </div>
        
        <div class="form-group">
            <label for="message">Mensagem</label>
            <textarea id="message" name="message" rows="5" required></textarea>
        </div>
        
        <button type="submit" class="btn btn-primary">Enviar Mensagem</button>
    </form>
</div>
```

### Validação HTML5

```html
<form>
    <!-- Campo obrigatório -->
    <input type="text" required>
    
    <!-- Mínimo e máximo de caracteres -->
    <input type="text" minlength="3" maxlength="20">
    
    <!-- Padrão com regex -->
    <input type="text" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}" title="Formato: 123-456-7890">
    
    <!-- Valor mínimo e máximo -->
    <input type="number" min="18" max="99">
    
    <!-- Campo com validação customizada -->
    <input type="email" required title="Digite um e-mail válido">
</form>
```

---

## 🎯 Meta Tags e SEO

As meta tags fornecem informações sobre a página para navegadores e mecanismos de busca.

### Meta Tags Essenciais

```html
<head>
    <!-- Codificação de caracteres -->
    <meta charset="UTF-8">
    
    <!-- Viewport para responsividade -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Título da página (aparece na aba) -->
    <title>Título da Página - Até 60 caracteres</title>
    
    <!-- Descrição para motores de busca -->
    <meta name="description" content="Descrição da página com 150-160 caracteres">
    
    <!-- Palavras-chave (menos importante hoje) -->
    <meta name="keywords" content="palavra1, palavra2, palavra3">
    
    <!-- Autor da página -->
    <meta name="author" content="Seu Nome">
    
    <!-- Controle de robôs dos motores de busca -->
    <meta name="robots" content="index, follow">
    
    <!-- Idioma principal -->
    <meta name="language" content="PT-BR">
</head>
```

### Meta Tags para Redes Sociais

#### Open Graph (Facebook, LinkedIn)
```html
<meta property="og:title" content="Título da Página">
<meta property="og:description" content="Descrição da página">
<meta property="og:image" content="https://exemplo.com/imagem.jpg">
<meta property="og:url" content="https://exemplo.com/pagina">
<meta property="og:type" content="website">
<meta property="og:site_name" content="Nome do Site">
```

#### Twitter Cards
```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@seuusuario">
<meta name="twitter:title" content="Título da Página">
<meta name="twitter:description" content="Descrição da página">
<meta name="twitter:image" content="https://exemplo.com/imagem.jpg">
```

### Favicon

```html
<!-- Favicon tradicional -->
<link rel="icon" type="image/x-icon" href="/favicon.ico">

<!-- Favicons modernos -->
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">

<!-- Apple Touch Icon -->
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">

<!-- Manifest para PWA -->
<link rel="manifest" href="/site.webmanifest">
```

---

## ♿ Acessibilidade

Tornar seu site acessível é fundamental para incluir todos os usuários.

### Atributos de Acessibilidade

```html
<!-- Texto alternativo para imagens -->
<img src="grafico.jpg" alt="Gráfico mostrando crescimento de 20% nas vendas">

<!-- Imagem decorativa -->
<img src="decoracao.jpg" alt="" role="presentation">

<!-- Labels para formulários -->
<label for="usuario">Nome de usuário:</label>
<input type="text" id="usuario" name="usuario">

<!-- Ou usando aria-label -->
<input type="search" aria-label="Buscar produtos">

<!-- Títulos para tabelas -->
<table>
    <caption>Vendas por região em 2024</caption>
    <th scope="col">Região</th>
    <th scope="col">Vendas</th>
</table>

<!-- Links descritivos -->
<a href="relatorio.pdf" aria-describedby="pdf-info">
    Baixar relatório
    <span id="pdf-info">(PDF, 2MB)</span>
</a>

<!-- Botões acessíveis -->
<button aria-label="Fechar modal">×</button>

<!-- Landmarks -->
<nav aria-label="Navegação principal">
<main aria-label="Conteúdo principal">
<aside aria-label="Barra lateral">
```

### ARIA (Accessible Rich Internet Applications)

```html
<!-- Estados -->
<button aria-pressed="false">Botão Toggle</button>
<div aria-expanded="false">Menu colapsado</div>
<input aria-invalid="true" aria-describedby="erro">
<span id="erro">Campo obrigatório</span>

<!-- Propriedades -->
<div role="tablist">
    <button role="tab" aria-selected="true">Aba 1</button>
    <button role="tab" aria-selected="false">Aba 2</button>
</div>

<!-- Live regions -->
<div aria-live="polite" id="status"></div>
<div aria-live="assertive" id="erro-critico"></div>

<!-- Relacionamentos -->
<input aria-describedby="ajuda">
<div id="ajuda">Digite apenas números</div>
```

### Estrutura Acessível

```html
<!-- Hierarquia correta de títulos -->
<h1>Título Principal</h1>
    <h2>Seção A</h2>
        <h3>Subseção A.1</h3>
        <h3>Subseção A.2</h3>
    <h2>Seção B</h2>

<!-- Skip links -->
<a href="#main" class="skip-link">Pular para conteúdo principal</a>

<!-- Focus visível -->
<style>
:focus {
    outline: 2px solid #007bff;
    outline-offset: 2px;
}
</style>
```

---

## ✅ Boas Práticas

### 1. Semântica e Estrutura

```html
<!-- ✅ Bom: Semântico -->
<article>
    <header>
        <h1>Título do Artigo</h1>
        <time>15/01/2025</time>
    </header>
    <p>Conteúdo do artigo...</p>
</article>

<!-- ❌ Ruim: Não semântico -->
<div class="artigo">
    <div class="titulo">Título do Artigo</div>
    <div class="data">15/01/2025</div>
    <div class="conteudo">Conteúdo do artigo...</div>
</div>
```

### 2. Atributos Obrigatórios

```html
<!-- Imagens sempre com alt -->
<img src="foto.jpg" alt="Descrição da foto">

<!-- Formulários com labels -->
<label for="nome">Nome:</label>
<input type="text" id="nome" name="nome">

<!-- Links externos com segurança -->
<a href="https://site-externo.com" target="_blank" rel="noopener noreferrer">
    Link externo
</a>
```

### 3. Performance

* Implemente técnicas de otimização como lazy loading, preload e DNS prefetch.
* use o atributo `loading="lazy"` para imagens que não precisam ser carregadas imediatamente.
* Use `preload` para carregar fontes e scripts críticos antes do render.
* Use `dns-prefetch` para otimizar requisições de recursos externos.
* Evite inline styles e scripts pesados no HTML.

```html
<!-- Carregamento lazy de imagens -->
<img src="imagem.jpg" alt="Descrição" loading="lazy">

<!-- Preload de recursos importantes -->
<link rel="preload" href="fonte-importante.woff2" as="font" type="font/woff2">

<!-- DNS prefetch -->
<link rel="dns-prefetch" href="//fonts.googleapis.com">
```

### 4. Validação

- Use sempre `<!DOCTYPE html>`
- Feche todas as tags que precisam ser fechadas
- Use aspas nos atributos
- Mantenha hierarquia correta de títulos
- Valide seu HTML no [W3C Validator](https://validator.w3.org/)

---

## 💡 Exemplos Práticos

### 1. Card de Produto

```html
<article class="produto-card">
    <figure>
        <img src="produto.jpg" alt="Smartphone XYZ" loading="lazy">
        <figcaption class="visuallyhidden">Imagem do produto</figcaption>
    </figure>
    
    <div class="produto-info">
        <h3>Smartphone XYZ</h3>
        <p class="preco">
            <span class="sr-only">Preço:</span>
            <data value="899.99">R$ 899,99</data>
        </p>
        <p class="descricao">Smartphone com 128GB de armazenamento...</p>
        
        <button type="button" aria-describedby="produto-1-info">
            Adicionar ao carrinho
        </button>
        <div id="produto-1-info" class="sr-only">
            Smartphone XYZ por R$ 899,99
        </div>
    </div>
</article>
```

### 2. Modal Acessível

```html
<div class="modal" role="dialog" aria-labelledby="modal-titulo" aria-hidden="true">
    <div class="modal-content">
        <header class="modal-header">
            <h2 id="modal-titulo">Confirmar Ação</h2>
            <button type="button" class="modal-close" aria-label="Fechar modal">
                ×
            </button>
        </header>
        
        <div class="modal-body">
            <p>Tem certeza que deseja excluir este item?</p>
        </div>
        
        <footer class="modal-footer">
            <button type="button" class="btn btn-secondary">Cancelar</button>
            <button type="button" class="btn btn-danger">Excluir</button>
        </footer>
    </div>
</div>
```

### 3. Navegação Breadcrumb

```html
<nav aria-label="Breadcrumb">
    <ol class="breadcrumb">
        <li><a href="/">Início</a></li>
        <li><a href="/produtos">Produtos</a></li>
        <li><a href="/produtos/eletronicos">Eletrônicos</a></li>
        <li aria-current="page">Smartphones</li>
    </ol>
</nav>
```

### 4. Tabela Responsiva

```html
<div class="tabela-container">
    <table>
        <caption>Vendas do primeiro trimestre de 2025</caption>
        <thead>
            <tr>
                <th scope="col">Mês</th>
                <th scope="col">Produto A</th>
                <th scope="col">Produto B</th>
                <th scope="col">Total</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <th scope="row">Janeiro</th>
                <td data-label="Produto A">1.200</td>
                <td data-label="Produto B">800</td>
                <td data-label="Total">2.000</td>
            </tr>
            <tr>
                <th scope="row">Fevereiro</th>
                <td data-label="Produto A">1.100</td>
                <td data-label="Produto B">900</td>
                <td data-label="Total">2.000</td>
            </tr>
        </tbody>
    </table>
</div>
```

---

## 🔧 Ferramentas Úteis

### Validação e Teste

- **[W3C HTML Validator](https://validator.w3.org/)** - Valida código HTML
- **[WAVE](https://wave.webaim.org/)** - Testa acessibilidade
- **[Lighthouse](https://developers.google.com/web/tools/lighthouse)** - Auditoria completa
- **[HTML5 Outliner](https://gsnedders.html5.org/outliner/)** - Verifica estrutura

### Extensões VS Code

- **HTML CSS Support** - Autocomplete de CSS em HTML
- **Auto Rename Tag** - Renomeia tags automaticamente
- **HTML Snippets** - Snippets úteis para HTML
- **Live Server** - Servidor local para desenvolvimento

### Geradores Online

- **[HTML Generator](https://html-generator.com/)** - Gera código HTML
- **[Meta Tags Generator](https://metatags.io/)** - Gera meta tags
- **[Favicon Generator](https://favicon.io/)** - Cria favicons

---

## 📚 Recursos de Aprendizado

- **[MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTML)** - Documentação oficial
- **[HTML Reference](https://htmlreference.io/)** - Referência visual
- **[Can I Use](https://caniuse.com/)** - Compatibilidade de navegadores
- **[HTML5 Spec](https://html.spec.whatwg.org/)** - Especificação oficial

---

## ✅ Checklist HTML

### Estrutura
- [ ] DOCTYPE declarado 
- [ ] Atributo lang definido 
- [ ] Meta charset UTF-8
- [ ] Meta viewport para responsividade
- [ ] Título descritivo (< 60 caracteres)

### Semântica
- [ ] Uso correto de elementos semânticos (header, nav, main, article, section, aside, footer)
- [ ] Uso adequado de headings (h1, h2, h3, etc.)
- [ ] Hierarquia de títulos lógica 
- [ ] Um h1 por página 
- [ ] Landmarks definidos (header, nav, main, footer) 

### Acessibilidade
- [ ] Alt text em todas as imagens 
- [ ] Labels em todos os inputs
- [ ] Contraste adequado
- [ ] Navegação por teclado
- [ ] Estados de foco visíveis

### Performance
- [ ] Imagens otimizadas 
- [ ] Loading lazy quando apropriado
- [ ] Meta tags de SEO
- [ ] Links externos com rel apropriado

### Validação
- [ ] HTML válido (W3C Validator) [link](https://validator.w3.org/)
- [ ] Teste de acessibilidade (WAVE) [link](https://wave.webaim.org/)
- [ ] Teste em múltiplos navegadores
- [ ] Teste em dispositivos móveis

---

*Este guia fornece uma base sólida para criar documentos HTML bem estruturados, semânticos e acessíveis. Pratique criando diferentes tipos de conteúdo e sempre valide seu código!*
