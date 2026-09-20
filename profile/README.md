# Real Estate VMs — Grupo 14

> Infraestrutura DevOps para pipeline de dados imobiliários, desenvolvida para a **JLeandro Imóveis**.

---

## Sobre o Projeto

A **JLeandro Imóveis** enfrenta o desafio de consolidar, processar e analisar dados de seus imóveis de forma eficiente. Este projeto propõe uma solução completa de infraestrutura como código, automatizando o ciclo de vida dos dados — da geração ao armazenamento — com foco em escalabilidade e boas práticas de engenharia.

Como os dados reais de clientes são protegidos pela **LGPD**, toda a base utilizada é **sintética**, gerada por um script próprio que simula o comportamento real do mercado imobiliário de São Paulo.

---

## Arquitetura

```
┌─────────────────┐     push CSV      ┌──────────────────────┐
│  VM: generator  │ ───────────────▶  │   GitHub Actions     │
│  Python script  │                   │   (Data Pipeline)    │
└─────────────────┘                   └──────────┬───────────┘
                                                 │
                          ┌──────────────────────┼──────────────────────┐
                          ▼                      ▼                      ▼
               ┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
               │  VM: processing │   │   VM: bigdata   │   │  VM: monitoring │
               │   R scripts     │   │   Armazenamento │   │ Grafana/Metrics │
               └─────────────────┘   └─────────────────┘   └─────────────────┘
```

| VM | Função | Tecnologia |
|----|--------|------------|
| `generator` | Gera dados sintéticos e faz push para o repositório | Python |
| `processing` | Processa e limpa os dados brutos | R |
| `bigdata` | Armazena os dados tratados | — |
| `monitoring` | Monitora a saúde da infraestrutura | Grafana + Prometheus |

---

## Stack

| Camada | Tecnologia |
|--------|------------|
| Infraestrutura como Código | OpenTofu + KVM/libvirt |
| Configuração de VMs | Ansible |
| Geração de dados | Python |
| Processamento | R |
| Pipeline CI/CD | GitHub Actions |
| Virtualização | KVM (cloud-init + Ubuntu 24.04) |

---

## Repositórios

| Repositório | Descrição |
|-------------|-----------|
| [`real-estate`](https://github.com/Real-Estate-VMs/real-estate) | Código principal — IaC, Ansible, scripts e pipeline |

---

## Equipe — Grupo 14

| Nome | RA |
|------|----|
| Enzo Dorigon Leandrini | 23000663 |
| Felipe da Fonseca Gimenes | 23000242 |
| Marcos Vinícius Carvalho da Silva | 23000327 |
| Gabriel José de Lima Carvalho | 22001435 |

---

<sub>Projeto acadêmico — dados sintéticos gerados para fins de desenvolvimento, sem uso de informações reais de clientes.</sub>
