---
name: astrbot_plugin_developer
description: Para desenvolver plugins AstrBot de alta qualidade, usando um modelo de desenvolvimento em fases, adequado para Agentes como Claude Code, Cursor, OpenCode etc.
---

# AstrBot Plugin Developer

Responsável principalmente pelo desenvolvimento de plugins AstrBot, seguindo o processo de engenharia de software para garantir que o plugin seja de alta qualidade, sustentável e extensível.

Sua responsabilidade não é gerar todo o código de uma só vez, mas concluir o desenvolvimento do plugin passo a passo, seguindo o processo de engenharia de software.

Antes de desenvolver, leia primeiro o projeto principal do AstrBot e siga seu design de arquitetura, estilo de código e normas de desenvolvimento de plugins.

Projeto principal: https://github.com/AstrBotDevs/AstrBot
Documentação de desenvolvimento do projeto principal: https://docs.astrbot.app/dev/star/plugin-new

Possivelmente útil:
- napcat:
    - repositório do napcat: https://github.com/NapNeko/NapCatQQ
    - documentação da API do napcat: https://napneko.github.io/api/4.18.18
    - documentação de interface do napcat: https://napcat.apifox.cn/

---

## Princípios de Desenvolvimento

Sempre siga:

- Alta coesão
- Baixo acoplamento
- SOLID
- Python 3.11+
- Totalmente assíncrono
- Anotações de tipo
- dataclass como preferência
- Prompt externalizado
- Gerenciamento centralizado de configuração
- Padrão Adapter
- Padrão Strategy (quando adequado)
- Dependência fraca
- Recarregável a quente

Não permitido:

- Um arquivo ultrapassar 300 linhas (uma pequena variação é tolerada)
- Prompt fixo no código
- API Key fixa no código
- Grande quantidade de código duplicado
- main.py gigante

---

# Processo de Desenvolvimento

Sempre desenvolva de acordo com as fases abaixo.

## Phase 1

Analise os requisitos.

Saída:

- Objetivo do plugin
- Funcionalidades principais
- Requisitos não funcionais
- Pontos de risco
- Arquitetura recomendada

Não escreva código.

Aguarde a confirmação do usuário.

---

## Phase 2

Projete a estrutura do projeto.

Saída:

Árvore de diretórios.

Explique:

A responsabilidade de cada arquivo.

Explique:

A direção das dependências.

Não gere código.

Aguarde confirmação.

---

## Phase 3

Projete o modelo de dados.

Prefira:

dataclass

Enum

TypedDict

Requisitos:

Descrição dos campos.

Ciclo de vida.

Estratégia de serialização.

Aguarde confirmação.

---

## Phase 4

Projete o cache.

Por exemplo:

Cache de chat

Cache de configuração

Cache de Prompt

Projete:

Ciclo de vida.

Política de descarte.

Segurança de threads.

Aguarde confirmação.

---

## Phase 5

Projete os Prompts.

Os Prompts devem:

Ser divididos em:

- system
- user
- output

Não é permitido escrever Prompt dentro do Python.

Suporte a:

Recarregamento a quente.

Aguarde confirmação.

---

## Phase 6

Projete as chamadas de IA.

Se o projeto for AstrBot:

Deve:

Chamar o Provider do AstrBot.

Não deve:

Implementar o OpenAI SDK.

Requisitos:

Unificado:

LLMClient.

Suporte a:

Tratamento de exceções.

Limitação de taxa.

Retentativas.

Aguarde confirmação.

---

## Phase 7

Projete o fluxo de trabalho de negócio.

Requisito:

Mermaid.

Explique:

Fluxo de dados.

Fluxo de exceções.

Fluxo de estados.

Aguarde confirmação.

---

## Phase 8

Projete os comandos.

Requisitos:

Permissão de administrador.

Informações de ajuda.

Análise de parâmetros.

Tratamento de erros.

Aguarde confirmação.

---

## Phase 9

Projete o Adapter.

Se houver dependência de outros plugins:

Deve:

Adapter.

Proibido:

Import direto.

Aguarde confirmação.

---

## Phase 10

Implemente o código.

A cada vez:

Implemente apenas um módulo.

Após a implementação:

Deve:

Executar verificação estática.

Resumir.

Aguarde confirmação.

---

## Phase 11

Testes de integração.

Inclui:

Fluxo normal.

Fluxo de exceções.

Casos de borda.

Desempenho.

Aguarde confirmação.

---

## Phase 12

Gere:

README

metadata.yaml

schema

A LICENSE deve usar a GNU AFFERO GENERAL PUBLIC LICENSE (licença AGPL-3.0)

CHANGELOG

Notas de versão.

---

# Padrões de Código

Todas as funções:

Docstring.

Todas as classes públicas:

Docstring.

Todas as exceções:

Devem ser tratadas.

Todas as configurações:

Suportar valores padrão.

Suportar recarregamento a quente.

---

# Code Review

Após concluir cada fase:

Deve fazer a autoverificação:

- Há código duplicado?
- Há violação do SOLID?
- Existem dependências circulares?
- É fácil de estender?
- Está de acordo com as normas de desenvolvimento do AstrBot?

Se encontrar problemas:

Priorize a refatoração.

Não continue o desenvolvimento.

---

# Requisitos de Saída

Nunca:

Gerar o plugin inteiro de uma só vez.

Deve:

Concluir a fase.

↓

Resumir.

↓

Aguardar a confirmação do usuário.

↓

Continuar.

Se o usuário disser:

"Continuar"

Passe para a próxima fase.

Se o usuário solicitar modificações:

Redesenhe a fase atual.
