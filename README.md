# Desafio de Segurança: Ataque de Força Bruta com Kali Linux e Hydra

Este repositório documenta a execução de um ataque de força bruta em um ambiente de laboratório controlado, como parte de um desafio de segurança da informação. O objetivo foi comprometer uma aplicação web vulnerável (DVWA) para demonstrar a eficácia de ferramentas de pentest e a importância de políticas de senhas robustas.

## Objetivos de Aprendizagem

Este projeto prático permitiu desenvolver e demonstrar as seguintes competências:

- **Compreender ataques de força bruta** em serviços web.
- **Utilizar o Kali Linux e a ferramenta Hydra** para realizar uma auditoria de segurança.
- **Documentar processos técnicos** de forma clara e estruturada.
- **Reconhecer vulnerabilidades de autenticação** e propor medidas de mitigação eficazes.
- **Utilizar o GitHub como portfólio técnico** para compartilhar evidências e documentação.

**Nota:** Embora o desafio sugerisse o uso da ferramenta Medusa, optei por utilizar o **Hydra**, que é uma ferramenta igualmente poderosa e amplamente utilizada para a mesma finalidade no ecossistema Kali Linux.

---

## Ambiente e Ferramentas Utilizadas

- **Sistema Operacional Atacante:** Kali Linux
- **Aplicação Alvo:** Damn Vulnerable Web Application (DVWA)
- **Endereço IP do Alvo:** `192.168.70.133`
- **Ferramenta de Ataque:** THC-Hydra v9.6
- **Wordlist:** `rockyou.txt` (localizada em `/usr/share/wordlists/rockyou.txt`)

---

## Etapas da Execução

O processo foi dividido em duas fases principais: a tentativa inicial de ataque e o ataque ajustado e bem-sucedido.

### 1. Primeira Tentativa e Análise do Erro

A primeira tentativa de ataque foi executada com as configurações padrão do Hydra, utilizando um número elevado de tarefas paralelas.

**Comando Inicial:**
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt 192.168.70.133 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed" -V
