# Sistema de Clasificación de Perfiles de Inversión con Lógica Difusa

Este proyecto implementa un sistema de lógica difusa para clasificar perfiles de inversión utilizando jFuzzyLogic, una biblioteca de Java para sistemas de inferencia difusa. El sistema evalúa a los potenciales inversionistas en una escala de 0 (muy conservador) a 10 (muy arriesgado) basándose en cuatro variables principales.

## Descripción del Sistema

El sistema clasifica a los inversionistas utilizando lógica difusa a partir de:

### Variables de Entrada:
1. **Edad** (en años)
   - Joven: 18-45 años
   - Medio: 35-75 años
   - Mayor: 65-100 años

2. **Ingresos Mensuales** (en dólares)
   - Bajos: 0-4,000 dólares
   - Medios: 3,000-10,000 dólares
   - Altos: 8,000+ dólares

3. **Tolerancia al Riesgo** (escala subjetiva 0-10)
   - Baja: 0-4
   - Media: 3-7
   - Alta: 6-10

4. **Horizonte de Inversión** (en años)
   - Corto: 0-5 años
   - Medio: 3-10 años
   - Largo: 8-50 años

### Variable de Salida:
- **Perfil del Inversionista** (escala 0-10)
  - Conservador: 0-4
  - Moderado: 3-7
  - Arriesgado: 6-10

## Lógica de Inferencia

El sistema utiliza operadores AND anidados para combinar las variables:
1. Primero combina (edad AND ingresos_mensuales)
2. Luego combina (tolerancia_riesgo AND horizonte_inversion)
3. Finalmente aplica una AND entre estos dos resultados para determinar el perfil final

## Requisitos

- Java Runtime Environment (JRE) 8 o superior
- jFuzzyLogic.jar (incluido en este repositorio)

## Ejecución

Para ejecutar el sistema desde la línea de comandos:

```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl <edad> <ingresos_mensuales> <tolerancia_riesgo> <horizonte_inversion>
```

### Ejemplos:

1. **Perfil conservador:**
```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl 70 1500 2 3
```
(Persona mayor con bajos ingresos, baja tolerancia al riesgo y horizonte corto)

2. **Perfil moderado:**
```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl 50 6000 5 7
```
(Persona de edad media con ingresos medios, tolerancia media y horizonte medio)

3. **Perfil arriesgado:**
```bash
java -jar jFuzzyLogic.jar -e perfil_inversionista.fcl 25 12000 9 20
```
(Persona joven con altos ingresos, alta tolerancia al riesgo y horizonte largo)

## Interpretación de Resultados

Al ejecutar el sistema, se mostrará la evaluación del perfil del inversionista en una escala de 0 a 10:
- Valores cercanos a 0-3: Perfil más conservador
- Valores cercanos a 4-6: Perfil moderado
- Valores cercanos a 7-10: Perfil más arriesgado

## Archivos del Proyecto

- `perfil_inversionista.fcl`: Archivo principal con la definición del sistema de lógica difusa
- `jFuzzyLogic.jar`: Biblioteca de Java para procesamiento de lógica difusa
- `tipper.fcl`: Ejemplo de sistema de propinas (para referencia)

## Extensión del Sistema

El sistema actual contiene reglas básicas para empezar. Para una clasificación más precisa, se recomienda:
- Agregar más reglas difusas para cubrir más casos
- Ajustar las funciones de membresía según datos reales
- Considerar variables adicionales (como situación familiar, deudas actuales, etc.)
