<p align="center">
  <img src="https://imgur.com/Vlxf8T7" alt="Bot-Manager-DayZ Banner" width="400" style="border-radius: 50%; box-shadow: 0 0 15px rgba(139, 0, 0, 0.5);"/>
</p>

<h1 align="center">☠️ Bot-Manager-DayZ</h1>
<p align="center">
  <strong>Um bot moderno e poderoso para gerenciar servidores DayZ no Discord.</strong><br>
  Desenvolvido por <a href="https://github.com/CodeProjects">CodeProjects</a> | Parceiro <a href="https://discord.gg/redegamer">RedeGamer</a>
</p>

<p align="center">
  <a href="https://dayz-doc.redebots.shop/"><img src="https://img.shields.io/badge/Documentação-Live-brightgreen?style=for-the-badge&logo=readme" alt="Documentação Live"/></a>
  <a href="https://github.com/CodeProjects/Bot-Manager-DayZ"><img src="https://img.shields.io/github/stars/CodeProjects/Bot-Manager-DayZ?style=for-the-badge&logo=github&color=yellow" alt="GitHub Stars"/></a>
  <a href="https://github.com/CodeProjects/Bot-Manager-DayZ/fork"><img src="https://img.shields.io/github/forks/CodeProjects/Bot-Manager-DayZ?style=for-the-badge&logo=github&color=orange" alt="GitHub Forks"/></a>
  <a href="https://github.com/CodeProjects/Bot-Manager-DayZ/issues"><img src="https://img.shields.io/github/issues/CodeProjects/Bot-Manager-DayZ?style=for-the-badge&logo=github&color=red" alt="GitHub Issues"/></a>
  <a href="https://discord.gg/redegamer"><img src="https://img.shields.io/badge/Discord-Join%20Us-7289DA?style=for-the-badge&logo=discord" alt="Join Discord"/></a>
  <img src="https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge" alt="Status Active"/>
  <img src="https://img.shields.io/badge/Version-1.1-blue?style=for-the-badge" alt="Version 1.1"/>
</p>

---

## 🚀 Sobre o Projeto

O **Bot-Manager-DayZ** é um bot Discord projetado para gerenciar servidores DayZ hospedados na Nitrado. Inspirado no antigo *DayZero KillFeed* (JavaScript), foi reescrito em Python com uma arquitetura modular baseada em cogs, usando **Nextcord** para interações e **PyMongo** para banco de dados MongoDB. O foco é oferecer uma experiência interativa com embeds, botões, menus dropdown e modals.

### 🎯 Funcionalidades Principais
- **Logs de Mortes PvE/PvP**: Notificações detalhadas com localização via iZurvive.
- **Sistema de Procurados**: Gerencie jogadores procurados com recompensas e atualizações periódicas.
- **Gerenciamento de Listas**: Controle whitelist, banlist e priority com sincronização Nitrado.
- **Interface Administrativa**: Configure canais e crie estruturas padrão com facilidade.

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia       | Descrição                          |
|------------------|------------------------------------|
| **Python**       | Linguagem principal                |
| **Nextcord**     | Interações Discord (fork do discord.py) |
| **PyMongo**      | Banco de dados MongoDB            |
| **Watchdog**     | Monitoramento de logs             |
| **Requests**     | Chamadas à API Nitrado            |
| **Regex**        | Parsing de logs                   |

---

## 📋 Estrutura do Projeto

Bot-Manager-DayZ/
│
├── cogs/                       # Módulos interativos
│   ├── interfaces/             # Interfaces do bot
│   │   ├── logs_interface.py   # Logs PvE/PvP
│   │   ├── wanted_interface.py # Sistema de procurados (v1.9)
│   │   ├── lists_interface.py  # Gerenciamento de listas
│   │   └── admin_interface.py  # Administração (v1.1)
│   ├── utils/                  # Utilitários
│   │   ├── api_manager.py      # API Nitrado
│   │   ├── map_utils.py        # Mapas e localização
│   │   └── db_manager.py       # Banco de dados
│
├── config/                     # Configurações
│   └── config.py
│
├── logs/                       # Logs do servidor
│   └── log.ADM
│
├── main.py                     # Arquivo principal
├── requirements.txt            # Dependências
└── .env                        # Variáveis de ambiente
---

## 🖼️ Como Funciona

1. **Logs PvE/PvP**: Use `/logs` para ativar killfeeds e visualizar mortes com localização.
2. **Procurados**: Use `/procurados` para adicionar jogadores e monitorar eventos (v1.9).
3. **Listas**: Gerencie acesso com `/lists` e sincronize com o Nitrado.
4. **Admin**: Configure com `/admin` e crie canais padrão com dropdown (v1.1).

<p align="center">
  <img src="https://via.placeholder.com/300x150.png?text=Logs+PvE/PvP" alt="Logs PvE/PvP" width="300" style="border-radius: 5px; margin: 5px;"/>
  <img src="https://via.placeholder.com/300x150.png?text=Sistema+Procurados" alt="Sistema Procurados" width="300" style="border-radius: 5px; margin: 5px;"/>
  <img src="https://via.placeholder.com/300x150.png?text=Interface+Admin" alt="Interface Admin" width="300" style="border-radius: 5px; margin: 5px;"/>
</p>

> **Nota**: Substitua os placeholders acima por screenshots reais do bot quando disponíveis.

---

## 🤝 Contribuição

Quer colaborar? Siga os passos:

1. Faça um fork: [https://github.com/CodeProjects/Bot-Manager-DayZ](https://github.com/CodeProjects/Bot-Manager-DayZ).
2. Crie uma branch (`git checkout -b feature/nova-funcionalidade`).
3. Commit suas mudanças (`git commit -m 'Adiciona nova funcionalidade'`).
4. Push para o remoto (`git push origin feature/nova-funcionalidade`).
5. Abra um Pull Request com detalhes.

---

## 📡 Suporte e Comunidade

Junte-se ao nosso Discord para suporte, sugestões ou bate-papo!

<p align="center">
  <a href="https://discord.gg/redegamer"><img src="https://img.shields.io/badge/Discord-RedeGamer-7289DA?style=for-the-badge&logo=discord" alt="Join Discord"/></a>
</p>

---

## 📜 Licença

Licenciado sob a **MIT License**. Veja o arquivo [LICENSE](LICENSE) para detalhes.

---

<h3 align="center">🧟 Desenvolvido com ❤️ por CodeProjects</h3>
<p align="center">
  Em parceria com <a href="https://discord.gg/redegamer">RedeGamer - Serviços Escaláveis para seu Game</a><br>
  Última atualização: <strong>07/03/2025</strong> | Versão: <strong>1.1</strong>
</p>
