<div align="center">
  <h1>🐺 UnB Comprometida — Capture The Flag</h1>
  <p><em>Um desafio de cibersegurança focado em exploração de infraestrutura acadêmica.</em></p>
</div>

---

## 📖 O Cenário

Você é um estudante membro do grupo de estudos em segurança ofensiva **UnBreakable**. Explorando a rede da universidade por pura curiosidade, você acaba esbarrando em algo inusitado: **um servidor de homologação do DETIC exposto** e acessível indevidamente. Ao reportar o achado, o professor Roberto Filho lhe confia uma missão oficial: invadir a infraestrutura e entregar um relatório técnico documentando todas as vulnerabilidades.

O servidor contém réplicas do **SIGAA** e do **Aprender 3**, rodando serviços legados, configurações inseguras e diretórios esquecidos pela equipe de TI após uma manutenção malsucedida.

**Sua missão:**
Invadir a infraestrutura, escalar privilégios até assumir o controle total (root) e coletar todas as flags que comprovam a invasão. 

---

## ✨ Por que jogar este CTF?

- 🏛️ **Imersão Total:** Explore portais que imitam os sistemas reais da UnB, com *easter-eggs* interativos.
- ⛓️ **Kill-Chain Realista:** Diferente de desafios isolados, aqui você precisará encadear técnicas: indo desde o primeiro acesso sem privilégios até a obtenção do acesso máximo ao servidor.
- 🎯 **Dificuldade Balanceada:** Desenhado para ser desafiador, porém justo. Ideal para exercitar as técnicas de exploração web e de sistemas operacionais.
- 🏆 **Múltiplos Caminhos:** Fique preso em uma vulnerabilidade e descubra que o sistema oferece rotas alternativas escondidas para continuar seu avanço!

---

## 🚩 Objetivos

O ambiente contém **5 flags obrigatórias** e **1 flag bônus** escondida para os mais curiosos. Todas estão no formato padrão: `UNB{conteudo_da_flag}`. 

Encontre todas, documente seus passos e entregue seu *write-up*!

---

## 🚀 Como subir o ambiente

O CTF é **100% offline-friendly** e roda inteiramente em containers Docker, garantindo que o laboratório não vai sujar o seu sistema operacional.

**Pré-requisitos:** Docker Engine (20.x+) e Docker Compose (v2.x+).

**1. Clone o repositório:**
```bash
git clone https://github.com/robertovrf/CTF_TAC_2026_1.git
cd CTF_TAC_2026_1/CTF_G1
```

**2. Inicie os servidores:**
```bash
docker compose up -d --build
```
> *O primeiro build pode levar alguns minutos enquanto o sistema configura a infraestrutura.*

**3. Inicie o reconhecimento!**
Com os containers rodando, o servidor web principal estará disponível na porta 80 da sua máquina local.
Comece acessando:
🔗 **http://localhost**

---
