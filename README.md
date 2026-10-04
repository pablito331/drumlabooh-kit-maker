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
2. O app abre sem slots. Escolha como começar:
   - **Kit General MIDI:** selecione `General MIDI (GM) - Percussion 35-81` e clique em `Aplicar`.
   - **Kit do zero:** selecione `Personalizado - começar vazio` e clique em `Aplicar`, ou use `+ Novo slot` diretamente. Use `+ Novo slot` para escolher uma peça GM ou criar uma peça personalizada informando nome e nota MIDI. Se houver slots existentes, confirme a remoção quando solicitado.
3. Para adicionar sons manualmente, clique em `+ samples` no slot desejado ou arraste arquivos de áudio do computador para o slot. Edite o nome, a nota MIDI e o modo de seleção do slot conforme necessário.
4. Para importar um kit, clique em `Importar kit SFZ / Hydrogen...` e selecione a pasta do kit. Se houver mais de um arquivo SFZ, escolha qual importar; arquivos referenciados por `#include` e samples em subpastas ou arquivos compactados são procurados automaticamente. Kits Hydrogen (`drumkit.xml`) são detectados automaticamente.
   - **Atenção:** a importação ainda não é 100% precisa e pode apresentar erros de mapeamento ou camadas. Confira cuidadosamente os slots e samples importados antes de exportar; use com cautela.
   - Quando uma faixa contém variações aleatórias `lorand`/`hirand`, o `drumkit.txt` inclui uma amostra representativa por faixa, mas divide velocity igualmente. Abra `drumkit.sfz` para preservar os limites originais de velocity com uma amostra representativa por faixa. O arquivo `drumkit-variants.sfz` inclui todas as variações aleatórias para outros players SFZ; o Drumlabooh não suporta esses opcodes.
   - A importação tenta associar cada instrumento ao slot mais compatível pelo nome e pela nota MIDI. Se houver uma associação ambígua, escolha o slot correto ou ignore o instrumento na janela exibida. A importação preenche slots compatíveis; para kits personalizados, crie antes os slots que deseja usar.
5. Organize as camadas dentro de cada slot. No modo **Velocity (fraco → forte)**, camadas marcadas `auto` dividem igualmente a faixa MIDI 0-127: duas camadas recebem metade cada, três recebem um terço cada, e assim por diante. Você pode editar os limites mínimo e máximo de cada camada. Use `↑`/`↓` ou arraste para mudar a ordem; arraste uma camada para outro slot para movê-la. Também estão disponíveis os modos **Round robin** e **Aleatório**.
6. Opcionalmente, adicione uma imagem do kit e informe o nome do kit.
7. Clique em `Baixar kit (.zip)` para exportar o pacote.

Os arquivos são processados no navegador e não são enviados para um servidor. A página não guarda o projeto: baixe o ZIP antes de fechar ou recarregar o app.

## Estrutura do pacote exportado

O ZIP gerado contém:

- `drumkit.txt` com o mapeamento final
- `drumkit.sfz` com as faixas de velocity preservadas para abrir diretamente no Drumlabooh
- `drumkit-variants.sfz` com samples e variações aleatórias SFZ, quando houver
- arquivos de áudio organizados por nome
- imagem do kit, quando houver

O formato `drumkit.txt` reparte as velocidades igualmente entre as camadas. Para manter as faixas originais importadas de SFZ ou Hydrogen, abra o `drumkit.sfz` gerado.

## Observação

Este projeto foi pensado para funcionar localmente e em páginas estáticas. Ele não depende de backend e não armazena dados em um servidor.

## Estrutura dos arquivos

- `index.html` contém a estrutura da página.
- `styles.css` contém os estilos da interface.
- `app.js` contém a lógica do aplicativo.

Os três arquivos ficam na mesma pasta para que o app continue funcionando ao abrir `index.html` diretamente ou ao publicá-lo em uma hospedagem estática.

## Licença

Este projeto está disponível para uso pessoal e estudo. Ajuste a licença conforme sua necessidade antes de publicar em produção ou distribuir publicamente.
