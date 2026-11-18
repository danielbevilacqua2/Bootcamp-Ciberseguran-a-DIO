# 🛡️ Simulando Ataques de Brute Force e Defesas Ativas (Medusa & Python no Google Colab)

Projeto prático desenvolvido para o **Bootcamp de Cibersegurança 2026 da DIO** (inspirado nas aulas da Profa. Dra. Isadora Ferrão).

> ⚠️ **Disclaimer Ético:** Todos os experimentos documentados neste repositório foram executados em ambiente de laboratório 100% isolado e controlado, com finalidade estritamente educacional e defensiva.

---

## 🎯 Objetivos do Projeto
- Compreender as diferenças arquiteturais entre autenticações **Stateless**, **Stateful** e **Federada (OAuth 2.0 / SAML)**.
- Analisar e comparar o ecossistema de ferramentas de auditoria de senhas do Kali Linux (**Medusa, Hydra, Ncrack, John the Ripper, WPScan e Patator**).
- Simular ataques de **Força Bruta em FTP**, **Automação de Formulário Web (DVWA)** e **Ataque em Cadeia (Enumeração SMB + Password Spraying)**.
- Implementar controles defensivos práticos (**Account Lockout / Rate Limiting** e auditoria de logs) demonstrando como neutralizar ofensivas automatizadas.

---

## 🧰 Ferramentas e Tecnologias Utilizadas
- **Ambiente de Execução:** Google Colab (Container Linux Ubuntu) & Kali Linux / Metasploitable 2
- **Linguagem e Bibliotecas:** Python 3 (`requests`, `concurrent.futures`, `http.server`, `pandas`, `matplotlib`)
- **Utilitários de Referência:** Medusa, Nmap, SMBClient
- **Copiloto de Arquitetura e Código:** Google Gemini

---

## 🗂️ Estrutura do Repositório
```text
├── Purple_Team_Lab_no_Google_Colab_Simulação_de_Ataques_de_Força_Bruta,_Password_Spraying_e_Motor_Defensivo_de_Detecção_(IDS_Rate_Limiting).ipynb  # Notebook executável completo
├── wordlists/
│   ├── users.txt                                   # Lista de usuários auditados
│   └── pass.txt                                    # Dicionário de senhas comuns
├── images/                                         # Evidências de execução e gráficos Blue Team
└── README.md                                       # Documentação técnica do projeto
