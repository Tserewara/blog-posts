Relações entre classes
Sabemos que a orientação a objetos nos permite resolver problemas do mundo real através da criação de objetos. Modelamos cada parte de um sistema com um objeto separado. No entanto, o verdadeiro poder da orientação a objetos está no modo como relacionamos os objetos entre si para que juntos componham um sistema que resolve o nosso problema real.

Podemos comparar isso a um restaurante bem organizado, onde os funcionários interagem com clientes para atendê-los. Um garçom (objeto) anota o pedido de um cliente (objeto) e então encaminha para o cozinheiro (objeto) diretamente ou por meio de outro funcionário (objeto). Quando o pedido fica pronto, o garçom leva o prato até o cliente. Após terminar sua refeição, o cliente paga a conta (pode ser um objeto também) para o funcionário que trabalha no caixa (objeto). Alguém precisa decidir quem faz cada coisa em um restaurante. O dono ou um gerente delega responsabilidades e estabelece como os funcionários devem interagir entre si.

De forma similar, ao criar um sistema usando orientação a objetos, o designer (nesse caso, nós programadores) deverá decidir como os objetos se relacionam e interagem entre si. Veja os tipos de relação existentes na orientação a objetos.

Associação
Na associação, duas classes têm uma relação (uma usa a outra) mas não precisam um da outra para existirem. No arquivo classes.py temos:

# classes.py

class Cozinheiro:
    def __init__(self, nome):
        self.nome = nome
        self.utensilio_de_corte = None


class Faca:
    def __init__(self, material):
        self.material = material
    
    def cortar(self):
        print('Faca está cortando')

class Cutelo:
    def cortar(self):
        print('Cutelo está cortando)
No arquivo main.py temos

# main.py

from classes import Cozinheiro
from classes import Faca
from classes import Cutelo

cozinheiro = Cozinheiro('Zé')
faca = Faca('Tramontina')
cutelo = Cutelo()

cozinheiro.utensilio_de_corte = faca
cozinheiro.utensilio_de_corte.cortar()
Primeiramente, criamos uma classe Cozinheiro. Note que ela possui o atributo utensilio_de_corte, por meio do qual podemos passar uma ferramenta para o cozinheiro cortar.

Depois, criamos a classe Faca e Cutelo. As duas classes têm o método cortar. Então, criamos uma instância de Faca (faca) e de Cutelo (cutelo). Finalmente, atribuímos faca a cozinheiro.utensilio_de_corte, o que permite que o cozinheiro use o método cortar da ferramenta que lhe foi passada. Também, podemos alterar a ferramenta do cozinheiro para cutelo, por exemplo. Para isso basta alterarmos o atributo em cozinheiro.utensilio_de_corte para caneta:

# main.py

from classes import Cozinheiro
from classes import Faca
from classes import Cutelo

cozinheiro = Cozinheiro('Zé')
faca = Faca('Tramontina')
cutelo = Cutelo()

cozinheiro.utensilio_de_corte = cutelo
cozinheiro.utensilio_de_corte.cortar()
Note que a relação entre as classes Cozinheiro e Faca é fraca. Se deletarmos cozinheiro, o objeto faca continua existindo normalmente, e podemos usá-lo sem problemas.

# main.py

from classes import Cozinheiro
from classes import Faca
from classes import Cutelo

cozinheiro = Cozinheiro('Zé')
faca = Faca('Tramontina')
cutelo = Cutelo()

del cozinheiro
faca.cortar()
Agregação
A agregação é um tipo de associação. Nesse caso, temos uma relação parte/todo, em que uma classe é parte de outra, de modo que a classe que agrega precisa da outra classe para funcionar.

# classes.py

class ListaDeProdutos:
    def __init__(self):
        self.produtos = []
    
    def inserir_produto(self, produto):
        self.produtos.append(produto)
    
    def listar_produtos(self):
        for produto in self.produtos:
            print(produto.nome, produto.valor)
    
    def total(self):
        total = 0
        for produto in self.produtos:
            total += self.produto.valor
        return total

class Produto:
    def __init__(self, nome, valor)
        self.nome = nome
        self.valor = valor
No exemplo dado, temos uma classe ListaDeProdutos que agrega instâncias da classe Produto. A classe ListaDeProdutos pode existir sem produtos, no entanto, ela não funciona sem eles. Ao mesmo tempo, a classe Produto não depende em nada de ListaDeProdutos e pode ser usada por outras partes de nossa aplicação.

Note que podemos instanciar ListaDeProdutos mesmo sem produtos.

# main.py

from classes import CarrinhoDeCompras, Produto

lista_produtos = ListaDeProdutos()

print(lista_produtos)
No entanto, só conseguimos usar as funcionalides de lista_produtos após adicionar alguns produtos:

# main.py

from classes import ListaDeProdutos, Produto

lista_produtos = ListaDeProdutos()

camiseta = Produto('Camiseta', 50)
calca = Produto('Calça', 150)
bone = Produto('Boné', 20)

lista_produtos.inserir_produto(camiseta)
lista_produtos.inserir_produto(camiseta)
lista_produtos.inserir_produto(calca)
lista_produtos.inserir_produto(bone)

lista_produtos.listar_produtos()
lista_produtos.soma_total()
Composição
A composição também é um tipo de associação. Nessa relação, uma classe é dona de outra. Assim, quando a classe dona é apagada, as classes que ela possui serão apagadas também.

# classes.py

class Aluno:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade
        self.cursos = []
    
    def matricular_em_curso(self, codigo_curso, nome_curso):
        self.cursos.append(Curso(codigo_curso, nome_curso))

    def listar_cursos(self):
        for curso em cursos:
            print(curso.nome_curso)


class Curso:
    def __init__(self, nome_curso, codigo_curso):
        self.nome_curso = nome_curso
        self.codigo_curso = codigo_curso
As instâncias da classe Curso são criadas apenas quando invocamos o método matricular_em_curso de Aluno. Portanto, os cursos não existem fora de aluno. Dessa forma, Aluno é composto por cursos. Sendo assim, quando deletamos uma instância de Aluno, os cursos que a compõem também são deletados. Vemos que esse tipo de relação é mais forte, pois Curso depende de Aluno para existir.

from classes import Aluno, Curso


joao = Aluno('João', 10)
joao.matricular_em_curso('Matemática', 'M1')
joao.matricular_em_curso('Português', 'PT1')
joao.matricular_em_curso('Inglês', 'EN1')

joao.listar_cursos()
Teremos a seguinte saída:

Matemática
Português
Inglês
Agora, iremos verificar o que acontece com os cursos ao deletarmos o objeto joao. Para isso, vamos adicionar o método __del__ em nossa classe Aluno para visualizar.

# classes.py

class Aluno:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade
        self.cursos = []
    
    def matricular_em_curso(self, codigo_curso, nome_curso):
        self.cursos.append(Curso(codigo_curso, nome_curso))

    def listar_cursos(self):
        for curso em cursos:
            print(curso.nome_curso)

    def __del__(self):
        print(f'O curso {self.nome_curso} foi apagado')


class Curso:
    def __init__(self, nome_curso, codigo_curso):
        self.nome_curso = nome_curso
        self.codigo_curso = codigo_curso
Ao apagarmos o objeto aluno, o garbage collector do Python entra em ação. Internamente, ele executará __del__ apagando o aluno. Veja o que acontecerá com os cursos quando isso acontecer

from classes import Aluno, Curso


joao = Aluno('João', 10)
joao.matricular_em_curso('Matemática', 'M1')
joao.matricular_em_curso('Português', 'PT1')
joao.matricular_em_curso('Inglês', 'EN1')

del joao # apagamos o objeto joao
Teremos o seguinte resultado

O curso Matemática foi apagado
O curso Português foi apagado
O curso Inglês foi apagado
Assim, vimos que quando joao deixa de existir, os cursos também são apagados.

Herança