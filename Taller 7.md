1. Cree un Jupyter notebook, el cual servir´a como documento de trabajo y entrega. Incluya todas las respuestas a las consultas solicitadas en el notebook.
2. Con´ectese al mismo servidor usado en las diapositivas, pero en este caso a la base de datos taller uni.
3. Liste todas las tablas en el esquema pu´blico.
4. Liste el nombre de todas las unidades acad´emicas.
5. Liste los nombres de todas las unidades acad´emicas a las que est´an asociados los profesores. Elimine duplicados con distinct antes del atributo de inter´es (nombre de la unidad).
6. Para cada tabla liste 5 registros usando limit al final de la consulta.
7. Realice una consulta que retorne un listado de los instructores con su nombre, ID y el doble de su salario.
8. Realice una consulta para obtener todos los cursos ofrecidos por la unidad ’IIND’.
9. Liste todos los nombres de los instructores con el edificio donde queda ubicada su respectiva unidad. Use un cross join.
10. Liste todos los instructores con sus clases. Use un cross join.
11. Liste todos los instructores con sus clases. Use un natural join.
12. Liste todos los IDs de los instructores con los c´odigos de los cursos que dictan. Use un natural join.
    Alternativamente se puede usar join using para hacer un join que use solo algunos atributos comunes, no todos. Por ejemplo, para listar todos los IDs de los instructores con los c´odigos de los cursos que dictan podemos ejecutar el siguiente comando
    select inst_ID , curso_cod
    from ( instructor natural join dicta ) join curso using ( curso_cod );

La clausula as se puede utilizar para renombrar los atributos en la relaci´on que se obtiene como resultado. Por ejemplo, en el siguiente comando cambiamos el nombre del primer atributo seleccionado
select nombre as nombre_inst , curso_cod from instructor , dicta
where instructor. inst_ID = dicta . inst_ID ;

La cl´ausula as tambi´en se puede utilizar para renombrar las relaciones consideradas. Por ejemplo, el comando anterior lo podr´ıamos escribir como

select nombre , curso_cod
from instructor as I, dicta as D where I. inst_ID = D. inst_ID ;

Esto puede ser u´til cuando se requiere comparar una relaci´on consigo misma. Por ejemplo, si se quiere determinar los cursos que tienen al menos tantos cr´editos como al menos un curso de IIND, ejecutar´ıamos el comando
select distinct A. nombre from curso as A, curso as B
where A. creditos > B. creditos and B. nombre_unid = ’ IIND ’;

Estos nombres para las relaciones se conocen como alias. 13. Realice una consulta en la que compare una relaci´on consigo misma (diferente a curso).
