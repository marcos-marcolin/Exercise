# Exercise

Tarefa de programação: Programa completo - Similaridades entre textos - Caso COH-PIAH
Atividade não enviada. Você deve obter 8/10 pontos para passar.
Prazo	
Seja aprovado nessa tarefa até Apr 19, 12:59 AM PDT
InstruçõesMeus envios
Prólogo
Neste último exercício da Parte 1, iremos praticar não só o que vimos até agora no curso mas também outra habilidade importante de um programador: utilizar e interagir com código escrito por terceiros. Aqui, você não irá implementar o seu programa do zero. Você irá partir de um programa já iniciado e irá completá-lo. Na verdade, esse é o caso mais comum na indústria de software, onde muitos desenvolvedores trabalham colaborativamente em um mesmo programa.

Introdução 
Manuel Estandarte é monitor na disciplina Introdução à Produção Textual I na Universidade de Pasárgada (UPA). Durante o período letivo, Manuel descobriu que uma epidemia de COH-PIAH estava se espalhando pela UPA. Essa doença rara e altamente contagiosa faz com que indivíduos contaminados produzam, involuntariamente, textos muito semelhantes aos de outras pessoas. Após a entrega da primeira redação, Manuel desconfiou que alguns alunos estavam sofrendo de COH-PIAH. Manuel, preocupado com a saúde da turma, resolveu buscar um método para identificar os casos de COH-PIAH. Para isso, ele necessita da sua ajuda para desenvolver um programa que o auxilie a identificar os alunos contaminados.

Detecção de autoria
Diferentes pessoas possuem diferentes estilos de escrita; por exemplo, algumas pessoas preferem sentenças mais curtas, outras preferem sentenças mais longas. Utilizando diversas estatísticas do texto, é possível identificar aspectos que funcionam como uma “assinatura” do seu autor e, portanto, é possível detectar se dois textos dados foram escritos por uma mesma pessoa. Ou seja, essa “assinatura” pode ser utilizada para detecção de plágio, evidência forense ou, neste caso, para diagnosticar a grave doença COH-PIAH.

Traços linguísticos
Neste exercício utilizaremos as seguintes estatísticas para detectar a doença:

Tamanho médio de palavra: Média simples do número de caracteres por palavra.
Relação Type-Token: Número de palavras diferentes utilizadas em um texto divididas pelo total de palavras.
Razão Hapax Legomana: Número de palavras utilizadas uma única vez dividido pelo número total de palavras.
Tamanho médio de sentença: Média simples do número de caracteres por sentença.
Complexidade de sentença: Média simples do número de frases por sentença.
Tamanho médio de frase: Média simples do número de caracteres por frase.
Funcionamento do programa
A partir da assinatura conhecida de um portador de COH-PIAH, seu programa deverá receber diversos textos e calcular os valores dos diferentes traços linguísticos desses textos para compará-los com a assinatura dada. Os traços linguísticos que seu programa deve utilizar são calculados da seguinte forma:

Tamanho médio de palavra é a soma dos tamanhos das palavras dividida pelo número total de palavras.
Relação Type-Token é o número de palavras diferentes dividido pelo número total de palavras. Por exemplo, na frase "O gato caçava o rato", temos 5 palavras no total (o, gato, caçava, o, rato) mas somente 4 diferentes (o, gato, caçava, rato). Nessa frase, a relação Type-Token vale  \frac{4}{5} = 0.8  
5
4
​	
 =0.8
Razão Hapax Legomana é o número de palavras que aparecem uma única vez dividido pelo total de palavras. Por exemplo, na frase "O gato caçava o rato", temos 5 palavras no total (o, gato, caçava, o, rato) mas somente 3 que aparecem só uma vez (gato, caçava, rato). Nessa frase, a relação Hapax Legomana vale  \frac{3}{5} = 0.6  
5
3
​	
 =0.6
Tamanho médio de sentença é a soma dos números de caracteres em todas as sentenças dividida pelo número de sentenças (os caracteres que separam uma sentença da outra não devem ser contabilizados como parte da sentença).
Complexidade de sentença é o número total de frases divido pelo número de sentenças.
Tamanho médio de frase é a soma do número de caracteres em cada frase dividida pelo número de frases no texto  (os caracteres que separam uma frase da outra não devem ser contabilizados como parte da frase).
Após calcular esses valores para cada texto, você deve compará-los com a assinatura fornecida para os infectados por COH-PIAH. O grau de similaridade entre dois textos,  a a e  b b, é dado pela fórmula:

 S_{ab} = \frac{\sum_{i=1}^6 || f_{i,a} - f_{i,b} ||}{6} S 
ab
​	
 = 
6
∑ 
i=1
6
​	
 ∣∣f 
i,a
​	
 −f 
i,b
​	
 ∣∣
​	
 

Onde:

 S_{ab} S 
ab
​	
  é o grau de similaridade entre os textos  a a e  b b;
 f_{i,a} f 
i,a
​	
  é o valor de cada traço linguístico  i i no texto  a a; e
 f_{i,b} f 
i,b
​	
  é o valor de cada traço linguístico  i i no texto  b b.
No nosso caso, o texto  b b não é conhecido, mas temos a assinatura correspondente: a assinatura de um aluno infectado com COH-PIAH. Ou seja, sabemos o valor de  f_{i,b} f 
i,b
​	
  que é dado como valor de entrada do programa. 

Caso você não esteja acostumado com a notação matemática, podemos destrinchar essa fórmula da seguinte maneira: 

Para cada traço linguístico  i i (tamanho médio da palavra, relação type-token etc.) se quer a diferença entre o valor obtido em cada texto dado ( a a) e o valor típico do texto de uma pessoa infectada ( b b):  f_{i, a} - f_{i, b} f 
i,a
​	
 −f 
i,b
​	
 

Dessa diferença se toma o módulo ( || \ldots || ∣∣…∣∣), lembre-se da função abs do python.

Somamos os resultados dos 6 traços linguísticos (\sum_{i=1}^6∑ 
i=1
6
​	
 )

E por final dividimos por 6 (  \frac{x}{6} 
6
x
​	
 )

Perceba que quanto mais similares  a a e  b b forem, menor  S_{ab} S 
ab
​	
  será. Para cada texto, você deve calcular o grau de similaridade com a assinatura do portador de COH-PIAH e, no final, exibir qual texto mais provavelmente foi escrito por algum aluno infectado (ou seja, o texto com assinatura mais similar à assinatura dada).

Exemplo:

234567891011121314151617181920211
$ > python3 coh_piah.py

Bem-vindo ao detector automático de COH-PIAH.
Informe a assinatura típica de um aluno infectado:

Entre o tamanho médio de palavra: 4.51
Entre a relação Type-Token: 0.693
Entre a Razão Hapax Legomana: 0.55
Entre o tamanho médio de sentença: 70.82
Entre a complexidade média da sentença: 1.82

Funções de suporte
Para facilitar seu trabalho, fornecemos para você um esqueleto do programa completo como base. Use-o! As funções definidas nele devem ser utilizadas no seu programa; algumas já estão implementadas, outras devem ser implementadas por você (conforme indicado pelo comentário "IMPLEMENTAR"). Sinta-se livre para criar funções adicionais, caso necessário.

444546474849505152535455565758596061626364656667686970717273747576777879808182
import re

def le_assinatura():
    '''A funcao le os valores dos tracos linguisticos do modelo e devolve uma assinatura a ser comparada com os textos fornecidos'''
    print("Bem-vindo ao detector automático de COH-PIAH.")
    print("Informe a assinatura típica de um aluno infectado:")

    wal = float(input("Entre o tamanho médio de palavra:"))
    ttr = float(input("Entre a relação Type-Token:"))
    hlr = float(input("Entre a Razão Hapax Legomana:"))
…    '''IMPLEMENTAR. Essa funcao recebe uma lista de textos e uma assinatura ass_cp e deve devolver o numero (1 a n) do texto com maior probabilidade de ter sido infectado por COH-PIAH.'''
    pass
Dica: não se preocupe com os detalhes de implementação das funções pré-prontas do esqueleto, como "separa_sentenca()", "separa_frase()" etc. nem com as definições exatas de frase e sentença. Essas funções já cuidam disso para você, e podem ser pensadas como "caixas pretas": você pode utilizá-las sabendo o que recebem e o que devolvem, mas não é necessário saber sobre os seus detalhes internos. Além de isso ser muito comum ao programar em equipe, usando essas funções você vai fazer o cálculo da maneira esperada pelo corretor automático.

Cuidado: A função le_textos() considera que um "texto" é uma linha de texto, ou seja, não é possível inserir parágrafos separados. Se você digitar algum "enter", a função vai entender que você está começando um novo texto. Preste especial atenção a isso se usar "copiar/colar" para inserir os textos! Note também que, no cálculo de similaridade, é preciso encontrar o valor absoluto de cada uma das diferenças.

Exemplo de Assinatura
Um passo importante para seu programa é calcular a assinatura dos textos corretamente. Para testar se sua função calcula_assinatura()  está correta, deixamos aqui um exemplo de execução:

123
>texto = "Então resolveu ir brincar com a Máquina pra ser também imperador dos filhos da mandioca. Mas as três cunhas deram muitas risadas e falaram que isso de deuses era gorda mentira antiga, que não tinha deus não e que com a máquina ninguém não brinca porque ela mata. A máquina não era deus não, nem possuía os distintivos femininos de que o herói gostava tanto. Era feita pelos homens. Se mexia com eletricidade com fogo com água com vento com fumo, os homens aproveitando as forças da natureza
Concluindo
Basicamente, sua tarefa é implementar corretamente as seguintes funções:  

compara_assinatura(as_a, as_b)
calcula_assinatura(texto)
avalia_textos(textos, ass_cp)
Usando o esqueleto que oferecemos acima e implementando essas 3 funções, seu detector de plágio estará completo e você poderá submetê-lo ao corretor automático. Caso o corretor automático aponte erros, tente ler com bastante cuidado e atenção a mensagem fornecida por ele, pois ela normalmente ajuda a identificar o erro.   

Boa sorte! Não desista! 

Sabemos que é um desafio, mas você vai aprender muito com ele. 

Pense no prazer que você vai sentir quando sua solução final for aceita!!!   

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

DICAS IMPORTANTES!!! (parte 1) - ILUMINANDO O PASSO A PASSO
YRYgor Xavier Carvalho Rios
10 months ago
Se você está se perguntando: Por onde eu começo? O que é isso? O que é aquilo?

Fique tranquilo. Trouxe aqui os questionamentos que me fiz e dicas tiradas do fórum. Dividi em DICAS IMPORTANTES!!! (parte 1) e DICAS IMPORTANTES!!! (parte 2).

Tem-se, aqui:

 INICIALMENTE: 1 - Enunciado ; 2 - Porque usar “import re”? ; 3 - O que é uma assinatura? ; 4 - Alguma informação fornecida está errada? ; 5 - Devo criar mais funções? ; 6 - Quais funções preciso implementar? ; 7 - Quais são as funções de suporte? Preciso mexer nelas? ; 8 - O que é esse “pass” e o que fazer com ele? ; 9 - O que é uma sentença? ; 10 - O que é uma frase? ; 11 - Preciso declarar variáveis globais?

 IMPLEMENTAÇÃO DO PROGRAMA: 1 - Contar Letras ou Caracteres? ;  2 - Por onde começar? ; 2.1 - Como passar texto como parâmetro para dentro da função? ; 2.2 - Tamanho médio de Palavras.

Em DICAS IMPORTANTES!!! (parte 2) tem-se: 2.3 Relação Type-Token ; 2.4 - Tamanho médio de sentença e de frase ; 3 - Função Compara Assinatura ; 4 - Função Avalia Textos ; 5 - Resultado Final 

 INICIALMENTE:

Leia o enunciado várias vezes e com calma (é sério): O enunciado te dá várias informações do que se quer. Só precisa ler com calma. Se na função está escrito que ela deve RECEBER uma lista de textos e uma assinatura, não é para chamar a lista e a assinatura no escopo da função, mas sim fazer com que a função receba essas coisas como parâmetro. Se está escrito que têm de RETORNAR algo, faça. Leia tudo com cuidado.
Porque usar “import re”? “re” vem de “regular expressions”. Para resumir, sem ele você não conseguiria usar as funções de separar palavras em letras por exemplo. Mais informações na biblioteca do Python. Nela, o Python diz que não se pode misturar textos do tipo “Unicode” e “8-bits” sem o módulo “re”. Se quiser é só ver aqui o que é um texto Unicode e um 8-bit.
O que é uma assinatura? A assinatura é uma LISTA de 6 elementos, sendo eles os TRAÇOS LINGUÍSTICOS calculados por você. Então, se uma função RECEBE como parâmetro uma assinatura, você tem que lembrar que ela está recebendo uma LISTA.
Alguma informação fornecida está errada? Não. Parta dessa premissa que isso vai te ajudar a entender o exercício.
Devo criar mais funções? Aconselho criar apenas a função "main()", pra chamar as outras e iniciar o programa automaticamente. Acredite, não é preciso criar mais nenhuma além de uma main(). Talvez criar funções para os cálculos pode te confundir.
Quais funções preciso implementar? calcula_assinatura(texto), compara_assinatura(as_a, as_b) e avalia_textos(textos, ass_cp). e elas devem RECEBER exatamente o que está escrito para receber.
Quais são as funções de suporte? Preciso mexer nelas?  São elas: le_assinatura, le_textos, separa_sentencas, separa_frases, separa_palavras, n_palavras_unicas e n_palavras_diferentes. NÃO MEXER nelas. Você chamará elas para as contas, nunca as modificará.
O que é esse “pass” e o que fazer com ele? Esse comando não faz nada. Você deverá APAGAR O PASS das funções a serem implementadas e RETORNAR o que se pede para cada função. Eles colocaram porque não podia deixar a função sem nenhuma definição, o que causaria erro Como pode ser visto aqui
O que é uma sentença? Em língua portuguesa, sentença e frase são iguais. MAS NÃO É ISSO para o programa COH-PIAH. Aqui, sentença também não é um parágrafo. Mas o que é então? Basta verificar quais são os caracteres usados para separar as sentenças entre si. A função separa_sentencas(texto) mostra que as sentenças serão separadas por     .!?  Então, encare uma sentença (no programa) como uma frase (em língua portuguesa) que termina com ponto final, ponto de exclamação ou ponto de interrogação.
O que é uma frase? Em língua portuguesa, a frase é um enunciado que faz sentido. MAS no programa a frase é qualquer trecho separado por vírgula, dois pontos ou ponto e vírgula (basta verificar a função separa_frase(texto).
Preciso declarar variáveis globais? Não precisa. Variáveis globais são aquelas que ficam fora de qualquer função. Fazer isso pode até te confundir.
 IMPLEMENTAÇÃO DO PROGRAMA:

1. Contar Letras ou Caracteres? às vezes o traço linguístico pede uma conta com número de LETRAS e às vezes com CARACTERES. Exemplo:

Tamanho médio de palavras: Envolve a quantidade de LETRAS nas palavras
Tamanho médio da sentença: Dentro de uma sentença terá letras, espaços entre palavras, vírgulas, dois pontos e ponto e vírgula, todas contabilizando como CARACTERES.
Tamanho médio da frase: Dentro da frase terá as palavras e os espaços entre elas, todas contabilizando como CARACTERES.
2. Por onde começar? Aconselho começar pela função “calcula_assinatura(texto)”. Dentro dela você vai fazer comandos para calcular todos os 6 traços linguísticos. Faça um de cada vez.

Lembre-se: Se você está dentro da função calcula_assinatura, ela tem que RETORNAR, ao final, uma LISTA com os 6 traços linguísticos, afinal de contas, a ASSINATURA É UMA LISTA (tópico 3 de INICIALMENTE)
 
 2.1 Tá, mas de onde vem esse texto? Como passar um texto como parâmetro para dentro de uma função? Funciona assim: 

123456789
def função_A():
  var_1 = lista_AA
  var_2 = função_B(X,Y) 'função que gera uma lista_BB'
  conta = calcular(var_1,var_2)
  print conta
  
def calcular(lista1,lista2):
  #Comandos quaisquer
  "Calcula o que quero"
FINJA QUE A FUNÇÃO calcula_assinatura JÁ ESTÁ RECEBENDO UM TEXTO COMO PARÂMETRO. Você declara variáveis, NO ESCOPO DE OUTRA FUNÇÃO, que puxam o que você precisa como parâmetros. Depois, declara outra variável que chama a função que você quer, com parâmetros de cálculo já dentro. No caso, a função "calcula_assinatura" é chamada por "avalia_textos". 

E fica a dica: Em "calcula_assinatura" você não vai chamar as funções "le_assinatura()" ou "le_textos()"
 2.2 Tamanho médio de Palavras

É o melhor traço linguístico para se começar. Conseguindo ele, você vai entender a lógica para todos os outros.

 Lógica do cálculo: A função "calcula_assinatura(texto)" recebe APENAS UM texto. Para calcular o tamanho médio de palavra, você vai precisar ter uma LISTA de todas as palavras desse texto, para conseguir pedir o tamanho de cada palavra e ir somando. Mas de onde vem essa lista de palavras? Vai vir da lista de frases do seu texto e assim por diante.
Então: De um texto que você já tem (finge que ele já está como parâmetro), você chamará a função separa_sentencas, atribuindo a ela a uma nova variável. Com isso, você terá uma nova variável que será uma LISTA de sentenças.
Você deve usar as funções separa_sentenca, separa_frase e separa_palavra em laços e ir juntando em uma lista de palavras, de maneira iterativa, como mostrado aqui. Para juntar as frases em sua lista de frases e palavras em sua lista de palavras, você pode usar o comando "extend" ao invés de criar um while e depois o append. O "extend" vai aumentando o conteúdo de uma lista ADICIONANDO OUTRA LISTA. Já o append vai adicionando ELEMENTOS na lista. Tem horas que o append é melhor, tem horas que o extend é melhor. Bom, o exemplo é:
12345678
lista_palavras = []
lista_frases = []
lista_sent = separa_sentencas(texto)
for sent in sentencas:
  novas_frases = separa_frases(texto)
  lista_frases.extend(novas_frases)
  
  'Fazer isso para as palarvras também. Pode ou não ser aninhado'
Com isso você terá uma LISTA DE PALAVRAS ao final desse processo. Depois é só calcular o tamanho médio das palavras como manda o enunciado. Nesse caso é saber usar da maneira certa o comando <len> para proceder com os cálculos ;-)
Aconselho salvar o valor desse traço linguístico com o nome "wal_texto", visto que na função "le_assinatura()" que eles deram, o nome dessa variável era "wal". Reproduza esse pensamento para os outros traços linguísticos, para ficar fácil de entender. 
Ir para DICAS IMPORTANTES (parte 2)
4 respostas
MAMARCO AURELIO ROSA DE AQUINO
8 months ago
boa noite Igor;

Interpretando melhor suas explicações neste cheguei programa:

def calcula_assinatura(texto): 

    '''IMPLEMENTAR. Essa funcao recebe um texto e deve devolver a assinatura do texto.''' 

    lista_palavras = [] 

    lista_frases = [] 

    sentencas = separa_sentencas(texto) 

    for sent in sentencas: 

        novas_frases = separa_frases(sent) 

        lista_frases.extend(novas_frases) 

        for fr in novas_frases: 

            novas_palavras=separa_palavras(fr) 

            lista_palavras.extend(novas_palavras) 

        soma1=len(lista_palavras) 

        soma2=len(lista_frases) 

        wal_texto= soma1 / soma2 

        return wal_texto 

Por enquanto estou tentando achar a média das palavras para seguir com o resto, mas o resultado está dando 7.0, então algo está errado.

MAMARCO AURELIO ROSA DE AQUINO
8 months ago
Consegui encontrar o tamanho médio das palavras, vou partir para os próximos traços linguisticos, obrigado pelas dicas até agora.

MAMARCO AURELIO ROSA DE AQUINO
8 months ago
Boa noite Igor;

Apesar desta grande explicação, ainda continuo com dificuldades.

O que eu entendi até agora:

1- É MELHOR COMEÇAR PELA FUNÇÃO CALULA_ASSINATURA OK

2-QUE NELA DEVO CALCULAR A ASSINATURA (COM 6 ELEMENTOS) DE UM TEXTO OK

E É AI QUE COMEÇO A ME CONFUNDIR, EU TENTEI CALCULAR O TAMANHO MEDIA DAS PALAVRAS DESSA FORMA:

def calcular(lista1,lista2): 

    lista_palavras = [] 

    lista_frases = [] 

    lista_sent = separa_sentencas(texto) 

    for sent in sentencas: 

        novas_frases = separa_frases(texto) 

        lista_frases.extend(novas_frases) 

        novas_palavras=separa_palavras(frase) 

        lista_palavras.extend(novas_palavras) 

        soma1=len(lista_palavras) 

        soma2=len(lista_frases) 

        wal_texto= soma1 / soma2 

        return wal_texto

ME INFORME POR FAVOR SE ESTOU NO CAMINHO CORRETO, OUTRA DIFICULDADE É QUE AINDA NÃO ENTENDI DE QUE FORMA VOU PUXAR O TEXTO COMO PARÂMETRO, PARA DENTRO DA FUNÇÃO, MESMO LENDO VARIAS VEZES SUA EXPLICAÇÃO,ESPERO QUE POSSA ME DAR UM HORIZONTE.

OBRIGADO!

avatar de perfil do usuárioGabriel Crispino
Equipe9 months ago
Olá Ygor,

Parabéns pelo post!

YRYgor Xavier Carvalho Rios
10 months ago
Segue o link para a Parte 2

---------------------------------------------------------------------------------------------

DICAS IMPORTANTES!!! (parte 2) - ILUMINANDO O PASSO A PASSO
Ygor Xavier Carvalho RiosAssignment: Programa completo - Similaridades entre textos - Caso COH-PIAH · 10 months ago · Editado
Continuando com as DICAS IMPORTANTES (parte 2). A primeira parte do tópico está aqui.

Aqui temos:

2.3 Relação Type-Token ; 2.4 - Tamanho médio de sentença e de frase ; 3 - Função Compara Assinatura ; 4 - Função Avalia Textos ; 5 - Resultado Final  

2.3 Relação Type-Token

A mesma lógica de percorrer uma  lista é pensada aqui. No caso você já tem uma lista de palavras que  você definiu anteriormente. Então é só fazer os cálculos. O traço  linguístico Hapax-Legomana segue o mesmo princípio.

2.4 Tamanho médio de sentença e de frase

Aqui você também vai seguir a mesma lógica de percorrer listas, mas atenção:

Para  as sentenças, você deve somar CARACTERES das sentenças. Ou seja, se  você tem uma LISTA DE SENTENÇAS (que olha que legal, você atribuiu como  primeiro comando para a função "calcula_assinatura") é só fazer as  contas utilizando o comando len, em processo iterativo de soma,  percorrendo a lista.
Com essas lógicas, você conseguirá calcular todos os traços linguísticos.
Ao final, não se esqueça de RETORNAR o que se pede para a função calcula_assinatura(texto)
TESTAR A FUNÇÃO: Não se esqueça que a sua função calcula_assinatura recebe um texto. Então a melhor maneira de testar se ela está funcionando é chamar essa função no Python Shell, colocando como parâmetro o texto que eles forneceram como teste. Se você der ENTER e o resultado for uma lista, você está no caminho certo. Só vai precisar verificar se as contas que fez estão certas.
3. Função compara_assinatura

Você NÃO DEVE chamar uma assinatura de um aluno com coh-piah ou chamar a função calcula_assinatura no escopo dessa função, pois essa função (como diz o enunciado) RECEBE duas assinaturas (listas). Então parta da premissa que já existem duas assinaturas que foram obtidas anteriormente, e essa função só está fazendo o cálculo de comparação entre elas. 
Você deverá pensar, mais pra frente, numa forma de chamar a função compara_assinatura dentro de outra função, de modo que os parâmetros da função compara_assinatura já serão carregados quando você chamar ela. 
Essa função simplesmente vai tirar as diferenças absolutas de elementos pareados de duas listas e fazer o cálculo devido. Portanto, mais uma vez você deverá percorrer as duas listas (assinaturas) de maneira iterativa, fazendo os cálculos necessários para tal.
Dica importante: Essa função precisa que os seus parâmetros sejam listas. Se qualquer um deles não for uma lista, ele dará algum erro do tipo "float object is not iterable" como descrito e respondido nesse tópico aqui
TESTAR A FUNÇÃO: Pra saber se ela está funcionando, basta chamar ela no Python Shell, colocando como parâmetro 2 listas. A primeira é a assinatura base com os 6 traços linguísticos fornecidos para um aluno com coh-piah. A segunda é a do texto que você calculou na função calcula_assinatura(texto).
4. Função avalia_textos

Perceba o que se pede na função avalia_textos: "Essa função recebe uma lista de textos e uma assinatura ass_cp e deve devolver o numero (1 a n) do texto com maior probabilidade de ter sido infectado por COH-PIAH"

Mais uma vez, essa função RECEBE determinados parâmetros. Mais uma vez, NÃO É para fazer "parâmetro_de_entrada_dela = função_que_preciso", no escopo dessa função. Você fará isso no escopo de outra função (como mostrado no tópico 2.1 - Como passar texto como parâmetro para dentro da função?). Suponha que ela já está recebendo os parâmetros necessários e você vai proceder a partir dai. Essa função será chamada em algum momento, em outro lugar (pense onde). Nesse outro lugar, você terá que achar uma forma de atribuir a uma variável uma lista de textos e à outra variável uma lista da assinatura de um aluno com COH-PIAH. Sendo assim, para implementar essa função você mais uma vez precisa entender que ela só funciona se receber esses parâmetros. Mas eles já vão vir quando você chamar essa função em outro lugar. 
Perceba que os parâmetros dessa função são LISTAS.
O que você tem que pensar é que essa função executa o seguinte: PARA cada texto (que será um elemento de uma lista de textos), você precisará CALCULAR a assinatura desse texto e depois COMPARAR com a assinatura base de um aluno com COH-PIAH (que é a ass_cp, como explicado aqui)
A execução dessa função NÃO PEDE PARA IMPRIMIR o número (índice) do texto, mas PEDE PARA RETORNAR/DEVOLVER o índice. Isso sugere que você precisará percorrer uma lista, cujos elementos armazenados são os valores da comparação entre as assinaturas dos textos e a assinatura do texto base. Nessa seção do Python Library, logo na primeira tabela, tem alguns comandos já conhecidos de listas e também tem o comando que te permite achar o índice de determinado elemento em uma lista qualquer.
5. Resultado Final

Percebam as etapas de execução: Informar assinatura dos alunos com COH-PIAH, informar os textos e por fim, já se chega numa avaliação final, com um PRINT.

Você precisará pensar em como unir essas informações em ordem, para no final IMPRIMIR o resultado, de modo que essa impressão conterá o número (índice) do texto do aluno que está contaminado. Ou seja, dentro do print você vai resgatar essa informação de alguma forma.
Bom, espero ter ajudado, trazendo as dúvidas que tive e discussões que me ajudaram aqui no fórum. Espero que eu consiga contribuir com seu aprendizado.

26 Classificações positivas
Responder
Acompanhar esta discussão

Mais antigas
Populares
Mais recente
Publicação de Gustavo Marroni de assis pereira
GP

GUSTAVO MARRONI DE ASSIS PEREIRA
Gustavo Marroni de assis pereira · a month ago
Bom Dia Pessoal, sou iniciante também em Python e estou quebrando a cabeça aqui para conseguir resolver esse problema..kkkk

Sei que no enunciado e o próprio Ygor passou aqui que não devemos mexer em nenhuma função já nos fornecidas, porem estou com um caso que não estou conseguindo resolver.

Meu programa esta colocando uma lista de palavras na função n_palavras_unicas e esta dando o seguinte retorno:

  File "C:/Users/gustavo/PycharmProjects/guppe/testes_USP.py", line 49, in n_palavras_unicas

    p = palavra.lower()

AttributeError: 'list' object has no attribute 'lower'

alguém teve esse erro também? Tentei procurar no fórum mas não achei. 

Agradeço se alguém puder me dar uma dica de como resolver isso. Obrigado.

0 Classificações positivas
Ocultar 1 Responder
Publicação de Gabriel Crispino
Gabriel Crispino
Gabriel CrispinoTeaching Staff · a month ago
Olá Gustavo,

Pelo que vi você já conseguiu resolver esse problema e obter nota máxima no exercício, certo? 

Você tem alguma outra dúvida?

0 Classificações positivas
MS

MARCOS SANTOS


Responder
Publicação de João Pedro Terra Zanuto
JZ

JOÃO PEDRO TERRA ZANUTO
João Pedro Terra Zanuto · 5 months ago
Cara, só tenho 2 coisas para te dizer: "PARA - BÉNS !!!"

1 Voto a favor
Responder
Publicação de Luísa Leal Rabello de Moraes
LM

LUÍSA LEAL RABELLO DE MORAES
Luísa Leal Rabello de Moraes · 6 months ago
nossa suas dicas me ajudaram muito, muito obrigada, demorei mais de 2 semanas fazendo, mas consegui kk

0 Classificações positivas
Responder
Publicação de Jailson Anjos
JA

JAILSON ANJOS
Jailson Anjos · 7 months ago
Ygor, finalmente consegui concluir o projeto COH-PIAH. Tive muita dificuldade para compreender o papel de cada função que deveria implementar. Graças a este post (e a respectiva parte 1) consegui entender o que era esperado e concluir o curso. Muito obrigado, cara!

1 Voto a favor
Responder
Publicação de Ygor Xavier Carvalho Rios
YR

YGOR XAVIER CARVALHO RIOS
Ygor Xavier Carvalho Rios · 10 months ago
Segue o link para a Parte 1

0 Classificações positivas
Ocultar 8 respostas
Publicação de Eliabe Rocha Da Cruz
Eliabe Rocha Da Cruz
Eliabe Rocha Da Cruz · 9 months ago
Cara, eu to com uma mega problema. Na função avalia_textos, o corretor retorna "AssertionError: Please define the function with name avalia_textos". Já fechei a função colocando no final avalia_textos(textos, ass_cp), mas nem assim  corretor aceita.Você sabe oq que pode ser?

0 Classificações positivas
Publicação de Ygor Xavier Carvalho Rios
YR

YGOR XAVIER CARVALHO RIOS
Ygor Xavier Carvalho Rios · 9 months ago · Editado
Bom, pelo que entendi, parece que a função avalia_textos não está definida ou não foi implementada. Mas acho que os professores e staffs do fórum podem responder melhor.

No meu programa, ela foi a última função a ser implementada. Primeiro de tudo: Você conseguiu implementar todas as outras funções, sem erros? Porque ela só vai funcionar se todas as outras estiverem funcionando.

A função "calcula_assinatura(texto)" tem que funcionar sozinha, e no final ela vai retornar uma lista, que no meu caso eu chamei de "ass_b", ou seja essa lista eu associei a uma variável chamada ass_b, que é a assinatura do texto que eu quero calcular. Para você entender, o meu ass_b é:
 ass_b = [wal_b, ttr_b, hlr_b, sal_b, sac_b, pal_b]

A função "compara_assinatura(as_a,as_b)" também tem que funcionar sozinha. Se você chamar ela no IDLE do python, escrevendo tipo:
compara_assinatura ([1,2,3,4,5,6], [7,8,9,10,11,12])

Ela vai ter que retornar um número, que é o cálculo daquela soma, que eles chamam de grau de similaridade. No meu programa, eu chamei esse grau de similaridade de "Sab". Pra testar a função, você pode ao invés de escrever "return Sab", escrever "print(Sab)" pra você ver o resultado.

Pois bem:

No meu programa, dentro do escopo da função "avalia_textos(textos, ass_cp):", eu comecei declarando uma lista vazia, chamada de "lista_sab", que é uma lista que vai conter vários graus de similaridade, pra eu poder dizer qual é o maior dentre eles.

123456
for cadatexto in textos:
        as_texto = calcula_assinatura(cadatexto)
        comparar = compara_assinatura(ass_cp,as_texto)        
        lista_sab.append(comparar)

# Continuar programação
Ou seja, vai adicionando na lista vazia os valores de grau de similaridade. Quando acabar de fazer isso, a minha lista vai ter vários Sab, que é a comparação de cada texto respectivo com a assinatura de coh_piah.

Depois, você pede pra dizer qual é o valor máximo dessa lista, e depois pede pra dizer qual o índice desse Sab (na lista_sab) que é o maior. No final, retornar esse índice como resposta.

Lembre-se que a função main é quem vai chamar le_assinatura, le_textos e avalia_textos, para que seu programa funcione.

123456
def main():
  #chamar as funções acima
  
def #todas as outras funções

main()
Não sei se consegui te ajudar em algo. Por que uma outra coisa que pensei é que parece que você tá chamando a função avalia_textos em algum lugar errado ou ela não está definida.

Já aconteceu comigo também de ter algum bug no arquivo e eu simplesmente criei um novo arquivo, copiei e colei do antigo pro novo e mandei rodar e foi. 

4 Classificações positivas
Publicação de Eliabe Rocha Da Cruz
Eliabe Rocha Da Cruz
Eliabe Rocha Da Cruz · 9 months ago
Cara, muito obrigado pela resposta!

Finalmente consegui terminar kkk

Curiosamente usando def main(): não funcionou, mesmo mudando a posição.Também não chamei as funções, como descrito em várias respostas. Pelo que entendi a única função que eu podia fechar no meu código era a função de comparação, quando fechei as demais deram erro na função avalia texto, mesmo rodando sem problemas no spyder e no IDLE python.

0 Classificações positivas
Publicação de Ygor Xavier Carvalho Rios
YR

YGOR XAVIER CARVALHO RIOS
Ygor Xavier Carvalho Rios · 9 months ago
Pois é, inicialmente eu também tive problema com a implementação do main(). Mas quando fui ver, eu tava fazendo algo errado nas outras funções, de modo que a chamada de uma função por outra não estava seguindo um caminho lógico. Ai, quando consegui acertar tudo, o main() foi. Mas essa é uma das formas de fazer né.

Que bom que conseguiu!

0 Classificações positivas
Publicação de Paulo Sergio Tadeu Gaya
Paulo Sergio Tadeu Gaya
Paulo Sergio Tadeu Gaya · 9 months ago
Ygor Xavier Carvalho Rios

Cheguei até aqui no curso com certa dificuldade. Sei que falta meio metro pra fincar a bandeira de final de curso. Quando cheguei no COH-PIAH levei um tombo feio. Não sei como é possível um iniciante ter que encarar um programa complexo desse. Confesso que suas dicas me parecem muito boas, até elogiadas pelo professor. Hoje, 10 de junho de 2020, estou completamente sem previsão alguma de quando vou conseguir fazer esse programa. Muito obrigado pela sua prestação de ajuda.

0 Classificações positivas
Publicação de maria celia cortez
MC

MARIA CELIA CORTEZ
maria celia cortez · 8 months ago
eu tb to nessa..

0 Classificações positivas
Publicação de Leonardo Issa Nicolau
LN

LEONARDO ISSA NICOLAU
Leonardo Issa Nicolau · 8 months ago
Boa tarde a todos,

Também sou iniciante em programação e iniciante também em Python. Apesar disso só tenho a elogiar o curso porque me colocou para estudar e tive que me esforçar muito a cada aula, a cada exercício. Bem, fiz essa breve introdução antes de expor a minha dúvida para que os colegas e o professor tenham noção de quão iniciante sou.

Estou na etapa do exercício final e tenho conseguido êxito  a cada correção, mas esbarrei num problema. Não sei se estou "entendendo errado" o que foi pedido, mas ao tentar avaliar um texto na função "avalia_textos" sendo que se neste texto há a presença da " (aspas) no corpo dele, surgem três cenários:

1 - se inserir "(aspas) no inicio e no fim do texto, a "(aspas) no corpo do texto sofrem influência e isso provoca um erro do tipo : SyntaxError: invalid syntax

2 - se não inserir nada no inicio e no fim do texto e tiver "(aspas) no corpo do texto, também surge o mesmo erro: SyntaxError: invalid syntax

3 - Só funciona quando eu coloco o texto com ' (apóstrofo) no inicio e no fim do texto que vai como argumento da função avalia_textos. 

Peço desculpas se a dúvida for muito básica, como disse, sou iniciante do iniciante (inclusive em programação).

Desde já agradeço,

Atenciosamente,

Leonardo

0 Classificações positivas
Publicação de Gabriel Crispino
Gabriel Crispino
Gabriel CrispinoTeaching Staff · 8 months ago
Leonardo,

Se você estiver falando do momento de introduzir um texto quando o programa pede, você não precisa por aspas. Se você estiver tentando colocar os textos "dentro" do seu programa manualmente, pode ser que algo a mais precise ser feito caso o texto possua aspas nele.

No mais, recomendo que você utilize o texto de exemplo do enunciado, inserindo-o quando o programa pede, como é lá mostrado, que você não deve ter problemas. Se você ainda estiver com dúvidas, peço que você crie um tópico a parte para não ficar difícil de seguir por aqui. 

0 Classificações positivas
