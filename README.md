# Drumlabooh Kit Maker

Uma ferramenta web para montar kits de bateria no navegador, criar o mapeamento MIDI e exportar um pacote pronto em ZIP com samples, `drumkit.txt` e imagem do kit.

## Acessar o app

Abra o [Drumlabooh Kit Maker no GitHub Pages](https://pablito331.github.io/drumlabooh-kit-maker/). Não é necessário instalar nada: o app funciona no navegador e processa os arquivos localmente.

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

1. Abra o [app no GitHub Pages](https://pablito331.github.io/drumlabooh-kit-maker/) ou, se preferir, abra `index.html` no navegador.
2. Escolha como começar:
   - **Kit General MIDI:** mantenha `General MIDI (GM) - Percussion 35-81` e clique em `Aplicar`.
   - **Kit do zero:** selecione `Personalizado - começar vazio` e clique em `Aplicar`. Confirme a remoção dos slots existentes, se solicitado. Use `+ Novo slot` para escolher uma peça GM ou criar uma peça personalizada informando nome e nota MIDI.
3. Para adicionar sons manualmente, clique em `+ samples` no slot desejado ou arraste arquivos de áudio do computador para o slot. Edite o nome, a nota MIDI e o modo de seleção do slot conforme necessário.
4. Para importar um kit, clique em `Importar kit SFZ / Hydrogen...`:
   - **SFZ:** selecione o arquivo `.sfz` e os samples referenciados por ele.
   - **Hydrogen:** selecione o arquivo `.h2drumkit`/ZIP ou a pasta descompactada que contém `drumkit.xml` e os samples.
   - A importação tenta associar cada instrumento ao slot mais compatível pelo nome e pela nota MIDI. Se houver uma associação ambígua, escolha o slot correto ou ignore o instrumento na janela exibida. A importação preenche slots compatíveis; para kits personalizados, crie antes os slots que deseja usar.
5. Organize as camadas dentro de cada slot. No modo **Velocity (fraco → forte)**, camadas marcadas `auto` dividem igualmente a faixa MIDI 0-127: duas camadas recebem metade cada, três recebem um terço cada, e assim por diante. Você pode editar os limites mínimo e máximo de cada camada. Use `↑`/`↓` ou arraste para mudar a ordem; arraste uma camada para outro slot para movê-la. Também estão disponíveis os modos **Round robin** e **Aleatório**.
6. Opcionalmente, adicione uma imagem do kit e informe o nome do kit.
7. Clique em `Baixar kit (.zip)` para exportar o pacote.

Os arquivos são processados no navegador e não são enviados para um servidor. A página não guarda o projeto: baixe o ZIP antes de fechar ou recarregar o app.

## Estrutura do pacote exportado

O ZIP gerado contém:

- `drumkit.txt` com o mapeamento final
- `drumkit.sfz` com as faixas de velocity preservadas para abrir diretamente no Drumlabooh
- arquivos de áudio organizados por nome
- imagem do kit, quando houver

O formato `drumkit.txt` reparte as velocidades igualmente entre as camadas. Para manter as faixas originais importadas de SFZ ou Hydrogen, abra o `drumkit.sfz` gerado.

## Observação

Este projeto foi pensado para funcionar localmente e em páginas estáticas. Ele não depende de backend e não armazena dados em um servidor.

## Licença

Este projeto está disponível para uso pessoal e estudo. Ajuste a licença conforme sua necessidade antes de publicar em produção ou distribuir publicamente.
