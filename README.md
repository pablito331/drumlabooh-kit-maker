# Drumlabooh Kit Maker

Uma ferramenta web para montar kits de bateria no navegador, criar o mapeamento MIDI e exportar um pacote pronto em ZIP com samples, `drumkit.txt` e imagem do kit.

## O que é

O Drumlabooh Kit Maker ajuda a organizar sons de bateria em um kit de forma rápida e simples, sem precisar instalar nenhuma aplicação local. O fluxo é 100% no navegador e os arquivos nunca são enviados para um servidor.

## Funcionalidades

- Mapeamento de percussão General MIDI padrão (notas 35-81) ou criação de kit personalizado vazio
- Criação e edição de slots por nota
- Adição de múltiplos samples por slot
- Ordenação de camadas por intensidade, round robin e aleatório
- Arraste e solte de arquivos de áudio diretamente na interface
- Upload de imagem do kit
- Exportação em `.zip` com os arquivos prontos para uso

## Como usar

1. Abra o arquivo `index.html` no navegador.
2. Use o mapeamento de percussão General MIDI padrão (notas 35-81) ou selecione `Personalizado - começar vazio` e clique em `Aplicar` para montar um kit do zero.
3. Clique em `Aplicar` para ativar o mapeamento escolhido.
4. Clique em `Importar kit SFZ / Hydrogen...` e escolha selecionar arquivos ou uma pasta descompactada. Para SFZ, selecione o `.sfz` junto com os samples referenciados. Para Hydrogen, selecione o `.h2drumkit`/ZIP ou a pasta com `drumkit.xml` e os samples. A importação acontece no navegador.
5. Os samples são associados à peça mais compatível no mapeamento General MIDI, usando o nome do instrumento e a nota MIDI em conjunto. No SFZ, as regiões e faixas de velocidade são usadas para ordenar as camadas. Kits Hydrogen usam o nome, `midiOutNote` e as camadas do `drumkit.xml`. Se o nome e a nota indicarem articulações diferentes, a peça aparece em uma janela para você escolher o slot ou ignorá-la.
6. Em um kit personalizado, use `+ Novo slot` para escolher uma peça General MIDI ou informar seu próprio nome e nota MIDI. Ajuste notas, nomes e modos dos slots. Quando houver várias camadas, o app divide automaticamente a faixa 0-127 igualmente entre os samples marcados `auto`; edite os limites mínimo e máximo nos campos de cada camada se desejar. Use as setas `↑` e `↓` ou arraste um sample para reordenar as camadas; arraste-o para outro slot para movê-lo. As faixas de velocity acompanham cada sample. Também é possível arrastar arquivos de áudio do computador para um slot.
7. Opcionalmente, adicione uma imagem do kit.
8. Clique em `Baixar kit (.zip)`.

## Estrutura do pacote exportado

O ZIP gerado contém:

- `drumkit.txt` com o mapeamento final
- `drumkit.sfz` com as faixas de velocity preservadas para abrir diretamente no Drumlabooh
- arquivos de áudio organizados por nome
- imagem do kit, quando houver

O formato `drumkit.txt` reparte as velocidades igualmente entre as camadas. Para manter as faixas originais importadas de SFZ ou Hydrogen, abra o `drumkit.sfz` gerado.

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
