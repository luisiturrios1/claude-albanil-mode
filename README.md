# 🧱 Claude, Codex & Cursor: modo albañil mexicano

«Arre, maistro. Vamos a dejar ese código bien aplomado».

Una skill para que **Claude Code, Codex y Cursor** hablen con el ingenio y el trato de un maestro de obra mexicano: expresiones coloquiales, analogías de construcción y humor ligero, conservando la precisión técnica.

La misma carpeta `skills/albanil-mode` funciona en los tres agentes. No requiere dependencias ni ejecuta scripts.

## Instalación

Necesitas Git y acceso SSH a GitHub. Clona este repo y entra en él:

```sh
git clone git@github.com:luisiturrios1/claude-albanil-mode.git
cd claude-albanil-mode
```

Si no tienes SSH configurado, puedes clonar por HTTPS:

```sh
git clone https://github.com/luisiturrios1/claude-albanil-mode.git
cd claude-albanil-mode
```

### Claude Code — todos tus proyectos

Desde la raíz de este repo:

```sh
mkdir -p "$HOME/.claude/skills"
cp -R skills/albanil-mode "$HOME/.claude/skills/"
```

Abre una nueva sesión de Claude Code y escribe:

```text
/albanil-mode
```

También puedes pedir: «Activa modo albañil y ayúdame a corregir este bug».

### Codex — todos tus proyectos

Desde la raíz de este repo:

```sh
mkdir -p "$HOME/.agents/skills"
cp -R skills/albanil-mode "$HOME/.agents/skills/"
```

Abre una nueva sesión de Codex e invócala:

```text
$albanil-mode Explícame este proyecto, maistro.
```

### Cursor — todos tus proyectos

Desde la raíz de este repo:

```sh
mkdir -p "$HOME/.cursor/skills"
cp -R skills/albanil-mode "$HOME/.cursor/skills/"
```

Reinicia Cursor. En el chat de Agent, escribe `/` y selecciona `albanil-mode`:

```text
/albanil-mode Explícame este proyecto, maistro.
```

Para mantener la skill en contexto durante toda la sesión, úsala como **Custom Mode** desde el selector de skills. Una invocación normal con `/` la adjunta a un solo mensaje.

Cursor también descubre skills en `~/.agents/skills/` y `.agents/skills/`. Si ya usaste la instalación de Codex, no necesitas otra copia para Cursor local.

Las skills globales de tu máquina no se copian automáticamente a entornos remotos. Para Cloud Agents, puedes sincronizar las de `~/.cursor/skills/` desde **Settings → Agents → Sync Skills for Cloud Agents**, o incluir la skill en el proyecto.

### Solo en un proyecto

En lugar de instalar globalmente, copia la carpeta dentro del proyecto de destino. Sustituye `/ruta/a/tu/proyecto`:

```sh
# Claude Code
mkdir -p /ruta/a/tu/proyecto/.claude/skills
cp -R skills/albanil-mode /ruta/a/tu/proyecto/.claude/skills/

# Codex
mkdir -p /ruta/a/tu/proyecto/.agents/skills
cp -R skills/albanil-mode /ruta/a/tu/proyecto/.agents/skills/

# Cursor
mkdir -p /ruta/a/tu/proyecto/.cursor/skills
cp -R skills/albanil-mode /ruta/a/tu/proyecto/.cursor/skills/
```

Elige instalación global o por proyecto para cada agente; evita mantener copias duplicadas con el mismo nombre. Si ya existe una carpeta `albanil-mode` personalizada en el destino, respáldala antes de copiar.

## Uso

```text
Activa modo albañil. Revisa por qué falla este test.
Explícame Docker como si estuviéramos en la obra.
Bájale a la carrilla y dame los pasos exactos.
Desactiva modo albañil y responde normal.
```

Ejemplo de respuesta:

> Mire, maistro: ese contenedor arranca, pero la aplicación escucha en `127.0.0.1`. Hay que configurarla para escuchar en `0.0.0.0` y publicar el puerto; así ya puede recibir conexiones desde fuera del contenedor.

El modo afecta la conversación. El código y los comandos mantienen su sintaxis; los entregables formales respetan el registro que pidas. El agente puede descubrir la skill cuando solicites este tono; invocarla explícitamente ayuda a activarla. Es una instrucción de estilo para el modelo, no una garantía de persistencia entre sesiones.

## Actualización y desinstalación

Para actualizar, ejecuta `git pull --ff-only` dentro de este repo y vuelve a copiar la carpeta al destino que elegiste. Para desinstalar, elimina únicamente la carpeta `albanil-mode` de ese destino y abre una nueva sesión. Si la instalaste por proyecto, revisa también sus carpetas locales.

## Personalización

Edita [`skills/albanil-mode/SKILL.md`](skills/albanil-mode/SKILL.md) para ajustar expresiones, humor y ejemplos. Después vuelve a copiar la skill instalada.

## Referencias

- [Skills en Cursor](https://cursor.com/docs/skills): instalación, invocación y Custom Modes.
- [Skills en Claude Code](https://code.claude.com/docs/en/skills): formato, rutas e invocación con `/`.
- [Instalación de skills para Codex y Claude Code — OpenAI Docs](https://developers.openai.com/api/reference/cli): rutas globales y por proyecto.
- [Construir skills — OpenAI Docs](https://learn.chatgpt.com/docs/build-skills): estructura de una skill.

## Licencia

[MIT](LICENSE).
