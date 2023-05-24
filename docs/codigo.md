# Códigos & Scripts

## Código 4.1:

```python title="Determinación numérica de m_0 para empuje en pozos gravitacionales"
import numpy as np 
from scipy.optimize import root

def main():
  mu = 0.104 #Coeficiente de masa total
  e = 0.08 #Coeficiente de masa estructural
  delta_v = 7000.0 #Delta v requerido (m/s)
  m_c = 500.0 #Masa de carga (kg)
  I_sp = 311.0 #Impulso específico (s)
  g0 = 9.81 #Aceleración gravitacional en el planeta Tierra (m/s^2)
  m_p = 321.21 #Flujo másico (kg/s)

  def f(x):
    f = g0*I_sp*np.log(x/(e*(x-m_c)+m_c))-(g0*x*(1-mu)/(5*m_p))-delta_v
    return f

  m_0 = root(fun=f,x0=70000)
  print(m_0.x[0].round(2))

if __name__ == "__main__":
    main()
```
### Descripción a detalle:

1. `import numpy as np` y `from scipy.optimize import root`: Estas líneas importan los módulos necesarios. Numpy se utiliza para realizar operaciones matemáticas y scipy.optimize proporciona la función `root` que se utiliza para encontrar las raíces de ecuaciones.

2. `def main():` : Esta línea define la función principal.

3. Las siguientes líneas dentro de la función `main` definen varias constantes:
    - `mu` es el coeficiente de masa total.
    - `e` es el coeficiente de masa estructural.
    - `delta_v` es el cambio de velocidad requerido, comúnmente conocido como "delta-v".
    - `m_c` es la masa de la carga de la nave espacial.
    - `I_sp` es el impulso específico, que es una medida de la eficiencia de un motor de cohete.
    - `g0` es la aceleración gravitacional en la Tierra.
    - `m_p` es el flujo másico, que podría referirse a la cantidad de combustible que el cohete puede quemar por segundo.

4. `def f(x):` : Esta función interna define la ecuación que se va a resolver. En este caso, es una versión de la ecuación del cohete que ha sido reorganizada para poder resolverla para `m_0` (la masa inicial de la nave espacial) dada la constante `delta_v`.

5. `m_0 = root(fun=f,x0=70000)`: Esta línea utiliza la función `root` de scipy para encontrar la raíz de la ecuación definida en `f(x)`. El valor inicial para la búsqueda de la raíz es `70000`.

6. `print(m_0.x[0].round(2))`: Esta línea imprime el resultado de la búsqueda de la raíz, que es el valor calculado para `m_0`. Se redondea a 2 decimales.

7. Las últimas dos líneas simplemente llaman a la función principal cuando se ejecuta el script.

En resumen, el objetivo general de este script es calcular la masa inicial necesaria para una nave espacial dada una serie de parámetros y requerimientos de misión.

### Playground:

Haga click en este enlace para poder interactuar con el [script](https://replit.com/@SantiagoAcua3/Determinacion-numerica-de-m0-para-empuje-en-pozos-gravitacio#main.py)


