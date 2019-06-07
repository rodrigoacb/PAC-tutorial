# Tutorial de Packmol

## Packmol: Donwload e instalação

Primeiramente vamos baixar o programa, isso pode ser feito diretamente do [site](http://m3g.iqm.unicamp.br/packmol/download.shtml) ou
executando o seguinte comando:

`wget https://github.com/leandromartinez98/packmol/archive/18.169.tar.gz`

Para instala-lo basta descompactar e executar o comando make dentro de sua pasta **caso tenha baixado pelo wget substitua pelo nome do arquivo baixado.**

```
tar -xvzf packmol.tar.gz
cd packmol
chmod +x configure
./configure
make
```

_Obs: o nome da pasta do packmol mudará dependendo da versão ou do local de download, adapte o comando ao seu caso. Isso pode ser feito
verificando o nome da pasta a partir do comando `ls`

O packmol é executado com a seguinte sintaxe: `./packmol < packmol.inp` para isso precisamos antes criar o arquivo de input.

#### Input file 
O packmol é otimizado para gerar configurações iniciais a partir de topografias basicas das moléculas. Ele trabalha com dois principais
tipos de arquivos: xyz e pdb (Protein Data Bank). Para configurações basicas o parâmetro mais importante a ser definido é a tolerância
que define a distância minima em Angstrons entre duas partículas.

```   
    # Configuração inicial para a uma caixa com 1000 moléculas de água.
    tolerance 2.0
    # Tipo de arquivo de input e output xyz
    filetype xyz
    # Nome do arquivo de output
    output waterout.xyz
    # 1000 moléculas de água serão postas dentro de uma caixa de lados 0. - 40.
    structure water.xyz
    number 1000 
    inside box 0. 0. 0. 40. 40. 40. 
    end structure
```
Como complemento deste arquivo a topografia das moléculas de água precisam estar definidas no arquivo informado, neste caso _water.xyz_.

```
    # Define-se o número de átomos ou sítios presentes na molécula e suas coordenadas.
    3 
    water
    H            9.625597       6.787278      12.673000 
    H            9.625597       8.420323      12.673000 
    O           10.203012       7.603800      12.673000 
```

Para gerar uma configuração a partir desses arquivos a chamada do packmol é feita com comando:

`   ./packmol < packmol.inp`

Caso encontre um erro, você precisará definir o caminho do diretório no qual o executavel do packmol se encontra. indo no diretório que
você instalou o packmol use o comando `pwd` e você precisará usar esse caminho na chamada da função. Por exemplo:

`   ~/Programs/packmol/./packmol < ./packmol.inp`

Como alternativa pode-se adicionar um alias no arquivo .bashrc especificando o caminho do comando.

`  alias packmol='~/Programs/packmol/./packmol'`

Agora tente fazer uma molécula de sítio unico, boa sorte!
