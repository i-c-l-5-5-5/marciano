# ☁️ Modelos Gratuitos na Nuvem

Rodam nos servidores do Google/Groq — não pesam nada no seu PC.

---

## Gemini (Google)

### Criar chave gratuita

1. Acesse [aistudio.google.com](https://aistudio.google.com)
2. Faça login com sua conta Google
3. Clique em **"Get API Key"** → **"Create API key"**
4. Copie a chave gerada

### Configurar

```bash
echo 'export GEMINI_API_KEY=sua_chave_aqui' >> ~/.bashrc
source ~/.bashrc
```

### Usar com Aider

```bash
# Gemini 2.5 Flash (mais rápido, 1000 req/dia grátis)
aider --model gemini/gemini-2.5-flash

# Gemini 2.5 Pro (melhor qualidade, 25 req/dia grátis)
aider --model gemini/gemini-2.5-pro
```

---

## Groq

### Criar chave gratuita

1. Acesse [console.groq.com](https://console.groq.com)
2. Faça login com Google
3. Vá em **API Keys → Create API Key**
4. Copie a chave gerada

### Configurar

```bash
echo 'export GROQ_API_KEY=sua_chave_aqui' >> ~/.bashrc
source ~/.bashrc
```

### Usar com Aider

```bash
aider --model groq/llama-3.3-70b-versatile
```

### Verificar se a chave está configurada

```bash
echo $GROQ_API_KEY
```

---

## Comparativo

| Modelo | Velocidade | Qualidade | Limite grátis |
|---|---|---|---|
| Gemini 2.5 Flash | ⚡ Rápido | ★★★★ | 1000 req/dia |
| Groq Llama 3.3 70b | ⚡⚡ Muito rápido | ★★★★ | 14.400 req/dia |
| Gemini 2.5 Pro | Médio | ★★★★★ | 25 req/dia |

**Recomendação para uso diário:** Groq (mais rápido e maior limite gratuito)

---

## ⚠️ Segurança

Nunca exponha sua API Key publicamente (no terminal, commits, chats, etc).

Se isso acontecer, acesse imediatamente o console do provedor, **delete a chave comprometida** e crie uma nova.
