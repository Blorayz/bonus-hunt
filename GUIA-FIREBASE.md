# 🔥 GUIA COMPLETO - FIREBASE BONUS HUNT

## 📋 PASSO A PASSO COMPLETO

---

## 1️⃣ CRIAR PROJETO NO FIREBASE

### **A. Acessa o Firebase Console**
1. Vai para: https://console.firebase.google.com/
2. Faz login com tua conta Google
3. Clica em **"Adicionar projeto"** ou **"Add project"**

### **B. Configura o Projeto**
1. **Nome do projeto:** `bonus-hunt` (ou o nome que quiseres)
2. **Google Analytics:** Podes desativar (não é necessário)
3. Clica em **"Criar projeto"**
4. Aguarda alguns segundos...
5. Clica em **"Continuar"**

---

## 2️⃣ ATIVAR REALTIME DATABASE

### **A. Acessa o Database**
1. No menu lateral esquerdo, clica em **"Build"** → **"Realtime Database"**
2. Clica em **"Create Database"** ou **"Criar banco de dados"**

### **B. Escolhe a Localização**
1. Seleciona a região mais próxima (ex: `europe-west1`)
2. Clica em **"Next"** ou **"Próximo"**

### **C. Configurar Regras de Segurança**
1. Seleciona **"Start in test mode"** (Modo de teste)
2. Clica em **"Enable"** ou **"Ativar"**

⚠️ **IMPORTANTE:** Depois vamos ajustar as regras!

---

## 3️⃣ CONFIGURAR REGRAS DE SEGURANÇA

### **A. Acessa as Regras**
1. No Realtime Database, clica na aba **"Rules"** ou **"Regras"**
2. Vais ver algo assim:
```json
{
  "rules": {
    ".read": "now < 1234567890000",
    ".write": "now < 1234567890000"
  }
}
```

### **B. Substitui pelas Regras Abertas**
**Cola isto:**
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

3. Clica em **"Publish"** ou **"Publicar"**

⚠️ **NOTA:** Estas regras permitem que qualquer pessoa leia/escreva. Para produção, deves proteger melhor!

---

## 4️⃣ OBTER CONFIGURAÇÃO DO FIREBASE

### **A. Acessa as Configurações**
1. Clica no ícone da **engrenagem** ⚙️ no topo (ao lado de "Project Overview")
2. Clica em **"Project settings"** ou **"Configurações do projeto"**

### **B. Adiciona uma Web App**
1. Scroll para baixo até **"Your apps"** ou **"Seus aplicativos"**
2. Clica no ícone **</>** (Web)
3. **Nickname:** `bonus-hunt-web`
4. **NÃO** marques "Firebase Hosting"
5. Clica em **"Register app"** ou **"Registrar app"**

### **C. Copia a Configuração**
Vais ver um código assim:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyC1234567890abcdefghijk",
  authDomain: "bonus-hunt-12345.firebaseapp.com",
  databaseURL: "https://bonus-hunt-12345-default-rtdb.europe-west1.firebasedatabase.app",
  projectId: "bonus-hunt-12345",
  storageBucket: "bonus-hunt-12345.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef1234567890"
};
```

**COPIA ESTE CÓDIGO TODO!** 📋

---

## 5️⃣ CONFIGURAR OS FICHEIROS HTML

### **A. Painel (painel-firebase.html)**

1. Abre o ficheiro `painel-firebase.html` num editor de texto
2. Procura por esta parte (linha ~450):

```javascript
const firebaseConfig = {
    apiKey: "SUA_API_KEY_AQUI",
    authDomain: "seu-projeto.firebaseapp.com",
    databaseURL: "https://seu-projeto-default-rtdb.firebaseio.com",
    projectId: "seu-projeto",
    storageBucket: "seu-projeto.appspot.com",
    messagingSenderId: "123456789",
    appId: "1:123456789:web:abcdef123456"
};
```

3. **SUBSTITUI** pela configuração que copiaste do Firebase
4. **SALVA** o ficheiro

### **B. Overlay (overlay-firebase.html)**

1. Abre o ficheiro `overlay-firebase.html`
2. Procura a mesma parte `firebaseConfig`
3. **COLA A MESMA CONFIGURAÇÃO** que usaste no painel
4. **SALVA** o ficheiro

⚠️ **IMPORTANTE:** A configuração deve ser **EXATAMENTE IGUAL** nos dois ficheiros!

---

## 6️⃣ HOSPEDAR NO NETLIFY

### **A. Prepara os Ficheiros**
Tens 3 ficheiros:
- `index.html` (página inicial)
- `painel-firebase.html` (painel de controlo)
- `overlay-firebase.html` (overlay para OBS)

### **B. Upload no Netlify**
1. Vai para https://app.netlify.com/drop
2. Cria uma **pasta** no teu PC
3. Coloca os **3 ficheiros** dentro da pasta
4. **Arrasta a pasta** para o Netlify Drop
5. Aguarda o deploy (30 segundos)

### **C. Obtém o URL**
O Netlify vai dar um URL tipo:
```
https://bonus-hunt-abc123.netlify.app
```

---

## 7️⃣ TESTAR TUDO

### **A. Testa o Painel**
1. Abre: `https://teu-site.netlify.app/painel-firebase.html`
2. Verifica se aparece **"Conectado"** no canto superior direito
3. Se aparecer o aviso amarelo, é porque não configuraste o Firebase ainda

### **B. Adiciona um Slot de Teste**
1. Define um Start (ex: 100.00)
2. Procura um slot (ex: "Gates of Olympus")
3. Seleciona da lista
4. Coloca uma aposta (ex: 0.40)
5. Clica em "Adicionar Slot"

### **C. Verifica no Firebase**
1. Volta ao Firebase Console
2. Vai em Realtime Database
3. Deves ver os dados aparecerem em tempo real! 🎉

### **D. Testa o Overlay**
1. Abre: `https://teu-site.netlify.app/overlay-firebase.html`
2. O slot que adicionaste deve aparecer automaticamente!
3. Se aparecer, **ESTÁ A FUNCIONAR!** ✅

---

## 8️⃣ ADICIONAR NO OBS

### **A. Cria Fonte Browser**
1. No OBS, clica em **"+"** em Sources/Fontes
2. Escolhe **"Browser"**
3. Nome: **"Bonus Hunt Overlay"**

### **B. Configurações**
```
URL: https://teu-site.netlify.app/overlay-firebase.html
Largura: 1920
Altura: 1080
FPS: 30
```

### **C. Opções Importantes**
- ✅ **Shutdown source when not visible**
- ✅ **Refresh browser when scene becomes active**

### **D. Ajusta a Posição**
1. Move e redimensiona como quiseres
2. O overlay tem fundo transparente
3. Fica por cima da stream

---

## 9️⃣ USAR O SISTEMA

### **No Painel (navegador):**
1. Define o Start da hunt
2. Adiciona slots conforme vais comprando bónus
3. Quando abrires um bónus, clica em "Abrir" e coloca o valor ganho
4. As estatísticas atualizam automaticamente

### **No OBS (overlay):**
- Atualiza automaticamente em tempo real (1-2 segundos)
- Mostra todos os slots
- Barra de progresso
- Estatísticas ao vivo
- Auto-scroll suave nos slots

---

## 🔧 RESOLUÇÃO DE PROBLEMAS

### **"Desconectado" no painel?**
✅ Verifica se colocaste a configuração do Firebase corretamente
✅ Verifica se o `databaseURL` está correto
✅ Verifica se as regras do Database estão em modo aberto

### **Overlay não atualiza?**
✅ Verifica se a configuração do Firebase é igual no painel e overlay
✅ Recarrega a fonte do OBS (clique direito → Refresh)
✅ Verifica se adicionaste slots no painel primeiro

### **Dados não aparecem no Firebase Console?**
✅ Verifica se salvaste os ficheiros depois de colar a configuração
✅ Limpa cache do navegador (Ctrl+F5)
✅ Verifica se as regras do Database permitem escrita

### **Erro "Firebase not defined"?**
✅ Verifica ligação à internet
✅ Os scripts do Firebase estão a carregar do CDN
✅ Aguarda alguns segundos para o Firebase inicializar

---

## 💡 DICAS

### **Para Streamers:**
- Mantém o painel aberto num monitor/tablet separado
- Adiciona slots durante a stream
- O overlay atualiza sozinho no OBS
- Espectadores veem tudo em tempo real!

### **Personalização:**
- Podes mudar as cores no CSS
- Ajustar velocidade do auto-scroll
- Personalizar layout do overlay

### **Backup:**
- Usa a função "Exportar" para fazer backup dos dados
- Guarda o ficheiro JSON em segurança
- Podes importar depois se precisares

---

## 📊 ESTRUTURA DE DADOS NO FIREBASE

Assim ficam os dados salvos:

```
bonus-hunt/
  ├── slots/
  │   ├── 0/
  │   │   ├── id: 1234567890
  │   │   ├── slotName: "Gates of Olympus"
  │   │   ├── provider: "Pragmatic Play"
  │   │   ├── imageUrl: "https://..."
  │   │   ├── betAmount: 0.40
  │   │   ├── opened: false
  │   │   └── winAmount: 0
  │   └── 1/
  │       └── ...
  └── stats/
      ├── start: 100.00
      ├── multiplier: 250.00
      ├── average: 50.00
      ├── breakEven: 100.00
      ├── profitLoss: 25.50
      └── huntNumber: 1
```

---

## 🔒 SEGURANÇA (OPCIONAL)

Para proteger melhor os dados, podes usar estas regras no Firebase:

```json
{
  "rules": {
    "bonus-hunt": {
      ".read": true,
      ".write": "auth != null"
    }
  }
}
```

Mas isto requer autenticação. Para uso pessoal, as regras abertas são OK.

---

## ✅ CHECKLIST FINAL

Antes de começar a usar:

- [ ] Projeto Firebase criado
- [ ] Realtime Database ativado
- [ ] Regras configuradas (leitura e escrita abertas)
- [ ] Configuração do Firebase copiada
- [ ] Configuração colada nos 2 ficheiros (painel e overlay)
- [ ] Ficheiros salvos
- [ ] Upload no Netlify feito
- [ ] Painel testado e a conectar
- [ ] Overlay testado e a atualizar
- [ ] Overlay adicionado no OBS
- [ ] Tudo a funcionar! 🎉

---

## 🆘 SUPORTE

Se algo não funcionar:

1. **Verifica o console do navegador** (F12 → Console)
2. **Procura por erros** vermelhos
3. **Verifica** se a configuração do Firebase está correta
4. **Testa** primeiro só o painel, depois o overlay

---

**Boa sorte com as tuas bonus hunts!** 🎰🍀

**Se tudo funcionar, vais ter:**
- ✅ Painel online sempre disponível
- ✅ Overlay sincronizado em tempo real
- ✅ Dados salvos na cloud
- ✅ Acesso de qualquer lugar
- ✅ Stream profissional com estatísticas ao vivo!
