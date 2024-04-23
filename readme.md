# Práctica 4
# Manipulación y transformación de datos

En esta práctica, trabajaremos con un conjunto de datos ficticio relacionado con el desempeño de empleados en una empresa. Imaginemos que tenemos un archivo CSV llamado "empleados.csv" con las siguientes columnas:

- `ID`: Identificador único del empleado.
- `Nombre`: Nombre completo del empleado.
- `Departamento`: Departamento al que pertenece el empleado (por ejemplo, Ventas, Marketing, Recursos Humanos, etc.).
- `Salario`: Salario mensual del empleado en dólares.
- `Horas_Trabajadas`: Número de horas trabajadas por el empleado en el último mes.

Nuestra tarea será realizar las siguientes operaciones de manipulación y transformación de datos:

1. **Carga de datos**: Leer el archivo CSV y cargarlo en un DataFrame de pandas.
2. **Exploración inicial**:
    - Verificar la cantidad de registros y columnas en el DataFrame.
    - Mostrar las primeras filas del DataFrame para entender la estructura de los datos.
    - Comprobar si hay valores nulos o faltantes en alguna columna.
3. **Transformación de datos**:
    - Crear una nueva columna llamada "Salario_Mensual" que contenga el salario mensual de cada empleado (dividiendo el salario anual entre 12).
    - Calcular el promedio de salario por departamento.
    - Filtrar los empleados que ganan más de $10 000 mensual.
4. **Agregación de datos**:
    - Calcular el salario total pagado por la empresa en el último mes.
    - Encontrar el o los empleado(s) con el salario más alto.
    - Calcular el total de empleados en cada departamento.
5. **Visualización de resultados**:
    - Crear un gráfico de barras que muestre el número de empleados en cada departamento.

A continuación, te proporciono un ejemplo de cómo podríamos implementar estas operaciones en código utilizando pandas:

```python
import pandas as pd

# Cargar datos desde el archivo CSV
df = pd.read_csv("empleados.csv")

# Exploración inicial
print("Cantidad de registros:", len(df))
print("Columnas:", df.columns)
print("\nPrimeras filas:")
print(df.head())
print("\nValores nulos:")
print(df.isnull().sum())

# Transformación de datos
df["Salario_Anual"] = df["Salario"] / 12
promedio_horas_por_departamento = df.groupby("Departamento")["Horas_Trabajadas"].mean()
empleados_mas_de_160_horas = df[df["Horas_Trabajadas"] > 160]

# Agregación de datos
salario_total = df["Salario"].sum()
empleado_salario_maximo = df.loc[df["Salario"].idxmax()]
total_empleados_por_departamento = df["Departamento"].value_counts()

# Visualización de resultados (requiere matplotlib)
# df["Departamento"].value_counts().plot(kind="bar")
# plt.xlabel("Departamento")
# plt.ylabel("Número de empleados")
# plt.title("Distribución de empleados por departamento")
# plt.show()
```

Recuerda que debes adaptar este código a tus necesidades específicas. ¡Espero que esta práctica te ayude a familiarizarte con las capacidades de pandas en la manipulación y transformación de datos! 🚀

[Mas información sobre la data](https://www.kaggle.com/datasets/sahirmaharajj/employee-salaries-analysis)