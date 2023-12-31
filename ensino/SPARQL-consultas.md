# SPARQL consultas 

## prep

- versão do Protegè: 5.5.0 (a mesma utilizada pelo Thiago/FALE)
- plugin: Snap SPARQL Query 6.0.0
- reasoner Hermit 1.4.3: deve estar ligado, para inferência de subclasses atribuir indivíduos
- prexix: atentar para a barra '/' do arquivo turtle ([1ª linha dos prefixos](https://github.com/Andrelamor/sparql-protege/blob/01835fba833529d1c1597be2cbfaa96826b4cb44/ensino/ensino.ttl#L1))

- ontologia descrita em [triplas](https://github.com/Andrelamor/sparql-protege/blob/main/ensino/ensino.ttl)
- visualização da ontologia em [OntoGraf](https://github.com/Andrelamor/sparql-protege/blob/main/ensino/ensino-graph.png) 

## 1. listar todos os cursos

````
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
prefix owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix : <http://www.semanticweb.org/andre/ontologies/2023/5/untitled-ontology-3/>
SELECT ?x
WHERE {
  ?x rdf:type :Curso .    
} 
````

![](ensino/1.png)
![image](https://github.com/Andrelamor/sparql-protege/assets/52294411/0ac200ed-b82e-4e13-aed5-05c166e689d7)

## 2. listar os cursos por professores organizadores e ordenados pelos créditos
````
SELECT ?x ?y ?z
WHERE {
  ?x rdf:type :Curso ;
       :ehOrganizadoPor ?y ;
       :creditos ?z.
       
} ORDER BY ?z
````
![](ensino/2.png)
![image](https://github.com/Andrelamor/sparql-protege/assets/52294411/b829e99a-c59d-48a3-bf25-5fb34ccf69f4)

## 3. listar todos os professores e ordenar pelo título

````
SELECT ?x ?z
WHERE {
  ?x rdf:type :Professor ;
      :titulo ?z.
       
} ORDER BY ?z
````

![](ensino/3.png)
![image](https://github.com/Andrelamor/sparql-protege/assets/52294411/8e67b113-98b3-4b2b-8e8d-2beea5099937)

## 4. listar todos os cursos organizados por professores assistentes, ordenados pelos nomes dos professores

````
SELECT ?x ?z
WHERE {
  ?x rdf:type :ProfessorAssistente ;
      :organiza ?z.
       
} ORDER BY ?x
````
![](ensino/4.png)
![image](https://github.com/Andrelamor/sparql-protege/assets/52294411/1e297d78-0ca6-4b5d-a0a4-29f39b2aa13a)

## 5. quantos alunos por curso

````
SELECT ?x COUNT(?z)
WHERE {
  ?x rdf:type :Curso ;
      :ehCursadoPor ?z.
       
} GROUP BY ?z
````

## 6.quais as lições de casa de determinado curso, ordenados por crédito dos cursos
