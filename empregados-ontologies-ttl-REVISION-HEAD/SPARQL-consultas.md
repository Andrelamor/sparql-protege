# SPARQL consultas 

1. listar todos os empregados

SELECT ?Empregado
WHERE {
  ?Empregado rdf:Type dbo:Empregado .
}

2. listar os empregados que têm nome:

SELECT ?Empregado ?nome
WHERE {
  ?Empregado rdf:Type dbo:Empregado ;
             dbo:temNome ?nome .
}

3. listar os nomes dos empregados e as empresas em que trabalham (e ordenar a lista resultante por empresa)

SELECT ?Empregado ?nome ?Empresa
WHERE {
  ?Empregado rdf:Type dbo:Empregado ;
             dbo:temNome ?nome ;
             dbo:trabalha ?Empresa .
} ORDER BY ?Empresa

4. listar os nomes dos empregados que trabalham na USIMINAS

SELECT ?Empregado ?nome 
WHERE {
  ?Empregado rdf:Type dbo:Empregado ;
             dbo:temNome ?nome ;
             dbo:trabalha "\"Usiminas\""^^xsd:string .
} ORDER BY ?Empresa

5. listar todos os estudantes da UFMG e ordenar a lista por nome

SELECT ?variavel ?nome 
WHERE {
  ?variavel rdf:Type dbo:Estudante ;
             dbo:temNome ?nome ;
             dbo:estuda "\"Universidade Federal de Minas Gerais\""^^xsd:string .
} ORDER BY ?nome
