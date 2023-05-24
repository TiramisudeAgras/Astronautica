# Código 4.2:

```python title="Determinación numérica del valor de optimización φ para sistemas multietapas"
import numpy as np
from scipy.optimize import root

def main():
  def delta_v(x,n,v_s,eps,dv): #Se define la funcion 5
    delta = 0
    for i in range(n):
        delta = delta + v_s[i]*np.log((v_s[i]-x)/(eps[i]*v_s[i]))
        i += 1
    return dv-delta
  
  n = 3 #Numero de etapas
  v_s = [4500,5000,4500] #Valores de velocidad efectiva de eyección para cada una de las etapas
  eps = [0.08,0.12,0.16] #Valores de razón de masa estructural para cada una de las etapas
  dv = 7000 #Delta v deseado
  varphi = root(delta_v,0.8,args=(n,v_s,eps,dv))
  print(varphi.x[0].round(2))

if __name__ == '__main__':
  main()
```
### Descripción a detalle:

1. `import numpy as np` y `from scipy.optimize import root`: Estas líneas importan los módulos necesarios. Numpy se utiliza para realizar operaciones matemáticas y scipy.optimize proporciona la función `root` que se utiliza para encontrar las raíces de ecuaciones.

2. `def main():` : Esta línea define la función principal.

3. `def delta_v(x,n,v_s,eps,dv):` : Esta función interna define la ecuación que se va a resolver. Esta ecuación se basa en el cálculo de la variación de la velocidad (`delta_v`) de un vehículo de múltiples etapas.

4. Las siguientes líneas dentro de la función `main` definen varias constantes:
    - `n` es el número de etapas del vehículo.
    - `v_s` es una lista de los valores de velocidad efectiva de eyección para cada una de las etapas.
    - `eps` es una lista de los valores de la razón de masa estructural para cada una de las etapas.
    - `dv` es el delta-v deseado.

5. `varphi = root(delta_v,0.8,args=(n,v_s,eps,dv))`: Esta línea utiliza la función `root` de scipy para encontrar la raíz de la ecuación definida en `delta_v`. El valor inicial para la búsqueda de la raíz es `0.8`.

6. `print(varphi.x[0].round(2))`: Esta línea imprime el resultado de la búsqueda de la raíz, que es el valor calculado para `varphi`. Se redondea a 2 decimales.

7. Las últimas dos líneas simplemente llaman a la función principal cuando se ejecuta el script.


### Playground:

Haga click en este enlace para poder interactuar con el [script](https://replit.com/@SantiagoAcua3/Determinacion-numerica-del-valor-de-optimizacion-ph#main.py)