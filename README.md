Markdown

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

O processo iniciou-se com uma tentativa de ataque padrão, que foi bloqueada pelo servidor. Isso demonstrou a existência de um mecanismo de segurança básico. Para contornar essa proteção, o ataque foi ajustado para ser mais lento e menos agressivo.

### Ataque Ajustado e Bem-Sucedido

A solução foi limitar o número de tentativas simultâneas com o parâmetro `-t 4`, evitando que o ataque fosse detectado e bloqueado.

**Comando Final Utilizado:**
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt -t 4 192.168.70.133 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed" -V
Resultado:
O ataque foi executado com sucesso, descobrindo a senha correta para o usuário admin, como evidenciado na captura de tela abaixo.

Credenciais Descobertas:

Login: admin

Senha: password

Análise de Vulnerabilidades e Medidas de Mitigação
A principal falha de segurança explorada foi o uso de uma credencial padrão extremamente fraca (admin/password), permitindo o sucesso do ataque com uma wordlist comum.

Recomendações e Medidas de Mitigação
Para proteger a aplicação contra ataques semelhantes, recomenda-se:

Política de Senhas Fortes: Exigir senhas complexas.

Bloqueio de Contas (Account Lockout): Bloquear contas após múltiplas tentativas falhas.

Rate Limiting: Limitar o número de requisições de login por IP.

Implementação de CAPTCHA: Diferenciar usuários humanos de bots.

Autenticação de Múltiplos Fatores (MFA): Adicionar uma segunda camada de verificação.

Conclusão
Este desafio demonstrou com sucesso a execução de um ataque de força bruta e a importância de ajustar a abordagem para contornar defesas simples. O resultado reforça a necessidade crítica de implementar múltiplas camadas de segurança para proteger sistemas de autenticação.
