# curso-flexbox

Repositorio para o curso de flexbox da Alura.

O curso tem como objetivo utilizar o flexbox em uma pagina ja pronta (fornecida pelo instrutor), para deixa-la responsiva.


Aula 1

O display:inline; nao nos permite ajustar o width nem o height.

Com o display:inline-block; precisamos de "numeros magicos" para ajustar a distancia entre os elementos.

O float:left/right; acaba se tornando muito trabalhoso.

Ja o display:flex; nos permite deixar os itens lado a lado, centraliza-los verticalmente, colocar o espaco restante entre os elementos, e ajustar automaticamente a disposicao dos itens de acordo com o tamanho da tela ou janela.


Aula 2

O primeiro objetivo desta aula foi aplicar o flexbox no rodape.

Percebi que seguindo as medidas do professor nos widths e margem, o logo da alura ficava mais distante da margem esquerda do que o formulario ficava da margem direita. Isso aconteceu porque o space-around adicionava aproximadamente 12% (70% / 3 itens / 2 lados) de margem a esquerda desse item.

Para deixar mais simetrico, coloquei 30% de width e 5% de margem a esquerda do formulario, e diminui o width dos patrocinadores para 60%, de forma que ficassem os mesmos 5% de margem a esquerda do logo da alura.

Assim, os patrocinadores ficaram com 65% do container, e o formulario com 35%. E 15% de espaco entre os dois blocos.

Apesar dos ajustes pessoais, a simetria continua melhor no chrome.

Ao colocar display: flex; em um container, seus filhos ficam com a mesma altura (quando lado a lado), ou mesma largura (quando empilhados).

O segundo objetivo foi posicionar as listas de cursos em colunas, uma ao lado da outra.

Diferentemente do professor, que nao envolveu cada lista em uma tag, eu assim o fiz, pois ele setou a altura do Mapa de Cursos em pixels, com medida da maior lista, para que quando a lista nao coubesse mais, houvesse uma quebra de coluna.

Entao, envolvi cada lista em uma ul, e coloquei-as em colunas, pois fazendo como o professor explica, temos um "numero magico", e o titulo de uma lista seguinte pode ficar abaixo de uma lista anterior dependendo do tamanho do navegador utilizado pelo usuario.

Para me auxiliar nessa mudanca, utilizei como fonte os seguintes topicos:

https://cursos.alura.com.br/forum/topico-quebrar-a-coluna-por-tamanho-de-height-em-pixels-parece-nao-ser-uma-boa-ideia-77581

https://cursos.alura.com.br/forum/topico-criterio-da-quebra-de-linha-no-caso-coluna-utilizando-o-flex-wrap-46814

justify-content: space-between; pega todo espaco em branco, faz a divisao
[(espaco restante) / (numero de elementos - 1)]
 e coloca cada fracao entre dois elementos.

justify-content: space-around; pega todo espaco em branco, faz a divisao
[(espaco restante) / (numero de elementos * 2)]
e o distribui em volta dos elementos. Dessa forma, fica uma fracao do lado direito de cada elemento, e uma fracao do lado esquerdo de cada elemento.

justify-content: flex-start; é o padrao, todo conteudo a esquerda.

justify-content: flex-end; todo o conteudo a direita.

justify-content: center; todo conteudo ao centro.

Fonte: https://www.binarycarpenter.com/flexbox-align-content-space-between-space-around-and-space-evenly/

Flex-wrap: wrap joga os elementos que nao cabem em uma linha ou coluna, passem para a seguinte. Para que estes nao ultrapassem os limites do elemento pai.

Flex-flow agrega o conjunto
flex-direction:
flex-wrap:
respectivamente.

Aula 3

Teve como objetivo organizar o grid de cursos em 4 colunas.

A forma como o professor implementou o layout continha um passo a mais, no qual foi necessario utilizar:

.conteudoPrincipal-cursos-links {
    width: 23%;
    /* margem em todos itens, pois o justify-content nao funciona para linhas com menos que 4 itens */
    margin: 1%
}

/* correcao das margens direitas dos itens do canto direito */
.conteudoPrincipal-cursos-link:nth-child(4n+1) {
    margin-left: 0;
}

/*correcao das margens esquerdas dos itens do canto esquerdo */
.conteudoPrincipal-cursos-link:nth-child(4n) {
    margin-right: 0;
}

Isso nao foi necessario na pratica, pois o codigo inicial fornecido ja continha media queries que corrigiam esse problema no arquivo style.css.

Aula 4

A quarta aula foca no desenvolvimento mobile, utilizando as ferramentas de desenvolvedor do browser. E no ajuste do video na parte desktop.

Isso é feito principalmente atraves do empilhamento dos itens, ajuste de largura, mudanca na ordem dos itens.

O flex-grow recebe um valor que sera interpretado como uma fracao do espaco restante do seu pai, e fara com que o item que recebe essa propriedade ocupe essa fracao. Ver classes videoSobre-video e videoSobre-sobre no arquivo flexbox.css para ver na pratica.

As logos respondem corretamente no chrome, mas no firefox o logo "casa do codigo" fica metade pra fora do layout, ocasionando uma barra de scroll horizontal.

Alem disso, nao deu certo colocar justify-content: center; no .rodapePrincipal-contatoForm-fieldset como na aula. O elemento nao fica centralizado.
