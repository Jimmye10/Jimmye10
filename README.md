# Base de datos de productos
productos = {
    "manzanas": 0.5,
    "plátanos": 0.25,
    "pan": 1.0,
    "leche": 1.5,
    "huevos": 2.0,
}

# Función para mostrar los productos disponibles
def mostrar_productos():
    print("Productos disponibles:")
    for producto, precio in productos.items():
        print(f"{producto}: ${precio}")

# Función para agregar productos al carrito
def agregar_al_carrito(carrito, producto, cantidad):
    if producto in productos:
        carrito.append((producto, cantidad))
        print(f"{cantidad} {producto} añadido al carrito.")
    else:
        print(f"{producto} no está en la lista de productos disponibles.")

# Función para calcular el total de la compra
def calcular_total(carrito):
    total = 0
    for producto, cantidad in carrito:
        if producto in productos:
            precio_unitario = productos[producto]
            total += precio_unitario * cantidad
    return total

# Inicializar el carrito de compras
carrito_de_compras = []

# Interacción con el usuario
while True:
    mostrar_productos()
    opcion = input("Elija un producto para agregar al carrito (o 'salir' para terminar): ").lower()

    if opcion == 'salir':
        break

    if opcion in productos:
        cantidad = int(input(f"¿Cuántos {opcion} desea agregar al carrito? "))
        agregar_al_carrito(carrito_de_compras, opcion, cantidad)
    else:
        print("Opción no válida.")

# Calcular y mostrar el total de la compra
total_compra = calcular_total(carrito_de_compras)
print(f"Total de la compra: ${total_compra}")
