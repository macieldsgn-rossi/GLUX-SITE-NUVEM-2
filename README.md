# Glux · Link na bio + catálogo

Site estático (HTML, CSS e JavaScript puros). Não precisa de build nem de servidor.

## Estrutura

```
glux-site/
├── index.html            página completa (estilos e scripts embutidos)
├── img/                  fotos das peças e da coleção (WebP)
├── favicon.svg           ícone da aba (troca sozinho no modo escuro)
├── apple-touch-icon.png  ícone ao salvar na tela inicial do celular
└── og-image.jpg          prévia do link no WhatsApp e no Instagram
```

## Deploy

**Vercel:** vercel.com → Add New → Project → arraste a pasta `glux-site` (ou importe do GitHub). Framework: "Other". Sem comando de build. Output: a própria pasta.

**Netlify:** app.netlify.com/drop → arraste a pasta `glux-site`.

**Hospedagem comum (cPanel/FTP):** envie o conteúdo de `glux-site` para a pasta `public_html`.

Depois do deploy, troque no `index.html` a linha `og:image` para o endereço completo (ex.: `https://glux.com.br/og-image.jpg`), para a prévia aparecer em todos os apps.

## Onde editar

Tudo fica no `<script>` no final do `index.html`:

- `WHATSAPP` → número que recebe os pedidos (55 + DDD + número, só dígitos).
- `PRODUTOS` → nome, categoria, preço, selo ("Novo", "Mais vendido") e foto de cada peça.
- `VARIACOES` → comprimentos e aros por categoria.
- `ENTREGAS` e `PAGTOS` → formas de entrega e de pagamento.

Para trocar uma foto, coloque o arquivo em `img/` e aponte o campo `img` do produto para ele. Formato recomendado: WebP, até 1000 px no lado maior.

Textos entre colchetes, como `[cidade/região]`, `[X]x`, a política de trocas e o CNPJ, ainda precisam dos dados reais.

## Como o pedido funciona

1. O cliente escolhe a peça e preenche as 4 etapas.
2. O botão final abre o WhatsApp com a mensagem do pedido pronta.
3. O PDF do resumo é gerado no navegador (biblioteca jsPDF via cdnjs) e baixado no aparelho. O WhatsApp não aceita anexar arquivos por link, então o cliente anexa o PDF na conversa se quiser.
4. O story é gerado no navegador. No celular, o botão abre o menu de compartilhar do sistema, onde o cliente escolhe Instagram → Story. No computador, a imagem é baixada.

Os dados do cliente ficam salvos só no navegador dele, para agilizar a próxima compra. Nada é enviado a servidor.

- `media/` — vídeo de fundo da seção "Ficou com alguma dúvida?" (sem áudio) e pôster.
