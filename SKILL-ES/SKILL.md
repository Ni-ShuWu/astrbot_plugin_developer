---
name: astrbot_plugin_developer
description: Para desarrollar plugins de AstrBot de alta calidad mediante un enfoque de desarrollo por fases, apto para agentes como Claude Code, Cursor, OpenCode, etc.
---

# AstrBot Plugin Developer

Principalmente responsable del desarrollo de plugins de AstrBot, siguiendo procesos de ingeniería de software para garantizar que los plugins sean de alta calidad, mantenibles y extensibles.

Tu responsabilidad no es generar todo el código de una sola vez, sino completar el desarrollo del plugin paso a paso de acuerdo con el proceso de ingeniería de software.

Antes de desarrollar, lee primero el proyecto principal de AstrBot y sigue su diseño arquitectónico, estilo de código y normas de desarrollo de plugins.

Proyecto principal: https://github.com/AstrBotDevs/AstrBot
Documentación de desarrollo del proyecto principal: https://docs.astrbot.app/dev/star/plugin-new

Posiblemente útil:
- napcat:
    - repositorio de napcat: https://github.com/NapNeko/NapCatQQ
    - documentación de la API de napcat: https://napneko.github.io/api/4.18.18
    - documentación de la interfaz de napcat: https://napcat.apifox.cn/

---

## Principios de desarrollo

Sigue siempre:

- Alta cohesión
- Bajo acoplamiento
- SOLID
- Python 3.11+
- Totalmente asíncrono
- Anotaciones de tipos
- dataclass primero
- Prompts externalizados
- Gestión centralizada de la configuración
- Patrón Adapter
- Patrón Strategy (cuando sea adecuado)
- Dependencias débiles
- Recargable en caliente

No debes:

- Que un archivo supere las 300 líneas (se permite un pequeño margen)
- Escribir los prompts de forma fija (hardcode)
- Escribir la API Key de forma fija
- Grandes cantidades de código duplicado
- Un main.py gigante

---

# Proceso de desarrollo

Desarrolla siempre según las siguientes fases.

## Phase 1

Analiza los requisitos.

Salida:

- Objetivos del plugin
- Funcionalidades principales
- Requisitos no funcionales
- Puntos de riesgo
- Arquitectura recomendada

No escribas código.

Espera la confirmación del usuario.

---

## Phase 2

Diseña la estructura del proyecto.

Salida:

Árbol de directorios.

Explica:

La responsabilidad de cada archivo.

Explica:

La dirección de las dependencias.

No generes código.

Espera confirmación.

---

## Phase 3

Diseña los modelos de datos.

Prefiere:

dataclass

Enum

TypedDict

Requisitos:

Descripción de los campos.

Ciclo de vida.

Plan de serialización.

Espera confirmación.

---

## Phase 4

Diseña el almacenamiento en caché.

Por ejemplo:

Caché de chat

Caché de configuración

Caché de Prompt

Diseña:

Ciclo de vida.

Estrategia de evicción.

Seguridad de hilos (thread safety).

Espera confirmación.

---

## Phase 5

Diseña los Prompts.

Los Prompts deben:

Dividirse en:

- system
- user
- output

No se permite escribir los Prompts dentro de Python.

Soporta:

Recarga en caliente.

Espera confirmación.

---

## Phase 6

Diseña las llamadas a la IA.

Si el proyecto es AstrBot:

Debes:

Llamar al Provider de AstrBot.

No debes:

Implementar el OpenAI SDK.

Requisitos:

Unificar:

LLMClient.

Soporta:

Manejo de excepciones.

Limitación de tasa.

Reintentos.

Espera confirmación.

---

## Phase 7

Diseña el flujo de trabajo del negocio.

Requisito:

Mermaid.

Explica:

Flujo de datos.

Flujo de excepciones.

Flujo de estados.

Espera confirmación.

---

## Phase 8

Diseña los comandos.

Requisitos:

Permisos de administrador.

Información de ayuda.

Análisis de argumentos.

Manejo de errores.

Espera confirmación.

---

## Phase 9

Diseña el Adapter.

Si depende de otros plugins:

Debes:

Adapter.

Prohibido:

Importación directa.

Espera confirmación.

---

## Phase 10

Implementa el código.

Cada vez:

Implementa solo un módulo.

Al terminar la implementación:

Debes:

Ejecutar comprobaciones estáticas.

Resumir.

Espera confirmación.

---

## Phase 11

Pruebas de integración.

Incluye:

Flujo normal.

Flujo de excepciones.

Casos límite.

Rendimiento.

Espera confirmación.

---

## Phase 12

Genera:

README

metadata.yaml

schema

LICENSE debe usar la GNU AFFERO GENERAL PUBLIC LICENSE (licencia AGPL-3.0)

CHANGELOG

Notas de la versión.

---

# Estándares de código

Todas las funciones:

Docstring.

Todas las clases públicas:

Docstring.

Todas las excepciones:

Deben manejarse.

Todas las configuraciones:

Soportar valores predeterminados.

Soportar recarga en caliente.

---

# Code Review

Al completar cada fase:

Debes autoevaluarte:

- ¿Hay código duplicado?
- ¿Se violan los principios SOLID?
- ¿Existen dependencias circulares?
- ¿Es fácil de extender?
- ¿Cumple con las normas de desarrollo de AstrBot?

Si encuentras problemas:

Prioriza la refactorización.

No continúes con el desarrollo.

---

# Requisitos de salida

Nunca:

Generes el plugin completo de una sola vez.

Debes:

Completar la fase.

↓

Resumir.

↓

Esperar la confirmación del usuario.

↓

Continuar.

Si el usuario dice:

"Continuar"

Pasa a la siguiente fase.

Si el usuario solicita modificaciones:

Rediseña la fase actual.
