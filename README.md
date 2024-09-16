import numpy as np

def temperatura_promedio_ciudad(temperaturas, ciudad_index):
    """
    Calcula la temperatura promedio para una ciudad específica a lo largo del período dado.
    
    Parámetros:
    temperaturas (np.ndarray): Una matriz 3D con las temperaturas. Dimensiones deben ser (num_ciudades, num_dias, num_semanas).
    ciudad_index (int): El índice de la ciudad para la cual se calculará el promedio.

    Retorna:
    float: La temperatura promedio para la ciudad especificada.
    """
    if ciudad_index < 0 or ciudad_index >= temperaturas.shape[0]:
        raise ValueError("Índice de ciudad fuera de rango.")
    
    # Seleccionar los datos de la ciudad específica
    temperaturas_ciudad = temperaturas[ciudad_index, :, :]
    
    # Calcular la temperatura promedio
    promedio = np.mean(temperaturas_ciudad)
    
    return promedio

# Ejemplo de uso
if __name__ == "__main__":
    # Parámetros
    num_ciudades = 3
    num_dias = 7
    num_semanas = 4
    
    # Crear una matriz 3D con temperaturas aleatorias
    np.random.seed(0)  # Para reproducibilidad
    temperaturas = np.random.uniform(15, 30, (num_ciudades, num_dias, num_semanas))
    
    # Calcular y mostrar la temperatura promedio para cada ciudad
    for ciudad in range(num_ciudades):
        promedio = temperatura_promedio_ciudad(temperaturas, ciudad)
        print(f"Temperatura promedio para la Ciudad {ciudad + 1}: {promedio:.2f}°C")
git add nombre_del_archivo.py
git commit -m "Añadida función para calcular la temperatura promedio de una ciudad"
git push origin main
assert np.isclose(temperatura_promedio_ciudad(temperaturas, 0), np.mean(temperaturas[0, :, :]))

