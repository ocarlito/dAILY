# Repository Guidelines

## Project Structure & Module Organization
- `public/` contém o site estático pronto para publicação. O arquivo `public/index.html` concentra o layout, estilos embutidos e scripts; adicione novos ativos em `public/assets/` e referencie-os com caminhos relativos à raiz para compatibilidade com o roteamento do Pages.
- A implantação ocorre via Cloudflare Pages; nenhuma configuração adicional é versionada. Ajustes de build (branch, pasta, variáveis) são feitos direto no painel e devem ser documentados nas PRs quando alterados.

## Build, Test & Development Commands
- `npx @cloudflare/wrangler pages dev public --port 8788` inicia um preview local com comportamento equivalente ao Pages (inclui SPA fallback). Use-o para validar mudanças estruturais.
- `npx serve public` serve o diretório de forma rápida para revisões HTML/CSS quando o preview completo não é necessário.
- Deploys são disparados pelo Pages a cada push na branch monitorada. Para publicar manualmente, utilize "Create Deployment" no painel apontando para o branch desejado.

## Coding Style & Naming Conventions
- Preserve a indentação com 4 espaços e atributos HTML em lowercase. Prefira tags semânticas (`section`, `main`, `article`) e reutilize padrões existentes.
- Amplie o sistema de design via variáveis CSS em `:root`, evitando cores soltas. Centralize novos utilitários no topo do `<style>` para manter a visibilidade.
- Nomeie arquivos e assets em kebab-case (ex.: `daily-summary.png`) e agrupe imagens por contexto em subpastas lógicas dentro de `public/assets/`.

## Testing Guidelines
- Não há suíte automatizada. Valide o HTML via W3C Validator e execute Lighthouse (Chrome DevTools) para garantir acessibilidade e performance estáveis.
- No preview local (`wrangler pages dev`), percorra os fluxos principais: abertura inicial, rolagem, modais e links externos. Registre no PR quando algum teste manual não for executado.

## Commit & Pull Request Guidelines
- Use mensagens curtas e imperativas como no histórico (`Update canonical URL...`, `publish`). Limite o assunto a 72 caracteres e detalhe contexto adicional no corpo.
- Nas PRs, inclua: descrição objetiva, validações realizadas (comandos, navegadores), captura/screencast para mudanças visuais e vínculo com issues (`Closes #12`).
- Cite quaisquer ajustes feitos no painel do Cloudflare Pages (variáveis, build command) para manter o conhecimento rastreável.
