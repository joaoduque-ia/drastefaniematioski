# Página própria no lugar do Linktree (versão 2, 05/11/2026)

## O que mudou da versão 1 para a 2

- Página principal reduzida em 05/11 a pedido de João: só os dois botões de agendamento, sem valores, duração ou seções de conteúdo; essas informações viraram respostas rápidas do WhatsApp (`whatsapp/respostas-rapidas.txt`). O rodapé mantém endereço, aviso de privacidade, termo da teleconsulta, Instagram e e-mail.
- Três páginas em vez de uma: `index.html` (página principal), `privacidade.html` (aviso de privacidade, LGPD) e `teleconsulta.html` (termo de consentimento para teleconsulta, Resolução CFM nº 2.314/2022).
- Seções novas na principal: "Sobre a médica", "Perguntas frequentes" (sete perguntas) e o que levar à consulta.
- Barra fixa "Agendar pelo WhatsApp" no celular, que aparece quando a lista de botões sai da tela.
- Origem do contato: aberta como `/?o=ig`, `/?o=google`, `/?o=doctoralia`, `/?o=cartao`, `/?o=qr` ou `/?o=ads`, a página acrescenta "Vim pelo Instagram" (e assim por diante) à mensagem do WhatsApp. Nada é gravado no navegador do paciente.
- Busca e compartilhamento: título e descrição por página, dados estruturados (schema.org, tipo Physician) com endereço e contatos, imagem de compartilhamento `og-image.png` (1200 x 630), favicons (`favicon.svg`, `favicon-32.png`, `favicon.ico`, `apple-touch-icon.png`, `favicon-192.png`, `favicon-512.png`).
- Rodapé com links para as três páginas. Modo escuro com os mesmos tons da papelaria.
- Paleta 2 (05/11, a partir do logotipo digital): papel quase branco, ouro champanhe, cartão do topo com moldura dupla e retângulo dourado na base, nome em caixa alta com filete, títulos de seção em caixa alta dourada, Tenor Sans em tudo. Detalhes em `brand/paleta.md`.
- Frase de posicionamento trocada para "Medicina baseada em evidências, com tempo para ouvir, compreender e cuidar" (a anterior insinuava resultado; ver docs/06, seção 2.2). A antiga está em comentário no HTML.
- Botões "Perfil na Doctoralia" e "Perfil no Google" já escritos, em comentário, para ativar quando os perfis existirem.

O que veio do Linktree de referência (Dr. Vitor Kern): a estrutura de três ações no topo (consulta presencial, consulta online, localização), as mensagens pré-preenchidas do WhatsApp e o link do Google Maps. O que a página acrescenta: identificação obrigatória da CFM, conteúdo indexável, aviso de privacidade, termo da teleconsulta e domínio próprio.

## Antes de publicar

1. Número do WhatsApp Business já inserido: 5581992613573 nos três links e na constante do script.
2. Designação profissional: a linha de identificação do cabeçalho e a seção "Sobre a médica" têm comentários HTML com as fórmulas prontas (com RQE, com pós-graduação cadastrada e sem nenhum dos dois). Escolher uma depois da conferência no CRM-PE.
3. Valor da consulta subsequente: hoje R$ 600,00 na seção "Investimento"; o manual diz R$ 500,00. Confirmar com a Stefanie.
4. Domínio: as páginas apontam para `https://drastefaniematioski.com.br/` nas tags `canonical`, `og:url`, `og:image` e no JSON-LD. Se o domínio escolhido for outro, substituir nas três páginas.
5. Telefone no JSON-LD de `index.html`: trocar `+55 81 99261-3573` pelo número.
6. Revisão jurídica de João: `privacidade.html` (encarregado, CNPJ se PJ) e `teleconsulta.html`.
7. Opcional: acrescentar estacionamento, recepção e acessibilidade em "Onde fica", depois de confirmar com o Esmere.

## Como publicar

GitHub Pages (gratuito), no repositório público `joaoduque-ia/drastefaniematioski`, com o conteúdo desta pasta na raiz da branch `main`. A pasta já traz `CNAME` (domínio), `.nojekyll`, `robots.txt` e `sitemap.xml`.

1. Enviar o conteúdo de `site/` para a branch `main` do repositório.
2. No GitHub, Settings, Pages: fonte "Deploy from a branch", branch `main`, pasta `/ (root)`. Sem domínio, a página já abre em `https://joaoduque-ia.github.io/drastefaniematioski/`.
3. Registrar o domínio no Registro.br (disponibilidade conferida em 05/11/2026 em docs/06, seção 3.1). Em Editar zona DNS (modo avançado), criar os registros abaixo, conforme a [documentação do GitHub Pages](https://docs.github.com/pt/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site):

   | Tipo | Nome | Valor |
   |---|---|---|
   | A | (raiz) | 185.199.108.153 |
   | A | (raiz) | 185.199.109.153 |
   | A | (raiz) | 185.199.110.153 |
   | A | (raiz) | 185.199.111.153 |
   | AAAA | (raiz) | 2606:50c0:8000::153 |
   | AAAA | (raiz) | 2606:50c0:8001::153 |
   | AAAA | (raiz) | 2606:50c0:8002::153 |
   | AAAA | (raiz) | 2606:50c0:8003::153 |
   | CNAME | www | joaoduque-ia.github.io |

   Depois da propagação, em Settings, Pages: domínio personalizado `drastefaniematioski.com.br` e "Enforce HTTPS".
4. Testar no celular: os três botões do WhatsApp abrem o aplicativo com a mensagem; o mapa abre o Esmere; `privacidade.html` e `teleconsulta.html` abrem pelo rodapé; abrir `/?o=ig` e conferir que a mensagem traz "Vim pelo Instagram".

Depois da publicação: cadastrar a página no Google Search Console, colocar `/?o=ig` na bio do Instagram, `/?o=google` no Perfil da Empresa e `/?o=doctoralia` na Doctoralia (docs/06, seção 3.3). As respostas rápidas /termo, /privacidade e /confirmacao do WhatsApp (docs/07) recebem os links das páginas publicadas.

## Como editar

As páginas são HTML puro. A fonte Tenor Sans (equivalente livre da Optima da papelaria) fica em `site/fontes/` e é carregada localmente, com fallback para Optima, Candara e Gill Sans; a pré-visualização no Claude usa a mesma fonte pelo Google Fonts. O monograma é vetor inline com degradê de ouro. O estilo está no início de cada arquivo e é o mesmo nas três páginas; ao mudar uma cor ou fonte, repetir nas outras duas. Paleta e tipografia em `brand/paleta.md`.
