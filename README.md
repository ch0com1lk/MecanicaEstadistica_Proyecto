# Mecanica Estadistica (PROYECTO)

Simulación del espectro de radiación de cuerpo negro como gas de fotones (Bose–Einstein), comparación de “estrellas tipo” y ajuste de temperatura a partir de un espectro “observado” sintético.

## Objetivo
Implementar una simulación del espectro de radiación de cuerpo negro basada en la ley de Planck para estudiar temperaturas superficiales estelares y, como extensión, conectar con flujo/luminosidad para estimar distancias (vía F = L / ($4π d²$))

## Fundamento físico (lo que se implementa)
- Ley de Planck en función de la longitud de onda $B(λ,T)$, implementada en planck_lambda(lamb, t) (unidades:$ W m⁻³ sr⁻¹$).
​- Ley de Wien (wien_lambda_max(t) = $b_wien / t$).
​- Ley de Stefan–Boltzmann para el flujo total (stefan_boltzmann_flux(t) = $\sigma * t**4$).
​- Luminosidad de cuerpo negro (luminosidad_cuerpo_negro(t, r) = $4 * π * r²$ * stefan_boltzmann_flux($t$)).
​- Flujo observado a una distancia $d$ (flujo_observado(L, d) = L / ($4 * π * d²$)).

## Cómo correr el notebook
1. Crea/activa un entorno con Python 3.
2. Instala dependencias:
   --> numpy, matplotlib, scipy (para curve_fit).
​3. Abre Pordefinri.ipynb en Jupyter/Colab y ejecuta las celdas en orden.

## Uso rápido (funciones principales)

1) Generar espectro de cuerpo negro
espectro_cuerpo_negro(t, lambda_min_nm=100, lambda_max_nm=3000, n_puntos=1000) devuelve 
(λ[nm],$B_λ$)
​
2) Comparar “estrellas tipo”
comparar_estrellas([4500, 5778, 10000], etiquetas=[...]) grafica espectros y muestra el corrimiento del máximo (Wien) y el aumento de intensidad total (Stefan–Boltzmann).
​

3) Ajuste de temperatura desde un espectro sintético

El notebook incluye una demo que:
- Genera datos sintéticos con ruido: generar_espectro_sintetico(t_real, ...).
​
- Ajusta T y un factor de escala a en el modelo I(λ)≈ a $B_λ(λ,T) con curve_fit: ajustar_temperatura(lambda_nm, datos).
​
- Grafica datos vs. ajuste y reporta t_fit.
​

### Ejemplo (ya incluido):

demo_ajuste_temperatura(t_real=7200.0)

Notas sobre el parámetro de escala a
En el ajuste I(λ)≈ a $B_λ(λ,T) el factor a representa una “área efectiva”/normalización (depende de geometría, distancia, respuesta instrumental o unidades arbitrarias del espectro).

## Referencias 
- Rybicki & Lightman, Radiative Processes in Astrophysics.
- Carroll & Ostlie, An Introduction to Modern Astrophysics.
- Planck (1901), On the law of distribution of energy in the normal spectrum.
- Landau & Lifshitz, Statistical Physics.
- Huang, Statistical Mechanics.
