# Instalador Lauren API para Windows

Configura o **Codex**, o **Claude Desktop**, o **Claude Code** e o **OpenCode** para usar a Lauren API (`https://api.ialauren.com`), em um comando, sem baixar programa.

## Instalar

1. Abra o **PowerShell** (menu Iniciar, digite "PowerShell").
2. Cole o comando abaixo e tecle **Enter**:

```powershell
irm https://raw.githubusercontent.com/LinkjohnDEV/lauren-instalador/v1.0/instalar.ps1 | iex
```

3. Cole a sua **chave** (começa com `lp_`) e tecle Enter. A chave não aparece na tela.
4. Leia o resumo e tecle **Enter** para instalar (ou Ctrl+C para cancelar).

A chave é testada antes de qualquer alteração. Se estiver errada, nada é mexido.

## Desfazer

```powershell
& ([scriptblock]::Create((irm https://raw.githubusercontent.com/LinkjohnDEV/lauren-instalador/v1.0/instalar.ps1))) -Uninstall
```

Volta os arquivos para **exatamente** o que eram antes da primeira instalação, remove as ferramentas e a variável da chave. O que não existia antes é renomeado (`.removido-data`), nunca apagado.

## Requisitos

- Windows 10 ou 11 com PowerShell 5.1 ou mais novo (já vem no Windows).
- **Node.js** instalado (https://nodejs.org), para as ferramentas extras funcionarem.

## O que ele altera

- Arquivos de configuração do Codex (`~/.codex/config.toml`, `AGENTS.md`), do Claude (`~/.claude/settings.json`) e do OpenCode (`~/.config/opencode/opencode.json`).
- A variável de ambiente do seu usuário `GATEWAY_API_KEY` (sua chave).
- Cria as ferramentas extras em `~/.codex/mcp` e o catálogo de modelos em `~/.codex`.
- Fecha o Codex durante a instalação.
- Antes de alterar, guarda cópia em `~/.gateway/backups` (a pasta `original` guarda o estado anterior à primeira instalação).

## Ferramentas extras incluídas

Busca na web, leitura e edição de arquivos, busca de código, memória, raciocínio em etapas, documentação (Context7), execução de **comandos no PowerShell**, REPL de Node, controle do computador (mouse e teclado) e **remoção de pastas temporárias**. As de execução e remoção **rodam sem pedir confirmação a cada uso**, como parte do funcionamento automático. Use em computador de confiança.

## Verificar o arquivo (opcional)

O arquivo `instalar.ps1` desta versão tem o SHA-256:

```
da4764adc75147c47a8a7c7cb3d52a1c58b19a8c14f69071ec810896aac138aa
```

Para conferir: `(Get-FileHash .\instalar.ps1 -Algorithm SHA256).Hash`

## Chave

A chave **nunca** vai neste repositório nem no comando. Ela é digitada na hora e só fica no seu computador.
