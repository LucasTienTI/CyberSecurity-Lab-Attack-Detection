# 🛡️ Lab de Ataque e Detecção: Kali Linux vs Windows 11

Este projeto demonstra a simulação de um ataque de reconhecimento (Port Scanning) e a implementação de telemetria para detecção de incidentes em ambiente Windows.

## 🎯 Objetivo
Simular um cenário real onde um atacante utiliza o Kali Linux para mapear a rede e o analista de segurança (SOC) utiliza o Windows Event Viewer para identificar e analisar a ameaça.

## 🚀 Passo a Passo da Implementação

### 1. Preparação da Telemetria (Blue Team)
Ativação da auditoria avançada de firewall via PowerShell (ADM):
```powershell
auditpol /set /subcategory:"Conexão de Plataforma de Filtragem" /success:enable /failure:enable

2. Execução do Ataque (Red Team)
Simulação de scan de portas utilizando o Kali Linux para identificar serviços ativos:

Bash
sudo nmap -sS -Pn -T4 [IP_DO_WINDOWS]

Evidência do Ataque (Kali Linux):
3. Análise e Detecção (SOC)
Detecção realizada através do Event ID 5157 (Windows Filtering Platform).

Evidência da Detecção (Windows Event Viewer):
🔎 Achados da Investigação
Ao analisar o evento de segurança capturado em 23/02/2026 às 17:53:18, os seguintes dados técnicos foram correlacionados:

IP Atacante: 192.168.100.93.

Porta Alvo: 1900.

Protocolo: UDP (17).

Resultado: Bloqueio efetuado com sucesso pelo firewall (ID 5157).
