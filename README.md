# README
Tiempo de prueba
Primero, iniciemos el servidor en localhost:3000:
rails server
# Alternativamente, también puedes ejecutar
# rails s
Segundo, creemos dos usuarios usando el comando curl:
curl -H "Content-type: application/json" -d '{"user":{"name":"Luke Skywalker","email":"luke@starwars.com","password": "12345678","password_confirmation":"12345678"}}' http://localhost:3000/users


curl -H "Content-type: application/json" -d '{"user":{"name":"Han Solo","email":"han@starwars.com","password": "12345678","password_confirmation":"12345678"}}' http://localhost:3000/users

Tercero, listemos los usuarios:

http://localhost:3000/users

Cuarto, autentiquémosnos:

curl -H “Content-type: application/json” -d ‘{“auth”: {“email”: “luke@starwars.com”, “password”: “12345678”}}’ http://localhost:3000/user_token

Observemos que la respuesta nos va a devolver el JWT:
{"jwt":"este_es_el_jwt"}

Quinto, obtengamos la información de nuestro propio usuario (Luke Skywalker):

curl -H "Authorization: Bearer el_jwt_recibido_previamente" http://localhost:3000/users/current

Sexto, obtengamos la información de otro usuario, en este caso Han Solo:

curl -H "Authorization: Bearer el_jwt_recibido_previamente" http://localhost:3000/users/2