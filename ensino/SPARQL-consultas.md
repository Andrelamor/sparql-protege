# SPARQL consultas 
0. listar os cursos por professores organizadores e ordenados pelos créditos
````
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
prefix owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix : <http://www.semanticweb.org/andre/ontologies/2023/5/untitled-ontology-3/>
SELECT ?x ?y ?z
WHERE {
  ?x rdf:type :Curso ;
       :ehOrganizadoPor ?y ;
       :creditos ?z.
       
} ORDER BY ?z
````

2. listar todos os professores

SELECT ?x
WHERE {
  ?x rdf:type dbo:Professor .
}

2. listar todos os professores titulares

SELECT ?x
WHERE {
  ?x rdf:type dbo:ProfessorTitular .
}

3. listar todos os professores que lecionam cursos regulares

SELECT ?x ?Curso
WHERE {
  ?x rdf:type dbo:Professor ;
  dbo:Professor dbo:titularLeciona ?Curso .
}

4. listar todos os professores que lecionam cursos de laboratório

SELECT ?x ?c
WHERE {
  ?x dbo:assistenteLeciona dbo:CursoLaboratorio ;
  ?c dbo:titularLeciona dbo:CursoLaboratorio .
}

5. qual professor leciona qual curso

SELECT ?x ?c
WHERE {
  ?x dbo:assistenteLeciona dbo:Curso ;
  ?c dbo:titularLeciona dbo:Curso .
}

6. qual professor organizou qual curso

SELECT ?x 
WHERE {
  ?x rdf:type dbo:organizadoPor .
}


7. quais as lições de casa de determinado curso

SELECT ?x 
WHERE {
  ?x rdf:type dbo:organizadoPor.
}
