# Сборка на чистой macOS

```bash
# 1. Инструменты командной строки (git и компиляторы)
xcode-select --install

# 2. Homebrew (если ещё нет)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 3. Node 22 LTS (в репозитории требуется >= 22.18)
brew install node@22
echo 'export PATH="/opt/homebrew/opt/node@22/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# 4. pnpm (репозиторий закреплён на pnpm@11.10.0 через поле packageManager)
corepack enable          # если corepack отсутствует: npm install -g pnpm@11

# 5. Клонирование проекта и переход на ветку с правками
git clone <url-репозитория> vscode-gitlens
cd vscode-gitlens
git checkout 18.3.0-1

# 6. Зависимости (все 11 workspace-пакетов)
pnpm install

# 7. Корпоративная сборка VSIX
CORPORATE_BUILD=1 pnpm run package
# → в корне появится gitlens-18.3.0.vsix
```
