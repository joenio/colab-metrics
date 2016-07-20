# colab-metrics

Este projeto contém dados de métricas e árvore AST do projeto Colab.

* https://github.com/colab/colab

## Ferramentas para extração de dados

Ferramentas de análise estática para código-fonte Python.

### Radon

http://radon.readthedocs.io

### Pylint + Pyreverse

http://www.pylint.org

O Pylint a partir da versão 0.15 vem junto com o Pyreverse para extraçao de
diagramas UML.

#### Rodar em Debian (testing)

    $ git clone https://github.com/colab/colab.git
    $ cd colab
    $ sudo apt-get install pylint
    $ pyreverse colab/ -pcolab

O Pyreverse irá criar 2 arquivos `classes_colab.dot` e `packages_colab.dot`,
para gerar visualização destes arquivos podemos usar o Graphviz.

    $ sudo apt-get install graphviz
    $ circo classes_colab.dot -Tpdf -O
    $ circo packages_colab.dot -Tpdf -O

Serão gerados 2 arquivos `classes_colab.dot.pdf` e `packages_colab.dot.pdf`.
No diretório `pylint` deste repositório temos os arquivos gerados pelos
comandos acima.

### PyChecker

http://pychecker.sourceforge.net

Verifica por erros comuns no código, não aceita analisar um projeto inteiro de
uma vez, apenas arquivos individuais.

    $ sudo apt-get install pychecker

### Prospector

http://github.com/landscapeio/prospector

    $ sudo apt-get install prospector

### Landscape

http://landscape.io

Não é bem uma ferramenta, mas sim uma plataforma web para monitoramento de
repositórios de projetos Python, roda o Prospector, talvez tenha outras
ferramentas "por baixo".

Cadastrei o Colab nele e notei que apenas faz checagem de estilo, erros,
bad smells, e dá uma série de alertas sobre o código-fonte. Mas não fornece
métricas ou nenhuma representação do projeto em árvore ou grafo, alguns
screenshots dos relatórios gerados para o projeto Colab foram adicionados
no diretório `landscape` deste repositório. Pode também ser acessado online
publicamente em https://landscape.io/github/joenio/colab/

### PMD

http://pmd.github.io/pmd-5.3.1/pmd-python

A ferramenta PMD funciona para Python mas apenas para detectar duplicação 
de código.

    $ ./bin/run.sh cpd --language python --minimum-tokens 100 --files ~/src/colab/colab/


### Pythoscope

http://pythoscope.org/

### Python AST

http://docs.python.org/3/library/ast.html

O Python vem com uma lib core para gerar e manipular AST, com isso foi feito um
script para gerar AST de cada arquivo de um dado projeto, no diretório `python-ast`
deste projeto criamos o script `parser` e extraimos AST de cada arquivo do projeto
colab em sua última versão, presente também no diretório `python-ast`.
