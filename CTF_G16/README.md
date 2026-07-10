Autor: Rodrigo Fonseca

# DesAprender3 
## 1. Contextualização (a história)

Faltam poucos dias para o fim do semestre e **João Vitor**, aluno de **CIC1337 – Tópicos
Avançados em Computadores**, descobriu que está **Reprovado**. O professor da disciplina,
**Robert Son**, é old-school: ainda usa o **DesAprender3**, o Ambiente Virtual de
(Des)Aprendizagem da universidade — um Moodle antigo, mal configurado e cheio de atalhos
perigosos do "CEAD/TI".

João decide que não vai repetir a matéria. Munido apenas das **próprias credenciais de aluno**,
ele vai enumerar o AVA, abusar de falhas de controle de acesso para mexer na própria nota,
roubar a conta do professor, conseguir execução de código no servidor e, no fim, **virar root**
na máquina que hospeda o AVA.

O objetivo do desafio é reproduzir essa invasão capturando as **duas flags obrigatórias**.

## 2. Briefing do atacante (ponto de partida — *assumed breach*)

Você é o João. Suas credenciais de aluno do DesAprender3:

```
CPF (login): 05544433322
Senha:       joao123
```

Alvo: **http://localhost:8080** (web). Boa caçada.

## 4. Como executar o ambiente

**Pré-requisito:** Docker + Docker Compose.

```bash
# na raiz do projeto (onde está o docker-compose.yml)
docker compose up --build -d
```

- AVA web: **http://localhost:8080**
- Banco MariaDB: interno (serviço `db`, não exposto ao host)

Parar e limpar tudo (inclui volume do banco):

```bash
docker compose down -v
```

> **Conflito de porta:** se a `8080` já estiver em uso no host, troque o mapeamento em
> `docker-compose.yml` (ex.: `"8088:80"`) e acesse `http://localhost:8088`.
