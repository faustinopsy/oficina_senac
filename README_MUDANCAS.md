# Relatório de Desenvolvimento - Oficina Senac
**Data:** 30 de Abril de 2026
**Objetivo:** Modernização da Experiência do Usuário (UX) e Refatoração Estrutural (Modularização).

---

## 1. Sistema de Animação (Scroll Reveal)
Implementamos um efeito de "revelação" para as seções do site, onde o conteúdo surge suavemente com opacidade e movimento conforme o usuário rola a página.

### Alterações Realizadas:
- **CSS (`assets/css/microframework.css`):**
  - Adicionadas as classes `.revelar` (estado inicial invisível e deslocado 30px para baixo) e `.ativo` (estado final visível na posição original).
  - Utilização de `transition: all 0.8s ease-out` para garantir a fluidez do movimento.
- **JavaScript (`assets/js/script.js`):**
  - Implementação da API **IntersectionObserver**, que monitora de forma performática quando um elemento entra na área visível da tela.
  - Toda a lógica foi escrita em **português** para facilitar o entendimento (variáveis como `elementosRevelar`, `opcoesRevelacao`, etc).
  - Aplicado exclusivamente às seções da `index.html`, conforme solicitado.

---

## 2. Componentização da Navegação (Navbar)
O maior ganho técnico do dia foi a eliminação de código redundante através da criação de um componente JavaScript para o menu.

### Estrutura do Novo Sistema:
- **Arquivo Central (`assets/js/navbar.js`):**
  - Este arquivo agora é a "Fonte Única da Verdade" (Single Source of Truth) para o menu. 
  - Contém o HTML da **Navbar Principal** (Logo, contatos e redes sociais) e da **Navbar Secundária** (Links de navegação).
  - **Lógica de Link Ativo:** O script detecta automaticamente em qual página o usuário está e aplica a classe de destaque (`bem-navbar__link--active`) ao link correspondente.
- **Refatoração do HTML:**
  - As páginas `index.html`, `projetos.html` e `servicos.html` tiveram centenas de linhas de código de menu removidas.
  - Foram substituídas por containers leves: `<div id="navbar-principal"></div>` e `<div id="navbar-secundaria"></div>`.

---

## 3. Arquivos Modificados
Abaixo, a lista de arquivos que receberam as atualizações:

| Arquivo | Descrição da Mudança |
| :--- | :--- |
| `index.html` | Inserção de containers dinâmicos e classes `.revelar`. |
| `projetos.html` | Substituição de menu estático por containers dinâmicos. |
| `servicos.html` | Substituição de menu estático por containers dinâmicos. |
| `assets/js/navbar.js` | **[Novo]** Arquivo que renderiza os menus em todo o site. |
| `assets/js/script.js` | Adição da lógica de animação por scroll. |
| `assets/css/microframework.css` | Adição dos estilos globais de animação e transição. |
| `assets/css/style.css` | Limpeza de classes de teste para manter o arquivo organizado. |

---

## 4. Benefícios Práticos
1. **Facilidade de Manutenção:** Para adicionar um novo link no menu, você só precisa editar o arquivo `navbar.js` uma única vez.
2. **Consistência Visual:** O menu será exatamente o mesmo em todas as páginas, sem risco de esquecer de atualizar algum arquivo.
3. **UX Premium:** O site agora tem um aspecto moderno e interativo, comparável a sites de alto padrão.
4. **Performance:** O uso de `IntersectionObserver` evita o consumo excessivo de processamento que eventos de scroll antigos causavam.

---
**Status da Sessão:** Finalizado com sucesso. 🚀
