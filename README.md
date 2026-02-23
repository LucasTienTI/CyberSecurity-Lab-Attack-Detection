# 🛡️ Lab de Ataque e Detecção: Kali Linux vs Windows 11

Este projeto demonstra a simulação de um ataque de reconhecimento (Port Scanning) e a implementação de telemetria para detecção de incidentes em ambiente Windows.

## 🎯 Objetivo
Simular um cenário real onde um atacante utiliza o Kali Linux para mapear a rede e o analista de segurança (SOC) utiliza o Windows Event Viewer para identificar e analisar a ameaça.

## 🚀 Passo a Passo da Implementação

### 1. Preparação da Telemetria (Blue Team)
Para que o Windows registre o ataque, foi necessário ativar a auditoria avançada de firewall via PowerShell (ADM):
```powershell
auditpol /set /subcategory:"Conexão de Plataforma de Filtragem" /success:enable /failure:enable

2. Execução do Ataque (Red Team)
Simulação de scan de portas utilizando o Kali Linux para identificar serviços ativos e mapear a superfície de ataque:

Bash
sudo nmap -sS -Pn -T4 [IP_DO_WINDOWS]
Evidência do Ataque (Kali Linux):
3. Análise e Detecção (SOC)
A detecção foi realizada através do Event ID 5157 (Windows Filtering Platform), que registra conexões bloqueadas pelo firewall nativo.

Evidência da Detecção (Windows Event Viewer):
🔎 Achados da Investigação (Análise do Log)
Ao analisar o evento de segurança capturado, os seguintes dados técnicos foram correlacionados conforme as marcações no print:

Data/Hora: 23/02/2026 17:53:18.

IP Atacante: 192.168.100.93.

Porta Alvo: 1900 (Conforme destacado pela seta no print de evidência).

Protocolo: UDP (17).

Resultado: Bloqueio efetuado com sucesso pelo firewall (ID 5157).

🧠 Conclusão
Este laboratório demonstra a importância da visibilidade de rede. Sem a configuração correta das políticas de auditoria avançada, atividades de reconhecimento passariam despercebidas pelos logs padrão, dificultando a resposta a incidentes.
