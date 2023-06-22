# SPARQL consultas 

1. listar todos os professores

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
