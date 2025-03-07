
# Bot-Manager-DayZ

O projeto Bot-Manager-DayZ é um bot para Discord desenvolvido para gerenciar servidores DayZ hospedados na Nitrado. Ele foi inicialmente baseado num bot JavaScript chamado DayZero KillFeed, mas foi totalmente reescrito em Python usando a biblioteca Nextcord para interações no Discord, PyMongo para gerenciamento de banco de dados MongoDB e uma estrutura modular com cogs.

## Visão Geral do Projeto

O bot foi projetado com foco em três prioridades principais definidas pelo cliente:
- **Logs detalhados de mortes PvE:** Notificações detalhadas com localização no mapa usando links para o iZurvive.
- **Logs detalhados de mortes PvP:** Similar ao PvE, mas com informações sobre assassino, vítima e arma usada.
- **Sistema de procurados:** Um sistema configurável para adicionar, remover e listar jogadores procurados, com atualizações periódicas de localização.

Além disso, o bot foi redesenhado para usar interfaces modernas e interativas (embeds com botões, menus dropdown e modals) ao invés de depender apenas de comandos slash, melhorando a experiência visual e a usabilidade para os usuários.

## Estrutura do Projeto

O projeto está organizado de forma modular para facilitar manutenção e expansão futura. Abaixo está a estrutura de diretórios:

```
Bot-Manager-DayZ/
│
├── cogs/                       # Pasta para os cogs
│   ├── interfaces/             # Módulo para interfaces interativas
│   │   ├── logs_interface.py   # Interface para logs PvE/PvP
│   │   ├── wanted_interface.py # Interface para sistema de procurados (Versão 1.9)
│   │   ├── lists_interface.py  # Interface para gerenciamento de listas
│   │   └── admin_interface.py  # Interface para comandos administrativos (Versão 1.1)
│   ├── utils/                  # Módulo para utilitários
│   │   ├── api_manager.py      # Gerencia chamadas à API da Nitrado
│   │   ├── map_utils.py        # Funções para lidar com mapas e localização
│   │   └── db_manager.py       # Gerencia o banco de dados MongoDB
│
├── config/                     # Configurações
│   └── config.py               # Arquivo de configuração
│
├── logs/                       # Pasta para logs baixados
│   └── log.ADM                 # Log administrativo do servidor
│
├── main.py                     # Arquivo principal
├── requirements.txt            # Dependências
└── .env                        # Variáveis de ambiente
```

## Funcionalidades Implementadas

### Logs Detalhados de Mortes PvE e PvP
- **Interface:** Acessada pelo comando `/logs`, que abre um embed com botões para iniciar/parar os killfeeds PvE e PvP, ativar/desativar exibição de localização e selecionar mapas (Chernarus ou Livonia).
- **Detalhes:** Os logs PvE mostram o jogador, a causa (ex.: zumbi, dano de queda) e a localização; os logs PvP mostram assassino, vítima, arma e localização.
- **Implementação:** Usa a biblioteca `watchdog` para monitoramento de logs e regex para identificar eventos de morte.

### Sistema de Procurados
- **Interface:** Acessada pelo comando `/procurados`, que abre um embed com botões para adicionar/remover/listar procurados, um dropdown para opções como ativar/desativar localização, configurar recompensas e exibir ranking de caçadores.
- **Detalhes:** Adicionar um jogador abre um modal para inserir nome, motivo e recompensa; as atualizações periódicas (a cada 5 minutos) enviam embeds com localização se ativadas; eventos de conexão/desconexão/morte são monitorados em tempo real (a cada 1 minuto).
- **Implementação:** Usa MongoDB para armazenar a lista e configurações, tarefas Nextcord para monitoramento, e regex para parsing de logs. A versão 1.9 corrige erros de status e timestamp dos eventos.

### Gerenciamento de Listas (Whitelist, Banlist, Priority)
- **Interface:** Acessada pelo comando `/lists`, que abre um embed com um dropdown para selecionar o tipo de lista e botões para adicionar/remover/exibir/resetar listas.
- **Detalhes:** Adicionar/remover jogadores usa modals e dropdowns; as atualizações são sincronizadas com o servidor Nitrado via API.
- **Implementação:** Usa MongoDB para armazenar listas e a biblioteca `requests` para interagir com a API da Nitrado.

### Interface Administrativa
- **Interface:** Acessada pelo comando `/admin`, que abre um embed com botões para configurar canais e criar canais padrão, além do comando `/admin_clear` para limpar mensagens.
- **Detalhes:** A configuração de canais usa um modal para inserir IDs; o botão "Criar Canais Padrão" agora exibe um dropdown para escolher a categoria antes de criar os canais `🐕┃𝖬𝗈𝗋𝗍𝖾𝗌-𝖯𝖵𝖤`, `👻┃𝖬𝗈𝗋𝗍𝖾𝗌-𝖯𝖵𝖯` e `🕵️┃𝖯𝗋𝗈𝖼𝗎𝗋𝖺𝖽𝗈𝗌`. Versão 1.1 implementa essa funcionalidade.
- **Implementação:** Usa MongoDB para armazenar configurações e Nextcord para criar canais com categoria.

## Testes a Realizar

Para garantir que o bot funcione corretamente, os seguintes testes devem ser realizados em um servidor de teste no Discord com membros online:
1. **Testar a Interface de Logs (/logs):**
   - Iniciar os killfeeds PvE e PvP e simular mortes no servidor DayZ para verificar se as notificações aparecem nos canais corretos.
   - Ativar/desativar a exibição de localização e verificar se os links do iZurvive são incluídos/excluídos conforme esperado.
   - Alterar mapas (Chernarus/Livonia) e confirmar se os links são atualizados corretamente.
2. **Testar o Sistema de Procurados (/procurados):**
   - Adicionar um jogador procurado usando o modal e verificar a notificação no canal configurado.
   - Remover um jogador e confirmar se a lista é atualizada no MongoDB e no status interno.
   - Simular conexões/desconexões no servidor DayZ e verificar se os eventos são detectados corretamente com status e timestamp precisos.
   - Ativar atualizações periódicas de localização e verificar se os embeds são enviados a cada 5 minutos com coordenadas reais (quando disponíveis).
   - Testar restrições de permissão com usuários sem os papéis "ADM" ou "PM".
3. **Testar o Gerenciamento de Listas (/lists):**
   - Adicionar jogadores às listas whitelist, banlist e priority list, e verificar as atualizações no MongoDB e no servidor Nitrado.
   - Remover jogadores e confirmar se as listas são atualizadas.
   - Resetar uma lista e garantir que ela é limpa no MongoDB e no Nitrado.
   - Testar restrições de permissão.
4. **Testar a Interface Administrativa (/admin):**
   - Criar canais padrão usando o botão e verificar se o dropdown de categorias aparece e se os canais são criados na categoria selecionada.
   - Configurar IDs de canais usando o modal e confirmar se as configurações são salvas no MongoDB.
   - Usar `/admin_clear` pra limpar mensagens e verificar se até 100 mensagens são removidas.
   - Testar restrições de permissão com usuários sem o papel "ADM".
5. **Testes Gerais:**
   - Garantir que todos os botões, dropdowns e modals funcionem sem erros.
   - Verificar se o bot lida com erros de forma elegante (ex.: falhas na API da Nitrado ou permissões insuficientes).
   - Testar a responsividade com múltiplos usuários interagindo simultaneamente.

## Melhorias Futuras

Possíveis melhorias para o bot com base na versão original em JavaScript e requisitos adicionais:
- Adicionar um sistema de economia (ex.: DzCoins) e uma loja, como visto no bot "raiox".
- Implementar mapas de calor para atividades PvP/PvE usando APIs externas ou bibliotecas.
- Melhorar os embeds com emojis personalizados e elementos visuais mais ricos.
- Adicionar suporte para tarefas agendadas (ex.: reinícios de servidor), como no bot "raiox".

## Licença

Este projeto é licenciado sob os termos da licença MIT.

## Desenvolvedores

- Criado por: CodeProjects
- Modificado por: CodeProjects
- Data da Modificação: 07/03/2025
- Versão: 1.1
- Desenvolvedores da Versão: CodeProjects e RedeGamer - Serviços Escaláveis para seu Game
