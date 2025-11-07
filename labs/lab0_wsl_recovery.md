# 🧩 Lab 0 – WSL Recovery & Linux Setup

## 🎯 Objetivo
Documentar o processo de diagnóstico e recuperação de uma instalação **Ubuntu corrompida no WSL (Windows Subsystem for Linux)**, garantindo que o ambiente Linux está funcional e preparado para futuros labs.

---

## 🧠 Contexto
Durante a configuração inicial do ambiente de estudos, o sistema apresentava:
- **Baixa memória RAM** e lentidão;
- O **Ubuntu no WSL** não iniciava corretamente (“Launching…” indefinidamente);
- Necessidade de reinstalar e corrigir o ambiente para retomar os exercícios.

Após pesquisa, decidi **utilizar o WSL** e efetuar uma reinstalação limpa, garantindo que o sistema ficava estável.

---

## 🧩 Etapas Executadas

### 1️⃣ Verificar distribuições instaladas
No PowerShell (executar como Administrador):
```powershell
wsl --list --verbose
```
**Resultado esperado:** lista de distribuições e versões (WSL 1 ou 2).

---

### 2️⃣ Remover versões corrompidas
```powershell
wsl --unregister Ubuntu
```
**Explicação:** remove instâncias corrompidas ou com falhas.  
⚠️ Atenção: isto apaga ficheiros dessa instalação.

---

### 3️⃣ Atualizar e configurar WSL2
```powershell
wsl --update
wsl --set-default-version 2
wsl --status
```
**Objetivo:** garantir que o WSL2 está ativo e atualizado.

---

### 4️⃣ Reinstalar Ubuntu
**Opção recomendada (Microsoft Store):**
- Pesquisar “Ubuntu 22.04 LTS” → Instalar → Abrir.

**Ou via PowerShell:**
```powershell
wsl --install -d Ubuntu-22.04
```

---

### 5️⃣ Configurar e atualizar Ubuntu
No terminal Ubuntu recém-instalado:
```bash
sudo apt update && sudo apt upgrade -y
```

Verificar informações básicas:
```bash
lsb_release -a
whoami
pwd
df -h
free -h
```
**Resultado esperado:**  
- Versão `Ubuntu 22.04` (ou similar);  
- Utilizador criado corretamente;  
- Disco e memória visíveis e funcionais.

---

### 6️⃣ Testar ambiente básico
```bash
mkdir -p ~/lab0_test
echo "Lab 0 OK" > ~/lab0_test/test.txt
cat ~/lab0_test/test.txt
```
**Resultado:** deve mostrar “Lab 0 OK”.

---

### 7️⃣ Testes adicionais
Verificar processos:
```bash
ps aux | head
top -b -n 1 | head -n 15
```

Corrigir pacotes (se necessário):
```bash
sudo apt --fix-broken install
sudo dpkg --configure -a
```

---

## ✅ Resultados
- Ubuntu reinstalado com sucesso no WSL2.  
- Sistema atualizado (`sudo apt update && sudo apt upgrade` sem erros).  
- Ambiente funcional e pronto para novos labs.  
- Ficheiros criados e comandos básicos testados com sucesso.

---

## 💡 Lições Aprendidas
- O WSL é uma ferramenta essencial para desenvolvimento Linux no Windows.  
- Corrupções podem ocorrer com pouca RAM, mas reinstalar é rápido com `wsl --unregister`.  
- Documentar o processo facilita a repetição e evita erros futuros.  
- A partir daqui, é possível iniciar os **Labs de Linux Commands**.

---

## 🧾 Checklist Final
| Verificação | Resultado |
|--------------|------------|
| WSL atualizado | ✅ |
| Ubuntu reinstalado | ✅ |
| Acesso ao terminal funcional | ✅ |
| Atualização `apt` sem erros | ✅ |
| Teste `echo` / `cat` OK | ✅ |
| Preparado para próximos labs | ✅ |

---

## 🗂️ Referências
- [Documentação oficial do WSL – Microsoft](https://learn.microsoft.com/windows/wsl)
- [Ubuntu WSL no Microsoft Store](https://apps.microsoft.com/detail/ubuntu-22-04-lts/9PN20MSR04DW)

---

📅 **Data de execução:** novembro 2025  
👤 **Autor:** Márcio Santos  
📘 **Lab:** 0 — WSL Recovery & Linux Setup  

