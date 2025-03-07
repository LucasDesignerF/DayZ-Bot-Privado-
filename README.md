# Bot-Manager-DayZ

<div style="text-align: center; padding: 20px;">
    <img src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/d8827203-d7df-4f8f-a846-62430fe5169d/d59zm2x-29cd82d0-3b58-4023-8bfd-50fea4cef6be.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcL2Q4ODI3MjAzLWQ3ZGYtNGY4Zi1hODQ2LTYyNDMwZmU1MTY5ZFwvZDU5em0yeC0yOWNkODJkMC0zYjU4LTQwMjMtOGJmZC01MGZlYTRjZWY2YmUucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.OSJ3kN9ISyZFyUotHlbt2L91g-oyVCJ2k0UOP4Rkno0" alt="Logo DayZ" style="max-width: 300px; margin-bottom: 20px;">
    <h1 style="font-size: 2.5em; color: #e5e5e5; font-weight: bold; text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);">
        <i class="fas fa-skull-crossbones" style="color: #8b0000; margin-right: 10px;"></i> Bot-Manager-DayZ
    </h1>
    <p style="font-size: 1.2em; color: #b3b3b3;">Um Bot Moderno para Servidores DayZ no Discord</p>
    <a href="https://dayz-doc.redebots.shop/" target="_blank" style="display: inline-block; background-color: #8b0000; color: #fff; padding: 10px 20px; border-radius: 5px; text-decoration: none; margin-top: 10px; transition: background-color 0.3s;">Ver Documentação Completa</a>
</div>

---

<div style="background-color: rgba(34, 34, 34, 0.95); border: 1px solid #444; border-radius: 0.5rem; padding: 2rem; margin: 2rem 0; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5); color: #e5e5e5;">

## Visão Geral do Projeto

O projeto <span style="background-color: #4a2c2a; padding: 0.5rem; border-radius: 0.3rem;">Bot-Manager-DayZ</span> é um bot para Discord desenvolvido para gerenciar servidores DayZ hospedados na Nitrado. Ele foi inicialmente baseado num bot JavaScript chamado <span style="background-color: #4a2c2a; padding: 0.5rem; border-radius: 0.3rem;">DayZero KillFeed</span>, mas foi totalmente reescrito em Python usando a biblioteca <span style="background-color: #4a2c2a; padding: 0.5rem; border-radius: 0.3rem;">Nextcord</span> para interações no Discord, <span style="background-color: #4a2c2a; padding: 0.5rem; border-radius: 0.3rem;">PyMongo</span> para gerenciamento de banco de dados MongoDB e uma estrutura modular com cogs.

### Prioridades do Cliente
- **Logs detalhados de mortes PvE:** Notificações detalhadas com localização no mapa usando links para o iZurvive.
- **Logs detalhados de mortes PvP:** Similar ao PvE, mas com informações sobre assassino, vítima e arma usada.
- **Sistema de procurados:** Um sistema configurável para adicionar, remover e listar jogadores procurados, com atualizações periódicas de localização.

O bot utiliza interfaces modernas com embeds, botões, menus dropdown e modals, melhorando a experiência visual e usabilidade em relação a comandos slash tradicionais.

</div>

---

<div style="background-color: rgba(34, 34, 34, 0.95); border: 1px solid #444; border-radius: 0.5rem; padding: 2rem; margin: 2rem 0; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5); color: #e5e5e5;">

## Estrutura do Projeto

O projeto é modular para facilitar manutenção e expansão. Veja a estrutura de diretórios:

```plaintext
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

</div>

---

<div style="background-color: rgba(34, 34, 34, 0.95); border: 1px solid #444; border-radius: 0.5rem; padding: 2rem; margin: 2rem 0; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5); color: #e5e5e5;">

## Funcionalidades Implementadas

### <i class="fas fa-scroll" style="color: #8b0000; margin-right: 10px;"></i> Logs Detalhados de Mortes PvE e PvP
- **Interface:** Comando `/logs` abre um embed com botões para iniciar/parar killfeeds, ativar/desativar localização e selecionar mapas (Chernarus/Livonia).
- **Detalhes:** PvE exibe jogador, causa e localização; PvP exibe assassino, vítima, arma e localização.
- **Implementação:** Usa <code>watchdog</code> para monitoramento de logs e regex para parsing.

### <i class="fas fa-skull" style="color: #8b0000; margin-right: 10px;"></i> Sistema de Procurados
- **Interface:** Comando `/procurados` abre um embed com botões para adicionar/remover/listar procurados e um dropdown para opções (localização, recompensas, ranking).
- **Detalhes:** Modal para adicionar jogador (nome, motivo, recompensa); atualizações a cada 5 minutos; monitoramento de eventos a cada 1 minuto. Versão 1.9 corrige status e timestamp.
- **Implementação:** MongoDB para armazenamento, tarefas Nextcord e regex para logs.

### <i class="fas fa-list" style="color: #8b0000; margin-right: 10px;"></i> Gerenciamento de Listas (Whitelist, Banlist, Priority)
- **Interface:** Comando `/lists` abre um embed com dropdown para tipo de lista e botões para gerenciar.
- **Detalhes:** Modals e dropdowns para adicionar/remover; sincronização com Nitrado via API.
- **Implementação:** MongoDB para listas e <code>requests</code> para API.

### <i class="fas fa-cog" style="color: #8b0000; margin-right: 10px;"></i> Interface Administrativa
- **Interface:** Comando `/admin` abre um embed com botões para configurar canais e criar canais padrão; `/admin_clear` limpa mensagens.
- **Detalhes:** Modal para IDs de canais; botão cria canais com dropdown de categoria (Versão 1.1).
- **Implementação:** MongoDB para configurações e Nextcord para canais.

</div>

---

<div style="background-color: rgba(34, 34, 34, 0.95); border: 1px solid #444; border-radius: 0.5rem; padding: 2rem; margin: 2rem 0; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5); color: #e5e5e5;">

## Testes a Realizar

Testes a serem feitos com membros online em um servidor de teste:
1. **Interface de Logs (/logs):**
   - Simular mortes e verificar notificações nos canais corretos.
   - Testar exibição de localização e troca de mapas.
2. **Sistema de Procurados (/procurados):**
   - Adicionar/remover jogadores e verificar notificações e lista.
   - Simular eventos (conexão/desconexão) e checar status/timestamp.
   - Testar atualizações periódicas e permissões.
3. **Gerenciamento de Listas (/lists):**
   - Adicionar/remover/resetar listas e verificar MongoDB/Nitrado.
   - Testar permissões.
4. **Interface Administrativa (/admin):**
   - Criar canais padrão com dropdown e verificar localização.
   - Configurar IDs e limpar mensagens; testar permissões.
5. **Testes Gerais:**
   - Checar funcionamento de botões/dropdowns/modals.
   - Verificar tratamento de erros e responsividade.

</div>

---

<div style="background-color: rgba(34, 34, 34, 0.95); border: 1px solid #444; border-radius: 0.5rem; padding: 2rem; margin: 2rem 0; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5); color: #e5e5e5;">

## Melhorias Futuras

- Sistema de economia (DzCoins) e loja (inspirado no "raiox").
- Mapas de calor para atividades PvP/PvE.
- Embeds com emojis personalizados e visuais ricos.
- Suporte para tarefas agendadas (ex.: reinícios).

</div>

---

<div style="background-color: rgba(34, 34, 34, 0.95); border: 1px solid #444; border-radius: 0.5rem; padding: 2rem; margin: 2rem 0; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5); color: #e5e5e5;">

## Licença

Este projeto é licenciado sob os termos da licença MIT.

</div>

---

<div style="text-align: center; padding: 20px; background-color: rgba(139, 0, 0, 0.5); color: #b3b3b3; border-radius: 0.5rem;">
    <p>© 2025 Bot-Manager-DayZ Project</p>
    <p>Criado por: CodeProjects</p>
    <p>Modificado por: CodeProjects</p>
    <p>Data da Modificação: 07/03/2025</p>
    <p>Versão: 1.1</p>
    <p>Desenvolvedores da Versão: CodeProjects e RedeGamer - Serviços Escaláveis para seu Game</p>
</div>

<!-- FontAwesome para ícones -->
<script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>


