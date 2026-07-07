# 🎓 UnB Comprometida — CTF

> **Capture The Flag** desenvolvido como trabalho final da disciplina **Tópicos Avançados em Computadores** — Universidade de Brasília (UnB)

---

## 📖 Sobre o Desafio

Você é um aluno membro do grupo de estudos **UnBreakable** e, durante análises rotineiras, deparou-se com sistemas de homologação da UnB acessíveis na rede interna — e aparentemente com várias portas e serviços vulneráveis expostos.

Sua missão é realizar uma simulação de pentest completo: explorar o ambiente, encontrar as falhas, capturar as flags que comprovam a exploração de cada etapa e, ao final, ter o caminho documentado para reportar as vulnerabilidades à universidade. O caminho vai exigir reconhecimento, análise cuidadosa e encadeamento de técnicas — nada aqui é sorte.

> ⚠️ **Spoiler-free zone.** O README não revela vulnerabilidades, flags ou dicas de exploração. Descubra você mesmo.

**Dificuldade estimada:** Intermediária  
**Flags no total:** 5 (+ 1 bônus)  
**Técnicas abordadas:** Enumeração de serviços, SQL Injection, LFI (Local File Inclusion), quebra de hashes (MD5Crypt/apr1), movimentação lateral entre usuários e escalação de privilégios via PATH Hijacking (SUID) e sudo misconfiguration (GTFOBins)

---

## ⚙️ Pré-requisitos

Antes de começar, certifique-se de ter instalado:

```bash
docker --version       # Docker Engine 20.x ou superior
docker compose version # Docker Compose v2.x ou superior
```

> O CTF roda inteiramente em containers Docker, é **100% offline-friendly** (fontes e recursos externos foram localizados para evitar carregamento infinito em redes isoladas) e não exige internet ativa.

---

## 🚀 Subindo o Ambiente

**1. Clone o repositório:**

```bash
git clone https://github.com/Mateusrb6/Trabalho-Final-TAC.git
cd Trabalho-Final-TAC
```

**2. Suba os containers:**

```bash
docker compose up -d --build
```

O primeiro build pode levar alguns minutos — o Docker vai baixar as imagens base e configurar todos os serviços.

**3. Aguarde a inicialização completa:**

```bash
docker compose logs -f
```

Quando os logs pararem de rolar e você ver os serviços confirmando que estão prontos, o ambiente está acessível.

**4. Verifique se tudo está rodando:**

```bash
docker compose ps
```

Ambos os containers devem estar com status `running`.

---

## 🌐 Portas Disponíveis

| Serviço | Porta no Host | Protocolo |
|---------|--------------|-----------|
| Servidor Web | `80` | HTTP |
| SSH | `2222` | SSH |
| FTP | `21` | FTP |
| FTP Passivo | `21100–21110` | FTP (dados) |

> **Ponto de entrada sugerido:** comece pelo servidor web em `http://localhost` — e não esqueça de fazer uma boa enumeração antes de sair testando coisas.

---

## 🏁 Formato das Flags

As flags seguem o padrão:

```
UNB{conteudo_da_flag}
```

Quando encontrar uma, anote — você vai precisar de todas ao final.

## 🛑 Encerrando o Ambiente

```bash
# Para os containers sem remover os dados
docker compose down

# Para os containers e remove tudo (use se quiser recomeçar do zero)
docker compose down --volumes --rmi local
```

---

## 🔧 Troubleshooting

**Conflito de portas (porta 21, 80 ou 2222 já em uso):**

```bash
# Identifique o processo usando a porta
sudo ss -tlnp | grep :21
sudo ss -tlnp | grep :80
sudo ss -tlnp | grep :2222

# Encerre o processo conflitante ou altere as portas no docker-compose.yml
```

**FTP em modo passivo com cliente externo:**  
Se estiver testando FTP de outra máquina na rede (não `localhost`), edite o `unb-ftp/vsftpd.conf` e substitua `pasv_address=0.0.0.0` pelo IP real da máquina host antes de fazer o build.

**Container travado na inicialização:**

```bash
docker compose logs unb-web
docker compose logs unb-ftp
```

---

## 👨‍💻 Autores

| Autor | GitHub |
|-------|--------|
| Mateus Reis | [@Mateusrb6](https://github.com/Mateusrb6) |
| Alberto Cortes | [@oalbertocavalcante](https://github.com/oalbertocavalcante) |

---

*Desenvolvido para a disciplina Tópicos Avançados em Computadores — UnB, 2026/1*
