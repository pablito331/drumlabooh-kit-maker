# Drumlabooh Kit Maker

Uma ferramenta web para montar kits de bateria no navegador, criar o mapeamento MIDI e exportar um pacote pronto em ZIP com samples, `drumkit.txt` e imagem do kit.

## O que é

O Drumlabooh Kit Maker ajuda a organizar sons de bateria em um kit de forma rápida e simples, sem precisar instalar nenhuma aplicação local. O fluxo é 100% no navegador e os arquivos nunca são enviados para um servidor.

## Funcionalidades

- Mapeamento MIDI por presets GM, AVL, BFD, EZ Drummer, Addictive Drums e Drumlabooh Automático
- Criação e edição de slots por nota
- Adição de múltiplos samples por slot
- Ordenação de camadas por intensidade, round robin e aleatório
- Arraste e solte de arquivos de áudio diretamente na interface
- Upload de imagem do kit
- Exportação em `.zip` com os arquivos prontos para uso

## Como usar

1. Abra o arquivo `index.html` no navegador.
2. Escolha um preset de mapeamento MIDI.
3. Ajuste as notas, nomes e modos dos slots.
4. Arraste seus arquivos de áudio para cada slot.
5. Opcionalmente, adicione uma imagem do kit.
6. Clique em `Baixar kit (.zip)`.

## Estrutura do pacote exportado

O ZIP gerado contém:

- `drumkit.txt` com o mapeamento final
- arquivos de áudio organizados por nome
- imagem do kit, quando houver

## GitHub Pages

Como o projeto é estático, ele pode ser publicado facilmente no GitHub Pages.

### Passos básicos

1. Faça upload do projeto para um repositório no GitHub.
2. Vá em `Settings` → `Pages`.
3. Escolha a branch principal como origem.
4. Salve e aguarde a publicação.

## Observação

Este projeto foi pensado para funcionar localmente e em páginas estáticas. Ele não depende de backend e não armazena dados em um servidor.

## Licença

Este projeto está disponível para uso pessoal e estudo. Ajuste a licença conforme sua necessidade antes de publicar em produção ou distribuir publicamente.
