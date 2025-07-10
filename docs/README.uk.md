# Context7 MCP - Актуальна документація для будь-якого промпту

[![Website](https://img.shields.io/badge/Website-context7.com-blue)](https://context7.com) [![smithery badge](https://smithery.ai/badge/@upstash/context7-mcp)](https://smithery.ai/server/@upstash/context7-mcp) [<img alt="Install in VS Code (npx)" src="https://img.shields.io/badge/VS_Code-VS_Code?style=flat-square&label=Install%20Context7%20MCP&color=0098FF">](https://insiders.vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%7B%22name%22%3A%22context7%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40upstash%2Fcontext7-mcp%40latest%22%5D%7D)

## ❌ Без Context7

LLM покладаються на застарілу або узагальнену інформацію про бібліотеки, з якими ви працюєте. В результаті цього ви отримуєте:

- ❌ Застарілі приклади коду багаторічної давнини
- ❌ Вигадані API, які навіть не існують
- ❌ Узагальнені відповіді для старих бібліотек

## ✅ З Context7

Context7 MCP отримує актуальну документацію та приклади коду, суворо відповідні потрібній версії, прямо з вихідних джерел та вставляє їх прямо у ваш промпт.

Додайте рядок `use context7` у промпт для Cursor:

```txt
Створи базовий Next.js проект з маршрутизатором додатків. Use context7
```

```txt
Створи скрипт, що видаляє рядки, де місто дорівнює "", використовуючи облікові дані PostgreSQL. Use context7
```

Context7 MCP підвантажує свіжі приклади коду та документацію з джерел прямо в контекст вашої LLM.

- 1️⃣ Напишіть свій промпт так, як писали його завжди
- 2️⃣ Додайте до промпту `use context7`
- 3️⃣ Отримайте працюючий результат

Ніякого перемикання між вкладками, вигаданого API або застарілого коду.

## 🛠️ Початок роботи

### Вимоги

- Node.js >= v18.0.0
- Cursor, Windsurf, Claude Desktop або інший MCP клієнт

### Встановлення через Smithery

Скористайтеся [Smithery](https://smithery.ai/server/@upstash/context7-mcp), щоб автоматично встановити MCP сервер Context7 для Claude Desktop:

```bash
npx -y @smithery/cli install @upstash/context7-mcp --client claude
```

### Встановлення в Cursor

Перейдіть у вкладку: `Settings` -> `Cursor Settings` -> `MCP` -> `Add new global MCP server`

Рекомендується вставити конфігурацію у файл `~/.cursor/mcp.json`. Також можна встановити конфігурацію для конкретного проекту, створивши файл `.cursor/mcp.json` в його директорії. Дивіться [документацію Cursor MCP](https://docs.cursor.com/context/model-context-protocol) для отримання додаткової інформації.

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

<details>
<summary>Альтернативний варіант - Bun</summary>

```json
{
  "mcpServers": {
    "context7": {
      "command": "bunx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

</details>

<details>
<summary>Альтернативний варіант - Deno</summary>

```json
{
  "mcpServers": {
    "context7": {
      "command": "deno",
      "args": ["run", "--allow-env", "--allow-net", "npm:@upstash/context7-mcp"]
    }
  }
}
```

</details>

### Встановлення в Windsurf

Додайте наступні рядки до вашого конфігураційного файлу Windsurf MCP. Дивіться [документацію Windsurf MCP](https://docs.windsurf.com/windsurf/mcp) для отримання додаткової інформації.

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

### Встановлення в VS Code

[<img alt="Встановлення в VS Code (npx)" src="https://img.shields.io/badge/VS_Code-VS_Code?style=flat-square&label=Встановити%20Context7%20MCP&color=0098FF">](https://insiders.vscode.dev/redirect?url=vscode%3Amcp%2Finstall%3F%7B%22name%22%3A%22context7%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40upstash%2Fcontext7-mcp%40latest%22%5D%7D)
[<img alt="Встановлення в VS Code Insiders (npx)" src="https://img.shields.io/badge/VS_Code_Insiders-VS_Code_Insiders?style=flat-square&label=Встановити%20Context7%20MCP&color=24bfa5">](https://insiders.vscode.dev/redirect?url=vscode-insiders%3Amcp%2Finstall%3F%7B%22name%22%3A%22context7%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22%40upstash%2Fcontext7-mcp%40latest%22%5D%7D)

Додайте наступні рядки до вашого конфігураційного файлу VS Code MCP. Дивіться [документацію VS Code MCP](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) для отримання додаткової інформації.

```json
{
  "servers": {
    "Context7": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

### Встановлення в Zed

Можна встановити через [Zed розширення](https://zed.dev/extensions?query=Context7) або додати наступні рядки до `settings.json`. Дивіться [документацію Zed Context Server](https://zed.dev/docs/assistant/context-servers) для отримання додаткової інформації.

```json
{
  "context_servers": {
    "Context7": {
      "command": {
        "path": "npx",
        "args": ["-y", "@upstash/context7-mcp"]
      },
      "settings": {}
    }
  }
}
```

### Встановлення в Claude Code

Запустіть наступну команду для встановлення. Дивіться [документацію Claude Code MCP](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/tutorials#set-up-model-context-protocol-mcp) для отримання додаткової інформації.

```sh
claude mcp add context7 -- npx -y @upstash/context7-mcp
```

### Встановлення в Claude Desktop

Додайте наступні рядки до вашого конфігураційного файлу `claude_desktop_config.json`. Дивіться [документацію Claude Desktop MCP](https://modelcontextprotocol.io/quickstart/user) для отримання додаткової інформації.

```json
{
  "mcpServers": {
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

### Встановлення в BoltAI

Відкрийте сторінку "Settings", перейдіть до "Plugins" та додайте наступні JSON-рядки:

```json
{
  "mcpServers": {
    "context7": {
      "args": ["-y", "@upstash/context7-mcp"],
      "command": "npx"
    }
  }
}
```

### Використання Docker

Якщо ви віддаєте перевагу запуску MCP сервера в Docker контейнері:

1. **Створіть образ Docker:**

   Спочатку створіть `Dockerfile` в корені вашого проекту (або в будь-якому іншому місці):

   <details>
   <summary>Натисніть, щоб переглянути вміст файлу Dockerfile</summary>

   ```Dockerfile
   FROM node:18-alpine

   WORKDIR /app

   # Встановіть останню версію пакету глобально
   RUN npm install -g @upstash/context7-mcp

   # Відкрийте стандартний порт, якщо це необхідно (необов'язково, це залежить від взаємодії з MCP клієнтом)
   # EXPOSE 3000

   # Стандартна команда для запуску сервера
   CMD ["context7-mcp"]
   ```

   </details>

   Потім зберіть образ, використовуючи тег (наприклад, `context7-mcp`). **Переконайтеся, що Docker Desktop (або демон Docker) працює.** Запустіть наступну команду в тій же директорії, де збережено `Dockerfile`:

   ```bash
   docker build -t context7-mcp .
   ```

2. **Налаштуйте ваш MCP клієнт:**

   Оновіть вашу конфігурацію MCP клієнта, щоб використовувати Docker команду.

   _Приклад для cline_mcp_settings.json:_

   ```json
   {
     "mcpServers": {
       "Сontext7": {
         "autoApprove": [],
         "disabled": false,
         "timeout": 60,
         "command": "docker",
         "args": ["run", "-i", "--rm", "context7-mcp"],
         "transportType": "stdio"
       }
     }
   }
   ```

   _Примітка: це приклад конфігурації. Зверніться до конкретних прикладів для вашого MCP-клієнта (наприклад, Cursor, VS Code тощо), в попередніх розділах цього README, щоб адаптувати структуру (наприклад, `mcpServers` замість `servers`). Також переконайтеся, що ім'я образу в `args` відповідає тегу, використаному при виконанні команди `docker build`._

### Встановлення в Windows

Конфігурація в Windows трохи відрізняється від Linux або macOS (_як приклад використовується `Cline`_). Однак, ці ж принципи застосовні до інших редакторів. У разі необхідності зверніться до налаштувань `command` та `args`.

```json
{
  "mcpServers": {
    "github.com/upstash/context7-mcp": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "@upstash/context7-mcp"],
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### Змінні середовища

- `DEFAULT_MINIMUM_TOKENS`: мінімальна кількість токенів, необхідна для отримання документації (за замовчуванням: 10000).

Приклади:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"],
      "env": {
        "DEFAULT_MINIMUM_TOKENS": "10000"
      }
    }
  }
}
```

### Доступні інструменти

- `resolve-library-id`: перетворює загальну назву бібліотеки на сумісний з Context7 ідентифікатор.
  - `libraryName` (обов'язково)
- `get-library-docs`: отримує документацію бібліотеки за сумісним з Context7 ідентифікатором.
  - `context7CompatibleLibraryID` (обов'язково)
  - `topic` (необов'язково): фокусує документацію на певній темі (наприклад, "routing", "hooks")
  - `tokens` (необов'язково, за замовчуванням 10000): максимальне число токенів у відповіді. Значення нижче заданого `DEFAULT_MINIMUM_TOKENS` будуть автоматично збільшені до нього.

## Розробка

Склонуйте проект та встановіть залежності:

```bash
bun i
```

Збірка:

```bash
bun run build
```

### Приклад локальної конфігурації

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["tsx", "/path/to/folder/context7-mcp/src/index.ts"]
    }
  }
}
```

### Тестування за допомогою інспектора MCP

```bash
npx -y @modelcontextprotocol/inspector npx @upstash/context7-mcp
```

## Вирішення проблем

### ERR_MODULE_NOT_FOUND

Якщо ви бачите цю помилку, використовуйте `bunx` замість `npx`.

```json
{
  "mcpServers": {
    "context7": {
      "command": "bunx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

Часто це вирішує проблему з відсутніми модулями, особливо в середовищі, де `npx` некоректно встановлює або розв'язує бібліотеки.

### Проблеми з розв'язанням ESM

Якщо ви стикаєтеся з проблемою типу: `Error: Cannot find module 'uriTemplate.js'`, спробуйте запустити команду з прапором `--experimental-vm-modules`:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "--node-options=--experimental-vm-modules", "@upstash/context7-mcp"]
    }
  }
}
```

### Проблеми з TLS/сертифікатами

Використовуйте прапор `--experimental-fetch` з `npx`, щоб уникнути помилок, пов'язаних з TLS:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "--node-options=--experimental-fetch", "@upstash/context7-mcp"]
    }
  }
}
```

### Помилки MCP клієнта

1. Спробуйте додати тег `@latest` до імені пакету.

2. Спробуйте використовувати `bunx` як альтернативу `npx`.

3. Спробуйте використовувати `deno` як заміну `npx` або `bunx`.

4. Переконайтеся, що використовуєте версію Node v18 або вище, щоб `npx` підтримував вбудований `fetch`.

## Відмова від відповідальності

Проекти Context7 створюються спільнотою. Ми прагнемо підтримувати високу якість, однак не можемо гарантувати точність, повноту або безпеку всієї документації бібліотек. Проекти, представлені в Context7, розробляються та підтримуються їхніми авторами, а не командою Context7.

Якщо ви зіткнетеся з підозрілим, неуместним або потенційно шкідливим контентом, будь ласка, скористайтеся кнопкою "Report" на сторінці проекту, щоб негайно повідомити нас. Ми уважно ставимося до всіх звернень та оперативно перевіряємо позначені матеріали, щоб забезпечити надійність та безпеку платформи.

Використовуючи Context7, ви визнаєте, що робите це на власний розсуд та на свій страх і ризик.

## Залишайтеся з нами на зв'язку

Будьте в курсі останніх новин на наших платформах:

- 📢 Слідкуйте за нашими новинами на [X](https://x.com/contextai), щоб бути в курсі останніх новин
- 🌐 Завітайте на наш [сайт](https://context7.com)
- 💬 За бажанням приєднуйтеся до нашої [спільноти в Discord](https://upstash.com/discord)

## Context7 у ЗМІ

- [Better Stack: "Безкоштовний інструмент робить Cursor в 10 разів розумнішим"](https://youtu.be/52FC3qObp9E)
- [Cole Medin: "Це, безумовно, НАЙКРАЩИЙ MCP-сервер для AI-помічників у коді"](https://www.youtube.com/watch?v=G7gK8H6u7Rs)
- [Income stream surfers: "Context7 + SequentialThinking MCPs: Це вже AGI?"](https://www.youtube.com/watch?v=-ggvzyLpK6o)
- [Julian Goldie SEO: "Context7: оновлення MCP-агента"](https://www.youtube.com/watch?v=CTZm6fBYisc)
- [JeredBlu: "Context 7 MCP: миттєвий доступ до документації + налаштування для VS Code"](https://www.youtube.com/watch?v=-ls0D-rtET4)
- [Income stream surfers: "Context7: новий MCP-сервер, який змінить кодування з ШІ"](https://www.youtube.com/watch?v=PS-2Azb-C3M)
- [AICodeKing: "Context7 + Cline & RooCode: Цей MCP сервер робить CLINE в 100 разів ЕФЕКТИВНІШЕ!"](https://www.youtube.com/watch?v=qZfENAPMnyo)
- [Sean Kochel: "5 MCP серверів для стрімкого вайб-програмування (Підключи і Працюй)"](https://www.youtube.com/watch?v=LqTQi8qexJM)

## Історія зірок на GitHub

[![Графік історії зірок на GitHub](https://api.star-history.com/svg?repos=upstash/context7&type=Date)](https://www.star-history.com/#upstash/context7&Date)

## Ліцензія

MIT 