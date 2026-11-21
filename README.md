# Gerador de convites · Ministério Liberta-me

Site estático (sem servidor, sem login, sem custo). Tu abre o link, preenche os campos e baixa os PNGs prontos:
- **Story / status do WhatsApp:** 1080 × 1920
- **Feed / conversas do WhatsApp:** 1080 × 1350

Layout, cores, fontes e logo são fixos. Tu escolhe um dos 4 modelos (Arco, Cartões, Retratos, Arcos de vidro) e muda: data, horário, local, endereço, ingresso solidário, chamada, logo da igreja parceira e quem são os preletores do evento (até 8).

## Convite em vídeo (modo Vídeo)
Fica logo abaixo dos cards. Gera o vídeo-convite de 45 s (1080 × 1920, Story/Reels/status do WhatsApp).
- **Data, horário, local, endereço e ingresso solidário** vêm dos mesmos campos dos cards.
- **Frases das cenas**: 9 campos com limite de caracteres, para nenhuma frase estourar o layout. "Voltar às frases padrão" restaura o texto original.
- **Música**: três hinos em domínio público, arranjados pela Vereda para este vídeo (*Castelo Forte*, *Santo, Santo, Santo* e *Sublime Graça*), ou **Sem música**, para pôr a música direto no Instagram. O ▶ toca um trecho.
- **Baixar vídeo com música** / **Baixar vídeo sem som**: o MP4 é gerado no próprio navegador (Chrome ou Edge do computador). Leva uns 4 minutos e a aba precisa ficar aberta.
- Arquivos do vídeo ficam em `motion/` (`motion.js`, `assets/`, `musica/`). O código-fonte da animação está no projeto Remotion da Vereda (`liberta-me-convite`), que gera de novo o `motion.js`.
- Licença: o vídeo usa o Remotion. Para empresas com até 3 pessoas é gratuito; a partir disso, o Remotion exige licença comercial.

## Banco de preletores
- Fotos em `preletores/fotos/` (PNG sem fundo, 900 × 1200, padrão do `tratar.py`).
- Lista em `preletores/preletores.json` (id, nome até 18 letras, papel, foto, ativo).
- **Preletor novo:** trata a foto com o `tratar.py`, sobe a foto em `preletores/fotos/` e o `preletores.json` atualizado. Não precisa mexer no `index.html`.
- **Tirar alguém da lista:** muda `"ativo": true` pra `false` no JSON.
- "+ Adicionar pessoa" no gerador serve pra um convidado de um evento só. Essa pessoa não fica salva.

## Publicar no GitHub Pages (uma vez)
1. Crie um repositório público, por exemplo `liberta-me-convites`.
2. Envie todo o conteúdo desta pasta para a raiz do repositório (`index.html`, `support.js`, `assets/`, `preletores/`, `motion/`, `README.md`).
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
