# iot-monitor

Plataforma de **monitoramento IoT** com MQTT, Node.js e InfluxDB — coleta, armazenamento e visualização de dados de sensores em tempo real com dashboard Grafana.

---

## Stack Tecnológica

- [Node.js 18+](https://nodejs.org/)
- [MQTT.js](https://github.com/mqttjs/MQTT.js) (protocolo IoT)
- [Mosquitto](https://mosquitto.org/) (broker MQTT)
- [InfluxDB 2.x](https://www.influxdata.com/) (série temporal)
- [Grafana](https://grafana.com/) (dashboard)
- [Docker Compose](https://www.docker.com/)

---

## Estrutura de Pastas

```
iot-monitor/
├── src/
│   ├── broker/        # Configuração Mosquitto
│   ├── subscriber/    # Leitura dos tópicos MQTT
│   ├── ingestion/     # Gravação no InfluxDB
│   ├── api/           # REST API para consultas
│   └── alerts/        # Alertas e notificações
├── grafana/
│   └── dashboards/    # JSONs dos dashboards
├── influxdb/
└── docker-compose.yml  # Orquestração completa
```

---

## Pré-requisitos

- Docker e Docker Compose
- Node.js 18+ (se rodar sem Docker)

---

## Instalação Local (com Docker - recomendado)

### 1. Clone o repositório

```bash
git clone https://github.com/Tuliospin/iot-monitor.git
cd iot-monitor
```

### 2. Configure as variáveis de ambiente

```bash
cp .env.example .env
```

Edite o `.env`:

```env
INFLUXDB_URL=http://localhost:8086
INFLUXDB_TOKEN=seu-token-aqui
INFLUXDB_ORG=minha-org
INFLUXDB_BUCKET=iot-data
MQTT_BROKER=localhost
MQTT_PORT=1883
```

### 3. Suba todos os serviços

```bash
docker compose up -d
```

### 4. Acesse os serviços

| Serviço | URL |
|---------|-----|
| Grafana Dashboard | http://localhost:3000 |
| InfluxDB UI | http://localhost:8086 |
| API Node.js | http://localhost:3001 |
| MQTT Broker | localhost:1883 |

---

## Instalação Local (sem Docker)

### 1. Instale as dependências Node

```bash
npm install
```

### 2. Inicie o subscriber MQTT

```bash
node src/subscriber/index.js
```

### 3. Inicie a API

```bash
node src/api/server.js
```

---

## Funcionalidades

- 📦 Coleta de dados via MQTT
- 💿 Armazenamento eficiente em série temporal (InfluxDB)
- 📊 Dashboard Grafana para visualização em tempo real
- 🔔 Alertas por e-mail/webhook para anomalias
- 📉 API REST para consulta histórica

---

## Licença

MIT License © 2026 Túlio Silva
