# Sistema de Clasificación de Perfiles de Inversión con Lógica Difusa

Este proyecto implementa un sistema de lógica difusa para clasificar perfiles de inversión utilizando jFuzzyLogic, una biblioteca de Java para sistemas de inferencia difusa. El sistema evalúa a los potenciales inversionistas en una escala de 0 (muy conservador) a 10 (muy arriesgado) basándose en cuatro variables principales.

## Descripción del Sistema

El sistema clasifica a los inversionistas utilizando lógica difusa a partir de:

### Variables de Entrada (en orden de parámetros para la ejecución):

1. **Edad** (en años)

   - Joven: 18-45 años
   - Medio: 35-75 años
   - Mayor: 65-100 años

2. **Horizonte de Inversión** (en años)

   - Corto: 0-5 años
   - Medio: 3-10 años
   - Largo: 8-30 años

3. **Ingresos Mensuales** (en dólares)

   - Bajos: 0-4,000 dólares
   - Medios: 3,000-10,000 dólares
   - Altos: 8,000-100,000 dólares

4. **Tolerancia al Riesgo** (escala subjetiva 0-10)
   - Baja: 0-4
   - Media: 3-7
   - Alta: 6-10

### Variable de Salida:

- **Perfil del Inversionista** (escala 0-10)
  - Conservador: 0-4
  - Moderado: 3-7
  - Arriesgado: 6-10

## Lógica de Inferencia

El sistema utiliza el operador AND para combinar las cuatro variables de entrada directamente, siguiendo este patrón:

```
IF edad IS ... AND ingresos_mensuales IS ... AND tolerancia_riesgo IS ... AND horizonte_inversion IS ... THEN perfil_inversionista IS ...
```

Las 24 reglas están organizadas por grupos según la edad:

1. **Grupo 1**: Personas jóvenes (18-45 años) - Reglas 1-10
2. **Grupo 2**: Personas de edad media (35-75 años) - Reglas 11-16
3. **Grupo 3**: Personas mayores (65-100 años) - Reglas 17-24

Dentro de cada grupo, las reglas se dividen en subgrupos según el nivel de ingresos (altos, medios, bajos) y luego según combinaciones de tolerancia al riesgo y horizonte de inversión.

## Requisitos

- Java Runtime Environment (JRE) 8 o superior
- jFuzzyLogic.jar (incluido en este repositorio)

## Ejecución

Para ejecutar el sistema desde la línea de comandos:

```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl <edad> <horizonte_inversion> <ingresos_mensuales> <tolerancia_riesgo>
```

### Ejemplos:

1. **Perfil conservador:**

```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl 70 3 1500 2
```

(Persona mayor con bajos ingresos, baja tolerancia al riesgo y horizonte corto)

2. **Perfil moderado:**

```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl 50 7 6000 5
```

(Persona de edad media con ingresos medios, tolerancia media y horizonte medio)

3. **Perfil arriesgado:**

```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl 25 20 12000 9
```

(Persona joven con altos ingresos, alta tolerancia al riesgo y horizonte largo)

## Interpretación de Resultados

Al ejecutar el sistema, se mostrará la evaluación del perfil del inversionista en una escala de 0 a 10:

- Valores cercanos a 0-3: Perfil más conservador
- Valores cercanos a 4-6: Perfil moderado
- Valores cercanos a 7-10: Perfil más arriesgado

Además, el sistema mostrará las reglas que se han activado y su nivel de soporte (Support). Un valor de 1.0 indica activación completa de la regla. El valor de la variable de salida `perfil_inversionista` es el que determina el perfil final.

## Archivos del Proyecto

- `perfil_inversionista.fcl`: Archivo principal con la definición del sistema de lógica difusa
- `jFuzzyLogic.jar`: Biblioteca de Java para procesamiento de lógica difusa
- `tipper.fcl`: Ejemplo de sistema de propinas (para referencia)

## Extensión del Sistema

El sistema actual contiene reglas básicas para empezar. Para una clasificación más precisa, se recomienda:

- Agregar más reglas difusas para cubrir más casos
- Ajustar las funciones de membresía según datos reales
- Considerar variables adicionales (como situación familiar, deudas actuales, etc.)
