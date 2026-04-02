# Laboratorio 9 - Parte 1 - Angel Camargo 24003664

Se implementó paginación del lado del servidor en el endpoint GET /api/properties. En propertyController.ts se extraen los query params page y limit con valores por defecto de 1 y 10, se calcula el skip, y se reemplazó la lógica de .slice() en memoria por un Promise.all que consulta los datos paginados y el conteo total en paralelo, retornando un objeto meta con total, page, limit y pages. Aparte de este archivo, tuvimos que modificar un archivo aparte del que decian las instrucciones, el cual fue propertyRepository.ts, en donde se modificó findAll para aceptar skip y take y pasarlos directamente a Prisma, y se agregó el método count para obtener el total de registros aplicando los mismos filtros.

# Laboratorio 9 - Parte 2 - Angel Camargo 24003664

Se implementó el endpoint GET /api/properties/stats para retornar estadísticas generales del inventario de propiedades de una forma ordenada y legible. Extra a lo que pedian las instrucciones se agregó el método getStats en propertyRepository.ts usando groupBy y aggregate de Prisma para calcular el conteo total, cantidad y precio promedio agrupado por tipo, y el rango de precios global. Se creó el controlador getPropertyStats en propertyController.ts que conecta el endpoint con el repositorio y retorna la respuesta en formato JSON. Finalmente se registró la ruta en propertyRoutes.ts antes de /:id para evitar conflictos de rutas.

Videos de demostración: https://drive.google.com/drive/folders/1oBMJo8SClv1Ge4HuPH2cqD_G-cpPcRPF?usp=sharing
