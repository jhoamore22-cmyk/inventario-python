# inventario-python
Solución Problema 3 - Auditoría de Inventario - Fase 5 Fundamentos de Programación
# ===============================================================
# FUNDAMENTOS DE PROGRAMACIÓN - CÓDIGO 213022
# FASE 5 - EVALUACIÓN FINAL POA
# PROBLEMA 3 - AUDITORÍA DE INVENTARIO
# ===============================================================
# ESTUDIANTE: [JHOAN SEBASTIAN MORENO GALINDO]
# GRUPO: [NÚMERO DE GRUPO]
# FECHA: Julio, 2026
# ===============================================================


# ===============================================================
# 1. DEFINICIÓN DE LA FUNCIÓN PARA CALCULAR CANTIDAD A PEDIR
# ===============================================================

def calcular_cantidad_pedido(stock_actual, stock_minimo):
    """
    Función que determina la cantidad exacta a pedir para un artículo.
    
    Parámetros:
    - stock_actual: número de unidades disponibles en inventario
    - stock_minimo: número mínimo de unidades que debe haber en inventario
    
    Retorna:
    - cantidad_a_pedir: número de unidades que se deben solicitar
                        (0 si el stock actual es suficiente)
    """
    
    # Lógica de negocio: comparar stock actual con stock mínimo
    if stock_actual < stock_minimo:
        # Si el stock actual es insuficiente, calcular la diferencia
        cantidad_a_pedir = stock_minimo - stock_actual
    else:
        # Si el stock actual es suficiente, no se necesita pedir
        cantidad_a_pedir = 0
    
    # Retornar la cantidad calculada
    return cantidad_a_pedir


# ===============================================================
# 2. DATOS INICIALES - MATRIZ DE INVENTARIO
# ===============================================================

# Estructura de la matriz: [Código, Nombre, Stock Actual, Stock Mínimo]
# Se incluyen 6 artículos para cumplir con el requisito mínimo de 5

inventario = [
    ["TEC-001", "Laptop Lenovo", 8, 5],
    ["TEC-002", "Monitor Samsung", 3, 10],
    ["TEC-003", "Teclado Mecánico", 15, 8],
    ["TEC-004", "Mouse Inalámbrico", 2, 6],
    ["TEC-005", "Disco Duro 1TB", 0, 4],
    ["TEC-006", "Memoria USB 64GB", 12, 15]
]


# ===============================================================
# 3. PROCESAMIENTO DE LA MATRIZ Y GENERACIÓN DE INFORME
# ===============================================================

# Variable para contar el total de artículos que necesitan pedido
total_pedidos = 0

# Encabezado del informe
print("\n" + "="*50)
print("        INFORME DE REABASTECIMIENTO")
print("="*50)
print("\nLista de artículos que necesitan ser solicitados:\n")

# Recorrer cada artículo de la matriz
for articulo in inventario:
    # Desempaquetar los datos del artículo
    codigo = articulo[0]
    nombre = articulo[1]
    stock_actual = articulo[2]
    stock_minimo = articulo[3]
    
    # Llamar a la función para calcular la cantidad a pedir
    cantidad = calcular_cantidad_pedido(stock_actual, stock_minimo)
    
    # Si la cantidad a pedir es mayor que 0, mostrar en el informe
    if cantidad > 0:
        print(f"  {nombre} → Cantidad a pedir: {cantidad} unidades")
        total_pedidos = total_pedidos + 1

# Mostrar resumen final
print("\n" + "-"*50)
print(f"TOTAL DE ARTÍCULOS A REABASTECER: {total_pedidos}")
print("="*50 + "\n")

# Mensaje final
if total_pedidos > 0:
    print("✅ Se han generado las órdenes de pedido correspondientes.")
else:
    print("✅ El inventario se encuentra en niveles óptimos. No se requieren pedidos.")
