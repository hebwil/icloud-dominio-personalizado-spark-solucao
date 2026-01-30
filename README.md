## TL;DR

Se você usa **iCloud Mail com domínio personalizado** no **Spark**  
e a conta **não autentica / não envia**, use:

- **E-mail:** alias do domínio (ex: `vendas@seudominio.com`)
- **Usuário IMAP/SMTP:** Apple ID raiz (`@me.com`, `@icloud.com`)
- **Senha:** senha específica de aplicativo

👉 Alias **NÃO** funciona como login.


===================================================================================================



# icloud-dominio-personalizado-spark-solucao
icloud-dominio-personalizado-spark-solucao


# iCloud Mail + Domínio Personalizado + Spark (Workaround Funcional)

## Contexto

Ao usar **Domínio de E-mail Personalizado do iCloud** com clientes IMAP
(como Spark Mail), a configuração frequentemente falha quando o alias
do domínio é usado como usuário de autenticação.

Esse comportamento **não é claramente documentado pela Apple**.

Após análise de múltiplos relatos em fóruns técnicos, foi identificado
um padrão funcional.

---

## ❌ Problema Comum

Ao tentar configurar a conta usando:

- E-mail: `sales@example.com`
- Usuário IMAP/SMTP: `sales@example.com`

O Spark pode:
- falhar na autenticação
- não permitir envio
- não exibir corretamente o remetente

---

## ✅ Solução (Workaround Confirmado)

A autenticação **DEVE** ser feita com o **Apple ID raiz**
(`@me.com`, `@icloud.com` ou `@mac.com`), mesmo que o e-mail exibido
seja o do domínio personalizado.

### Regra de Ouro
> **Alias ≠ Credencial de login**

---

## 🔧 Configuração Correta (IMAP / SMTP)

### IMAP (Entrada)
- Servidor: `imap.mail.me.com`
- Porta: `993`
- Segurança: `SSL`
- **Usuário:** `user@me.com`
- Senha: **Senha específica de aplicativo**

### SMTP (Saída)
- Servidor: `smtp.mail.me.com`
- Porta: `587`
- Segurança: `STARTTLS`
- **Usuário:** `user@me.com`
- Senha: **Senha específica de aplicativo**

### No cliente de e-mail (ex: Spark)
- **Campo E-mail:** `sales@example.com`
- **Campo Usuário:** `user@me.com`

---

## 🔐 Observação sobre Senha
É obrigatório usar **senha específica de aplicativo**, gerada em:

https://appleid.apple.com  
→ Início de sessão e segurança  
→ Senhas específicas de aplicativo

---

## 🧠 Por que isso funciona?

Os servidores IMAP/SMTP da Apple validam apenas o **Apple ID raiz**.
Aliases de domínio funcionam apenas como **identidade de envio**,
não como credencial de autenticação.

---

## 📚 Referências
Relatos semelhantes encontrados em:
- Reddit (`r/SparkMail`, `r/iCloud`)
- Apple Support Communities

---

## ⚠️ Aviso
Este comportamento pode mudar no futuro.
Atualmente, este é o método mais confiável relatado pela comunidade.












==============================================================================================


---

# iCloud Mail + Custom Domain + Spark  
## Working IMAP / SMTP Workaround

## Context

When using **iCloud Custom Email Domain** with IMAP clients
(such as **Spark Mail**), the setup often fails if the
**custom domain alias** is used as the authentication username.

This behavior is **not clearly documented by Apple**.

After analyzing multiple reports across technical forums and communities,
a **reliable working pattern** was identified.

---

## ❌ Common Issue

When configuring the account using:

- **Email:** `sales@example.com`
- **IMAP/SMTP Username:** `sales@example.com`

Spark may exhibit:

- authentication failures  
- inability to send messages  
- incorrect sender display  

---

## ✅ Solution (Confirmed Workaround)

Authentication **MUST** be performed using the **root Apple ID**
(`@me.com`, `@icloud.com`, or `@mac.com`), even though the
**email address itself is a custom domain alias**.

### Golden Rule
> **Alias ≠ Login credential**

---

## 🔧 Correct Configuration (IMAP / SMTP)

### IMAP (Incoming)
- **Server:** `imap.mail.me.com`
- **Port:** `993`
- **Security:** `SSL`
- **Username:** `user@me.com`
- **Password:** app-specific password

### SMTP (Outgoing)
- **Server:** `smtp.mail.me.com`
- **Port:** `587`
- **Security:** `STARTTLS`
- **Username:** `user@me.com`
- **Password:** app-specific password

### In the email client (e.g. Spark)
- **Email field:** `sales@example.com`
- **Username field:** `user@me.com`

---

## 🔐 App-Specific Password Requirement

An **app-specific password** is mandatory and must be generated at:

https://appleid.apple.com  
→ **Sign-In and Security**  
→ **App-Specific Passwords**

---

## 🧠 Why This Works

Apple’s IMAP/SMTP servers authenticate **only the root Apple ID**.
Custom domain aliases function strictly as **sending identities**,
not as authentication credentials.

---

## 📚 References

Similar behavior reported across:

- Reddit (`r/SparkMail`, `r/iCloud`)
- Apple Support Communities

---

Add TL;DR with working configuration summary

---

## ⚠️ Disclaimer

This behavior may change in the future.
At the time of writing, this is the **most reliable and consistent**
method reported by the community.

