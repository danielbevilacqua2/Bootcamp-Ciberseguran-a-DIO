

# 🛡️ Laboratório Educacional de Análise Defensiva, Integridade e Simulação Controlada em Python

Projeto prático desenvolvido para o **Bootcamp de Cibersegurança 2026 da DIO** (com base nas aulas da Profa. Dra. Isadora Ferrão), focado na compreensão defensiva de mecanismos de impacto em arquivos, captura/registro de eventos de entrada e monitoramento de integridade em ambiente isolado.

> ⚠️ **Aviso Ético e Educacional:** Todo o experimento foi conduzido exclusivamente em ambiente isolado e controlado (`lab_sandbox/`), sem execução de códigos maliciosos reais, captura de teclado externa ou exfiltração remota. O objetivo é compreender como ameaças atuam na teoria e como estruturar controles preventivos e detectivos.

---

## 🎯 Objetivos do Projeto
- Compreender o ciclo de impacto e recuperação de dados por meio de uma **transformação e restauração reversível** em arquivos fictícios dentro de um diretório isolado.
- Simular de forma segura e reproduzível o **registro formatado de eventos de entrada** (tratamento de teclas especiais como `Espaço`, `Enter` e `Tab`, exclusão de teclas modificadoras e codificação UTF-8).
- Implementar **monitoramento de integridade de arquivos (FIM)** usando hashes **SHA-256** para detectar alterações não autorizadas (`ALTERADO`) e validar a recuperação completa (`INTEGRO`).
- Consolidar evidências tabulares e visuais com `pandas` e `matplotlib`, além de documentar medidas de prevenção contra engenharia social e malwares.

---

## 🧪 Cenários Simulados e Resultados Observados

### 1. Ambiente Isolado e Transformação / Restauração Reversível
Em um diretório isolado (`lab_sandbox/test_files/`), foram criados três arquivos fictícios (`credenciais_ficticias.txt`, `notas_estudo.txt` e `relatorio_financeiro_demo.txt`), com registro de *baseline* em hash SHA-256 e proteção de caminho para impedir operações fora da pasta de testes.

- **Detecção intermediária de alteração:** ao aplicar a transformação reversível antes da restauração, a verificação de integridade apontou status `ALTERADO` com alerta de divergência de hash SHA-256 nos três arquivos (ex.: `credenciais_ficticias.txt` passando de 100 bytes para 228 bytes durante a transformação).
- **Restauração e validação:** após reverter a transformação com a chave do laboratório, a checagem confirmou retorno ao status `INTEGRO` (`NENHUM` alerta) e recuperação exata dos hashes iniciais.

### 2. Registro Simulado de Eventos de Entrada
Foi simulado o processamento de eventos de entrada em ambiente controlado (`eventos_simulados.log`), demonstrando como sequências de teclas podem ser convertidas em texto legível se não houver controle de execução de scripts e monitoramento de processos/arquivos.

### 3. Evidência Visual (Gráfico de Integridade e Tamanho)
Salve o arquivo `resumo_integridade.png` (gerado na etapa de visualização) na pasta `images/` do repositório para exibir o gráfico abaixo:

![Análise Defensiva — Integridade e Tamanho dos Arquivos em Sandbox](images/resumo_integridade.png)

---

## 🧠 Reflexão Pessoal: Engenharia Social e Defesa na Prática
Na prática, a maioria dos incidentes envolvendo malwares como ransomware ou keyloggers começa muito antes da exploração técnica — geralmente por **engenharia social** (mensagens urgentes, falsas notificações, anexos disfarçados ou links maliciosos que induzem o usuário a executar um arquivo ou inserir credenciais).

Para mim, o principal aprendizado deste laboratório é que **a tecnologia defensiva precisa trabalhar em camadas junto com o comportamento humano**:
- Mesmo que um sistema tenha ferramentas de detecção, um clique descuidado pode iniciar a cadeia de infecção.
- Por outro lado, **sandboxing**, **backups/restauração testada**, **monitoramento de integridade** e **autenticação multifator (MFA)** reduzem drasticamente o impacto caso uma falha humana aconteça.

---

## 🛡️ Medidas de Prevenção e Defesa
- **Autenticação Multifator (MFA):** dificulta o uso indevido de credenciais mesmo em casos de vazamento ou captura indevida.
- **Sandboxing e Privilégio Mínimo:** isola experimentos e restringe permissões de escrita/execução apenas ao necessário.
- **Antivírus / EDR:** identifica comportamentos suspeitos, alterações em lote de arquivos e processos não autorizados.
- **Firewall e Controle de Rede:** restringe comunicações de saída indevidas e reduz a superfície de ataque.
- **Conscientização e Verificação:** desconfiar de urgência incomum, validar solicitações por canal oficial e nunca executar scripts ou anexos de origem duvidosa.

---

## 🧰 Ferramentas e Tecnologias
- **Ambiente:** [Google Colab](https://colab.research.google.com/) e [GitHub](https://github.com/)
- **Linguagem e Bibliotecas:** Python 3, `cryptography` (`Fernet`), `hashlib`, `pathlib`, `pandas` e `matplotlib`

---

## 🗂️ Estrutura Sugerida do Repositório
```text
Bootcamp-Ciberseguran-a-DIO/
├── README.md                  # Documentação técnica e reflexões do projeto
├── notebook_laboratorio.ipynb # Notebook modular executado no Google Colab
└── images/
    └── resumo_integridade.png # Gráfico gerado na análise defensiva
