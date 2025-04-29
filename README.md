Zairyx: A Amiga de IA para Organizar Arquivos, Finanças e Sustentabilidade
Zairyx é uma assistente de inteligência artificial (IA) open-source, projetada para integrar-se aos gerenciadores de arquivos (Windows Explorer, Android, Mac, Linux) e empoderar usuários, especialmente jovens e adolescentes, a organizarem suas vidas digitais, gerenciarem finanças e adotarem práticas sustentáveis. Desenvolvida por Tiago Rocha, um comunicador sem conhecimento técnico, em colaboração com uma IA (Grok), a Zairyx prova que a tecnologia pode ser moldada por qualquer pessoa através de conversas naturais, sem necessidade de programação.

Por Que a Zairyx?
Imagine Maria, uma estudante de 17 anos de uma comunidade carente. Com a Zairyx, ela organiza seus arquivos escolares, descobre como economizar na mesada e aprende a fazer compostagem com sobras de alimentos. A Zairyx não é apenas uma ferramenta; é uma amiga que guia, educa e inspira, mostrando que a IA é acessível e pode transformar vidas. E se a sua empresa pudesse liderar essa transformação, conectando milhões de jovens a um futuro mais organizado, financeiramente consciente e sustentável?

Objetivos
Organização Intuitiva de Arquivos: Usar busca semântica, dicas de organização e memorização para simplificar a gestão de arquivos.
Educação Financeira: Analisar recibos, faturas, pagamentos e recebimentos, gerando relatórios e gráficos que ensinam gestão financeira.
Educação Sustentável: Fornecer dicas personalizadas para reduzir o impacto ambiental, como compostagem para usuários de baixa renda, contribuindo para créditos de carbono corporativos.
Inspiração para o Futuro: Mostrar que a IA é acessível, incentivando jovens a explorarem tecnologia sem barreiras técnicas.
Benefícios para Usuários
Jovens e Adolescentes: Organizam arquivos escolares, gerenciam mesadas e aprendem práticas sustentáveis, como reaproveitar sobras de alimentos.
Profissionais: Gerenciam projetos, analisam finanças e adotam práticas sustentáveis no trabalho.
Comunidades de Baixa Renda: Recebem dicas práticas para reduzir desperdício e custos, como compostagem e sopas nutritivas.
Inspiração: A interação com a Zairyx, via Microsoft Copilot, mostra que qualquer pessoa pode usar IA para criar e inovar.
Benefícios para Corporações
Liderança em IA Acessível: Integre sua IA (ex.: Copilot, Gemini) ao Zairyx e democratize a tecnologia, posicionando sua empresa como pioneira em inovação inclusiva.
Sustentabilidade: Use dados de redução de impacto para obter créditos de carbono, alinhando-se a metas globais de ESG.
Educação e Inovação: Amplie sua plataforma educacional, oferecendo uma experiência contínua que empodera jovens globalmente.
Imagem e Impacto: Seja a empresa que transforma vidas, conectando tecnologia, educação e sustentabilidade em um futuro promissor.
Tecnologias
Linguagem: Python
Frameworks de IA: Hugging Face Transformers, Tesseract-OCR
Agente Principal: Microsoft Copilot
Automação No-Code: n8n
API: FastAPI
Gráficos: Matplotlib
Banco de Dados: SQLite
Ambiente: WSL 2 (Ubuntu 22.04), Docker
IDE: Visual Studio Code
Pré-requisitos
Windows 11 com WSL 2 (Ubuntu 22.04)
Docker e Docker Compose
Python 3.8+
GPU: AMD RX 580 8GB (ou NVIDIA RTX 4060 Ti para melhor suporte a IA)
Instalação
Configure o WSL 2 e Ubuntu:
powershell

Copiar
# No Windows PowerShell
wsl --install
Instale o Docker no WSL 2:
bash

Copiar
sudo apt update
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker $USER
newgrp docker
Configure o Docker (em /etc/docker/daemon.json):
json

Copiar
{
  "default-ulimits": {
    "nofile": {
      "Name": "nofile",
      "Hard": 65536,
      "Soft": 65536
    }
  },
  "storage-driver": "overlay2"
}
Reinicie o Docker:
bash

Copiar
sudo systemctl restart docker
Instale as Dependências Python: Crie um arquivo requirements.txt com:
plaintext

Copiar
fastapi
uvicorn
transformers
pytesseract
torch
pillow
matplotlib
sqlite3
Instale:
bash

Copiar
pip install -r requirements.txt
Clone este Repositório e Rode a API:
bash

Copiar
git clone https://github.com/TiagoIA-ux/Zairyx-FileManager.git
cd ai-file-manager
python main.py
Uso
A API FastAPI, integrada ao Microsoft Copilot, oferece os seguintes endpoints:

Busca Semântica: /search_files - Encontre arquivos com descrições naturais (ex.: "recibos de 2024").
bash

Copiar
curl -X POST "http://localhost:8000/search_files" -d '{"query": "recibos de 2024"}' -H "Content-Type: application/json"
Dicas de Organização: /organize_tips - Receba sugestões para organizar arquivos.
bash

Copiar
curl "http://localhost:8000/organize_tips"
Memorização: /save_file_location e /recall_file - Salve e recupere localizações de arquivos.
bash

Copiar
curl -X POST "http://localhost:8000/save_file_location" -d '{"name": "recibo_marco", "path": "data/finanças/recibo.jpg", "description": "Recibo de março"}' -H "Content-Type: application/json"
curl "http://localhost:8000/recall_file?name=recibo_marco"
Análise Financeira: /analyze_receipt - Extraia e categorize dados de recibos.
bash

Copiar
curl -X POST "http://localhost:8000/analyze_receipt" -d '{"file_path": "data/finanças/recibo.jpg"}' -H "Content-Type: application/json"
Relatório Financeiro: /financial_report - Gere relatórios e gráficos de gastos.
bash

Copiar
curl "http://localhost:8000/financial_report"
Dicas Sustentáveis: /sustainability_tips - Receba dicas de redução de impacto ambiental.
bash

Copiar
curl "http://localhost:8000/sustainability_tips"
Integração com Gerenciadores de Arquivos:

Configure o Samba para compartilhar a pasta data/finanças:
bash

Copiar
sudo nano /etc/samba/smb.conf
Adicione:
text

Copiar
[finanças]
path = /home/<seu_usuario>/ai-file-manager/data/finanças
writable = yes
browsable = yes
Reinicie o Samba:
bash

Copiar
sudo systemctl restart smbd
Roadmap
 Configurar ambiente (WSL 2, Docker, Python).
 Desenvolver busca semântica, análise financeira e dicas sustentáveis (até 07/05/2025).
 Integrar com Windows Explorer, Android e Mac (até 25/05/2025).
 Testar com beta testers (até 06/07/2025).
 Preparar demo para corporações (até 20/07/2025).
Contribuição
Junte-se à nossa comunidade no GitHub! Abra issues ou envie pull requests para ajudar a moldar a Zairyx.