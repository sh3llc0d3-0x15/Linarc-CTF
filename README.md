
# LINARC CTF — Credenciais Expostas

<div align="center">

**LINARC CTF** · Web · Very Easy

*Write-up por [sh3llc0d3](https://github.com/sh3llc0d3-0x15)*
*Discord Server: https://discord.gg/linarc*

</div>

---

## 📌 Visão Geral

| Campo | Detalhes |
|---|---|
| **Plataforma** | LINARC CTF |
| **Categoria** | Web |
| **Dificuldade** | Very Easy |
| **Vulnerabilidade** | Exposição de credenciais |
| **Autor do Write-up** | [sh3llc0d3](https://github.com/sh3llc0d3-0x15) |

## 1. Reconhecimento

Começamos baixando os arquivos públicos do site para analisar sua estrutura.

```bash
wget -r -np -k https://linarcctf.vercel.app/
```

Listamos os arquivos baixados:

```bash
ls
```

## 2. Análise dos Arquivos

Primeiro, analisamos o código HTML da página principal:

```bash
cat index.html
```

Durante a análise, identificamos uma referência ao arquivo `app.js`.

Em seguida, examinamos o JavaScript:

```bash
cat app.js
```

O código revelou uma referência ao endpoint `/backend`, indicando o próximo ponto a investigar.

## 3. Análise do Endpoint

Consultamos o endpoint identificado:

```bash
curl https://linarcctf.vercel.app/backend
```

A resposta observada no desafio continha credenciais de acesso.

> **Observação:** publique apenas credenciais fictícias do laboratório. Não inclua segredos reais ou ainda válidos.

## 4. Acesso

Com as credenciais fornecidas pelo desafio, o próximo passo era testar o acesso à área restrita e concluir o objetivo proposto.

## 5. Vulnerabilidade Identificada

**Exposição de informações sensíveis — Information Disclosure**

O endpoint disponibilizava informações de autenticação sem a proteção adequada, permitindo que visitantes obtivessem credenciais que deveriam permanecer privadas.

### Impacto

- Acesso não autorizado à área restrita, caso as credenciais fossem válidas.
- Possível comprometimento de contas e funcionalidades protegidas.
- Exposição de informações que deveriam ser acessíveis somente a usuários autorizados.

## 6. Mitigação

- Nunca disponibilize credenciais em código público ou respostas de endpoints sem autenticação.
- Implemente autenticação e autorização no backend.
- Remova segredos do frontend e armazene-os de forma segura.
- Revogue credenciais que tenham sido expostas.

---

<div align="center">

**LINARC CTF — Write-up**

Autoria: [sh3llc0d3](https://github.com/sh3llc0d3-0x15)

</div>
