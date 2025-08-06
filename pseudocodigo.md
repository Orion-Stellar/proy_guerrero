INICIO

VARIABLES:
    fuerza (int) = 10
    resistencia (int) = 10
    energia (int) = 20
    experiencia (int) = 0
    nivel (int) = 1
    opcion (int)
    random (aleatorio)

DO
    MOSTRAR "==========================="
    MOSTRAR "   GUERRERO DEL BARRIO"
    MOSTRAR "1. Ver estado"
    MOSTRAR "2. Entrenar fuerza"
    MOSTRAR "3. Entrenar resistencia"
    MOSTRAR "4. Pelear"
    MOSTRAR "5. Dormir"
    MOSTRAR "6. Salir"
    MOSTRAR "==========================="
    LEER opcion

    SWITCH opcion
        CASO 1:
            LLAMAR VerEstado()
        CASO 2:
            LLAMAR EntrenarFuerza()
        CASO 3:
            LLAMAR EntrenarResistencia()
        CASO 4:
            LLAMAR Pelear()
        CASO 5:
            LLAMAR Dormir()
        CASO 6:
            MOSTRAR "El guerrero se fue a comer tacos. Fin del juego."
        DEFAULT:
            MOSTRAR "Opcion invalida, prueba de nuevo"
    FIN SWITCH

    LLAMAR SubirNivel()

MIENTRAS opcion != 6

FIN

FUNCION VerEstado()
    MOSTRAR "------ ESTADO DEL GUERRERO ------"
    MOSTRAR "Nivel: " + nivel
    MOSTRAR "Fuerza: " + fuerza
    MOSTRAR "Resistencia: " + resistencia
    MOSTRAR "Energia: " + energia
    MOSTRAR "Experiencia: " + experiencia
    MOSTRAR "---------------------------------"
FIN FUNCION

FUNCION EntrenarFuerza()
    maxHoras = energia / 5
    SI maxHoras == 0 ENTONCES
        MOSTRAR "Estas demasiado cansado para entrenar"
        RETORNAR
    FIN SI

    MOSTRAR "¿Cuantas horas vas a entrenar fuerza? Maximo " + maxHoras
    LEER horas
    SI horas > maxHoras ENTONCES
        horas = maxHoras
    FIN SI

    PARA i DESDE 1 HASTA horas
        fuerza = fuerza + 6
        energia = energia - 5
    FIN PARA

    experiencia = experiencia + 5
    MOSTRAR "Entrenamiento completado, ahora tus brazos parecen de acero"
FIN FUNCION

FUNCION EntrenarResistencia()
    maxHoras = energia / 2
    SI maxHoras == 0 ENTONCES
        MOSTRAR "No tienes energia ni para caminar"
        RETORNAR
    FIN SI

    MOSTRAR "¿Cuantas horas vas a entrenar resistencia? Maximo " + maxHoras
    LEER horas
    SI horas > maxHoras ENTONCES
        horas = maxHoras
    FIN SI

    PARA i DESDE 1 HASTA horas
        resistencia = resistencia + 4
        energia = energia - 2
    FIN PARA

    experiencia = experiencia + 4
    MOSTRAR "Corriste tanto que ahora puedes aguantar hasta las pedradas del barrio"
FIN FUNCION

FUNCION Pelear()
    SI energia < 5 ENTONCES
        MOSTRAR "No puedes pelear, estas agotado"
        RETORNAR
    FIN SI

    energia = energia - 5
    fuerzaEnemigo = ALEATORIO(5, 15)
    resistenciaEnemigo = ALEATORIO(5, 15)

    poderGuerrero = fuerza + resistencia
    poderEnemigo = fuerzaEnemigo + resistenciaEnemigo

    MOSTRAR "Te enfrentas a un rival con poder " + poderEnemigo

    SI poderGuerrero > poderEnemigo ENTONCES
        experiencia = experiencia + 10
        MOSTRAR "Ganaste la pelea, todos te aplauden"
    SINO
        experiencia = experiencia + 3
        MOSTRAR "Perdiste la pelea, te dejaron tirado en la banqueta"
    FIN SI
FIN FUNCION

FUNCION Dormir()
    MOSTRAR "Tu guerrero se duerme en la banqueta como un campeon"
    energia = energia + 10
    SI energia > 20 ENTONCES
        energia = 20
    FIN SI
FIN FUNCION

FUNCION SubirNivel()
    SI experiencia >= nivel * 20 ENTONCES
        nivel = nivel + 1
        fuerza = fuerza + 2
        resistencia = resistencia + 2
        experiencia = 0
        MOSTRAR "Subiste de nivel, ahora eres leyenda del barrio"
    FIN SI
FIN FUNCION
