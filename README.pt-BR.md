# Samsung Health Dashboard

Painel visual e analítico para os dados exportados do **Samsung Health** — muito mais completo do que a visualização padrão do app. Um único arquivo HTML autocontido que lê seus CSVs exportados e transforma tudo em gráficos, comparações e cruzamentos entre métricas.

Sem instalação, sem servidor, sem conta. Você abre o arquivo, seleciona a pasta com os CSVs, e o painel é montado na hora — **100% no seu navegador**. Nenhum dado sai da sua máquina.

---

## ✨ O que o painel mostra

### 📋 Painel geral
KPIs consolidados (FC média, sono médio, passos/dia, peso atual) e destaques automáticos sobre seus dados recentes.

### ❤️ Coração
- Frequência cardíaca ao longo do dia (por data selecionável)
- FC mínima, máxima e de repouso
- Distribuição de FC por horário do dia
- Comparação de FC média por dia da semana
- Episódios de frequência cardíaca elevada fora de exercícios
- Evolução da FC de repouso ao longo do tempo

### 😴 Sono
- Horário de dormir e de acordar
- Duração total de sono por noite
- Composição por estágio: sono leve, profundo, REM e despertares
- Regularidade do horário de sono
- Comparação entre dias de semana e fins de semana
- Tabela completa com todas as noites registradas

### 🏃 Exercícios
- Distância, duração, calorias e frequência cardíaca por sessão
- Evolução semanal de distância e calorias
- Carga de treinamento (aguda x crônica)
- Relação entre distância percorrida e FC média
- Tabela detalhada de todas as sessões

### 📊 Evolução
Peso, passos, sono, frequência cardíaca, frequência de exercícios e estresse, todos lado a lado ao longo do tempo.

### 🔀 Cruzamentos
A parte mais analítica do painel — cruza métricas diferentes para responder perguntas como:
- Nos dias em que você dormiu menos de 6h30, como fica sua FC média no dia seguinte?
- Como sua frequência cardíaca se comporta em dias de exercício comparado a dias de descanso?
- Existe relação entre duração do sono e nível de estresse?
- Dias mais ativos (mais passos) resultam em noites de sono mais longas?

Cada cruzamento vem com o coeficiente de correlação (r) calculado automaticamente.

---

## 🚀 Como usar

1. **Exporte seus dados do Samsung Health**
   No app, vá em *Configurações → Sincronizar dados com o Samsung Cloud* (ou *Gerenciar dados → Baixar dados pessoais*) e exporte um arquivo `.zip`.

2. **Extraia o `.zip`** em uma pasta no seu computador. Ela deve conter os arquivos `.csv` (nomes como `com.samsung.shealth.tracker.heart_rate.*.csv`, `com.samsung.health.sleep_stage.*.csv`, etc.).

3. **Abra o `samsung_health_dashboard.html`** com duplo clique — ele abre em qualquer navegador moderno (Chrome, Edge, Firefox).

4. Clique em **"Selecionar pasta"** e escolha a pasta onde extraiu os CSVs.

5. Pronto — o painel é montado automaticamente. Sempre que exportar dados novos do Samsung Health, basta clicar em "Selecionar pasta" de novo para atualizar.

> Não é possível o navegador monitorar a pasta sozinho por questões de segurança do próprio navegador — a atualização é sempre feita clicando no botão.

---

## 🔒 Privacidade

Todo o processamento acontece localmente, no JavaScript do navegador. Não há backend, não há upload, não há telemetria. O arquivo é totalmente autocontido: as bibliotecas usadas (PapaParse para ler CSV e Chart.js para os gráficos) vêm embutidas no próprio HTML, então o painel funciona até sem conexão com a internet.

---

## 🛠️ Tecnologia

- HTML + CSS + JavaScript puro (sem build, sem dependências externas em tempo de execução)
- [PapaParse](https://www.papaparse.com/) para parsing dos CSVs
- [Chart.js](https://www.chartjs.org/) para os gráficos

---

## ⚠️ Limitações conhecidas

- **HRV**: o export em CSV do Samsung Health não inclui os valores numéricos de HRV (ficam em arquivos binários internos do app), então essa métrica aparece como indisponível.
- **Tipos de exercício**: o Samsung Health identifica atividades por códigos numéricos internos; o painel reconhece os mais comuns (caminhada, corrida, ciclismo, natação, musculação, yoga) e exibe `Atividade #NNN` para os demais.
- Compatível com navegadores modernos que suportam seleção de pasta via `<input webkitdirectory>` (Chrome, Edge, Firefox, Opera).
