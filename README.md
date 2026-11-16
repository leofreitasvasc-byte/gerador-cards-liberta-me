# Gerador de convites · Ministério Liberta-me

Site estático (sem servidor, sem login, sem custo). Tu abre o link, preenche os campos e baixa os PNGs prontos:
- **Story / status do WhatsApp:** 1080 × 1920
- **Feed / conversas do WhatsApp:** 1080 × 1350

Layout, cores, fontes e logo são fixos. Só mudam: data, horário, local, endereço, investimento, chamada, logo da igreja parceira e foto dos preletores.

## Publicar no GitHub Pages (uma vez)
1. Crie um repositório público, por exemplo `liberta-me-convites`.
2. Envie todo o conteúdo desta pasta para a raiz do repositório (`index.html`, `support.js`, `assets/`, `README.md`).
3. Em **Settings → Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`. Salve.
4. Em cerca de 1 minuto o site fica em `https://SEU-USUARIO.github.io/liberta-me-convites/`.
5. Manda esse link pro ministério. Funciona no computador e no celular.

## Usar sem publicar (na própria máquina)
Não dá pra só dar dois cliques no `index.html`: o navegador bloqueia algumas funções em arquivo local. Roda um servidor simples na pasta:
- **VS Code:** extensão *Live Server* → botão direito no `index.html` → *Open with Live Server*.
- **Terminal:** `npx serve .` e abre o endereço que aparecer.

Mesmo assim precisa de internet (fontes, exportação e recorte vêm de CDN).

## Como funciona
- Tudo roda no navegador de quem usa. Nada é enviado a servidor.
- Os campos de texto ficam salvos no navegador para o próximo evento.
- **Foto dos preletores:** manda a montagem com todos juntos. O recorte das pessoas é automático (biblioteca @imgly/background-removal, roda no próprio navegador). Na primeira vez baixa o modelo e leva cerca de um minuto. Se falhar, a foto fica só dentro do arco.
- **Exportação:** html-to-image, com a fonte Jost embutida no PNG.

## Dependências externas (CDN)
- Google Fonts (Archivo, Jost)
- html-to-image 1.11.11 (jsDelivr)
- @imgly/background-removal 1.5.5 (jsDelivr + staticimgly.com)

Sem internet o gerador não funciona.

## Mudar o modelo
O layout está em `index.html`. Qualquer mudança visual deve passar pelo MIV do Liberta-me antes: a regra deste sistema é que ninguém redesenha o convite a cada evento.

Desenvolvido por Vereda Gestão Integrada.
