# punto-5-trabajo-diciembre-
import statistics

# Definir una lista para almacenar la información de las ciudades y los sismos
ciudades = []

# Función para registrar una ciudad
# Función para registrar una ciudad
def registrar_ciudad():
    nombre_ciudad = input("Ingrese el nombre de la ciudad: ")
    cantidad_sismos = int(input("Ingrese la cantidad de sismos a registrar por ciudad: "))
    ciudades.append({"nombre": nombre_ciudad, "cantidad_sismos": cantidad_sismos, "sismos": []})

# Función para registrar un sismo
def registrar_sismo():
    if not ciudades:
        print("Primero debe registrar al menos una ciudad.")
        return

    print("Seleccione la ciudad para registrar el sismo:")
    for i, ciudad in enumerate(ciudades, 1):
        print(f"{i}. {ciudad['nombre']}")

    opcion_ciudad = int(input("Ingrese el número de la ciudad: "))
    ciudad_actual = ciudades[opcion_ciudad - 1]

    for i in range(ciudad_actual["cantidad_sismos"]):
        magnitud_sismo = float(input(f"Ingrese la magnitud del sismo {i + 1} para {ciudad_actual['nombre']}: "))
        ciudad_actual["sismos"].append(magnitud_sismo)

# Función para buscar sismos por ciudad
def buscar_sismos_por_ciudad():
    if not ciudades:
        print("Primero debe registrar al menos una ciudad.")
        return

    print("Seleccione la ciudad para buscar sismos:")
    for i, ciudad in enumerate(ciudades, 1):
        print(f"{i}. {ciudad['nombre']}")

    opcion_ciudad = int(input("Ingrese el número de la ciudad: "))
    ciudad_actual = ciudades[opcion_ciudad - 1]

    print(f"\nSismos registrados para {ciudad_actual['nombre']}:\n{ciudad_actual['sismos']}")

# Función para generar un informe de riesgo
def informe_de_riesgo():
    if not ciudades:
        print("Primero debe registrar al menos una ciudad.")
        return

    for ciudad in ciudades:
        promedio_sismos = statistics.mean(ciudad["sismos"])
        print(f"\nInforme de riesgo para {ciudad['nombre']}:")

        if promedio_sismos < 2.5:
            print("Nivel de riesgo: Amarillo (Sin riesgo)")
        elif 2.6 <= promedio_sismos <= 4.5:
            print("Nivel de riesgo: Naranja (Riesgo medio)")
        else:
            print("Nivel de riesgo: Rojo (Riesgo alto)")

# Menú principal
while True:
    print("\nMenú:")
    print("1. Registrar Ciudad")
    print("2. Registrar Sismo")
    print("3. Buscar Sismos por Ciudad")
    print("4. Informe de Riesgo")
    print("5. Salir")

    opcion = int(input("Ingrese la opción deseada: "))

    if opcion == 1:
        registrar_ciudad()
    elif opcion == 2:
        registrar_sismo()
    elif opcion == 3:
        buscar_sismos_por_ciudad()
    elif opcion == 4:
        informe_de_riesgo()
    elif opcion == 5:
        print("¡Hasta luego!")
        break
    else:
        print("Opción no válida. Por favor, ingrese una opción válida.")
