---

# PrimeOps Lab: Um Ecossistema de Cloud Híbrida, Segurança e DevSecOps

<p align="center">
  <img src="https://github.com/AndreGoncallez/PrimeOps-Lab/blob/main/PrimeOpsLogo.jpeg" alt="PrimeOps Lab Logo" width="350"/>
</p>

<p align="center">
  <strong>Um laboratório de nível empresarial para simulação, automação e defesa de infraestruturas modernas.</strong>
</p>

<p align="center">
  <a href="#-arquitetura-do-ecossistema">Arquitetura</a> •
  <a href="#-pilares-tecnológicos">Tecnologias</a> •
  <a href="#-cenários-de-uso-e-demonstrações">Demonstrações</a> •
  <a href="#-automação-e-infraestrutura-como-código-iac">IaC</a> •
  <a href="#-roadmap-de-implementação">Roadmap</a>
</p>

---

## 🎯 Visão Geral do Projeto

O **PrimeOps Lab** não é apenas uma coleção de ferramentas, mas um **ecossistema funcional que simula os desafios de engenharia e segurança de uma empresa moderna**. Ele foi projetado para ir além da teoria, implementando uma infraestrutura híbrida (On-Premise + Cloud) totalmente gerenciada por código, monitorada por um SOC (Security Operations Center) em miniatura e operada com uma mentalidade DevSecOps.

O objetivo é demonstrar proficiência prática nas seguintes áreas:
- **Arquitetura de Sistemas Distribuídos e Redes Seguras.**
- **Operações de Segurança (SecOps) e Resposta a Incidentes.**
- **Automação de Infraestrutura (IaC) e Cultura DevOps.**
- **Segurança em Pipelines de CI/CD e Orquestração de Containers (DevSecOps).**
- **Governança, Risco e Conformidade (GRC) aplicados à tecnologia.**

---

## 🏗️ Arquitetura do Ecossistema

A topologia foi desenhada para refletir uma arquitetura de defesa em camadas (*defense-in-depth*), com redes segregadas, controle de perímetro e visibilidade centralizada.

*(**Nota:** Substitua o link abaixo pela imagem real do seu diagrama quando o tiver)*
<p align="center">
  <img src="URL_PARA_SEU_DIAGRAMA_DE_ARQUITETURA.png" alt="Diagrama da Arquitetura do PrimeOps Lab"/>
  <br>
  <em>Diagrama de alto nível da infraestrutura híbrida.</em>
</p>

**Componentes Chave:**
- **Fundação On-Premise:** Um hypervisor Proxmox VE hospeda a infraestrutura principal, com armazenamento segmentado (SSD para performance, RAID 1 para resiliência de dados).
- **Perímetro de Segurança:** Um firewall virtual (OPNsense) gerencia todo o tráfego Norte-Sul e Leste-Oeste entre redes segregadas (DMZ, Rede de Aplicações, Rede de Gerenciamento).
- **Acesso Remoto Zero-Trust:** O acesso ao laboratório é feito exclusivamente via VPN (WireGuard), garantindo que nenhuma porta de gerenciamento seja exposta.
- **Gerenciamento de Identidade Centralizado:** Um Provedor de Identidade (Active Directory / FreeIPA) atua como a única fonte da verdade para autenticação, integrado a um sistema de SSO (Keycloak) para aplicações.
- **SOC e Observabilidade:** Um SIEM (Wazuh) e uma stack de monitoramento (Prometheus/Grafana) coletam, analisam e geram alertas para eventos de segurança e métricas de performance de todo o ecossistema.
- **Plataforma de Aplicações Modernas:** Um cluster Kubernetes (K3s) hospeda aplicações containerizadas, gerenciado por um pipeline CI/CD seguro.

---

## 🛠️ Pilares Tecnológicos

| Categoria | Ferramentas Utilizadas | Propósito e Habilidades Demonstradas |
| :--- | :--- | :--- |
| **Virtualização & Infra** | `Proxmox VE`, `ZFS`, `Linux (Ubuntu)` | Gerenciamento de hypervisor, redes virtuais, storage de alta performance e resiliência. |
| **Redes & Segurança** | `OPNsense`, `WireGuard`, `Suricata` | Arquitetura de redes, segmentação (VLANs), políticas de firewall, VPN, IDS/IPS. |
| **Identidade & Acesso** | `Active Directory`, `Keycloak`, `MFA` | Gerenciamento de identidade federada, SSO, OAuth 2.0/OIDC, RBAC e políticas de acesso. |
| **SIEM & Observabilidade** | `Wazuh`, `Prometheus`, `Grafana`, `ELK Stack` | Coleta e análise de logs, detecção de ameaças, monitoramento de métricas e criação de dashboards. |
| **Automação & IaC** | `Terraform`, `Ansible` | Provisionamento e configuração de infraestrutura como código, garantindo reprodutibilidade e escalabilidade. |
| **DevSecOps & Containers** | `Kubernetes (K3s)`, `Docker`, `GitLab CI` | Orquestração de containers, automação de build/deploy, integração de segurança no pipeline (SAST/DAST). |
| **Segurança Avançada** | `HashiCorp Vault`, `OPA`, `Sigstore` | Gestão centralizada de segredos, política como código (PaC) e segurança da cadeia de suprimentos de software. |

---

## 🔬 Cenários de Uso e Demonstrações

Este laboratório permite a simulação de cenários do mundo real. A pasta `/docs/runbooks` contém guias detalhados para cada um.

1.  **Simulação de Ataque e Resposta (Blue Team):**
    - **Cenário:** Um ataque de força bruta é lançado contra um serviço na DMZ.
    - **Demonstração:** O firewall bloqueia o IP atacante, o Wazuh gera um alerta em tempo real no dashboard do SOC, e um e-mail é disparado para a equipe de segurança.
    - **Habilidades:** Detecção de intrusão, análise de logs, automação de alertas.

2.  **Pipeline DevSecOps em Ação:**
    - **Cenário:** Um desenvolvedor commita código com uma vulnerabilidade conhecida.
    - **Demonstração:** O pipeline CI/CD é acionado, o scanner de segurança (Trivy) detecta a falha e bloqueia o build, impedindo que o código vulnerável chegue à produção.
    - **Habilidades:** Shift-Left Security, automação de testes de segurança (SAST), governança de pipeline.

3.  **Provisionamento Automatizado de Infraestrutura:**
    - **Cenário:** Uma nova equipe de desenvolvimento precisa de um ambiente de staging.
    - **Demonstração:** Um único comando `terraform apply` provisiona um novo conjunto de VMs, as configura com Ansible e as registra no sistema de monitoramento, tudo em minutos.
    - **Habilidades:** Infraestrutura como Código, automação de ponta a ponta, agilidade operacional.

---

## 🤖 Automação e Infraestrutura como Código (IaC)

Todo o ambiente é definido como código e versionado neste repositório. Isso garante que ele possa ser destruído e recriado de forma consistente e automática.

- **Provisionamento:** `Terraform` é usado para criar os recursos de infraestrutura (VMs, redes, etc.) no Proxmox.
- **Configuração:** `Ansible` é usado para configurar o estado do sistema operacional e instalar aplicações dentro das VMs.

**Para reproduzir o ambiente:**
```bash
# Clone o repositório
git clone https://github.com/seu-usuario/primeops-lab.git
cd primeops-lab/iac

# Inicialize o Terraform
terraform init

# Revise e aplique o plano
terraform plan
terraform apply
```

---

## 🗺️ Roadmap de Implementação

Este projeto foi construído em fases lógicas, documentadas para referência e replicação.

- **[✅] Fase 0: Fundação** - Setup do Proxmox, redes e storage.
- **[✅] Fase 1: Acesso Seguro & Serviços** - Firewall, VPN e serviços essenciais (Web/Cloud).
- **[✅] Fase 2: Identidade & Observabilidade** - Implantação de AD, SIEM e stack de monitoramento.
- **[✅] Fase 3: Automação & DevSecOps** - IaC, Cluster Kubernetes e pipeline CI/CD.
- **[🚧] Fase 4: Segurança Avançada** - Implementação de Vault, OPA e Sigstore.
- **[🔄] Fase 5: Documentação & Melhoria Contínua** - Refinamento de runbooks e arquitetura.

---

## 📜 Licença

Este projeto é licenciado sob a [MIT License](LICENSE). Ele é destinado a fins educacionais e de demonstração. **NÃO UTILIZE EM AMBIENTES DE PRODUÇÃO.**
