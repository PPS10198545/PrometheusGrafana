# Proyecto de Monitorización con Prometheus, Grafana, Node Exporter y cAdvisor

Este proyecto documenta la puesta en marcha de una arquitectura de monitorización basada en **Prometheus**, **Grafana**, **Node Exporter** y **cAdvisor** mediante Docker Compose. El objetivo es supervisar tanto los contenedores como los recursos del sistema local y remoto.

---

## Estructura del proyecto

```
.
├── docker-compose.yml       # Stack de servicios Prometheus, Grafana, cAdvisor
├── prometheus/prometheus.yml # Configuración de Prometheus con targets definidos
├── assets/                   # Evidencias de funcionamiento del entorno
└── README.md                 # Documentación técnica
```

---

## 🧱 Preparación del entorno

Se creó una red personalizada de Docker para aislar los servicios.

---

## 🐧 Node Exporter como servicio

En el servidor remoto, se descargó e instaló `node_exporter`, configurándolo como servicio `systemd` y verificando que estuviera en ejecución:

📸 **Captura.png**
![Captura4](/assets/Captura4.png)

---

## 🚀 Despliegue de la solución

Se utilizó el siguiente comando para levantar el stack completo desde un `docker-compose.yml` personalizado:

```bash
docker compose up -d --build
```

Esto inicia:
- **Prometheus** en el puerto `9090`
- **Grafana** en el puerto `3000`
- **cAdvisor** en el puerto `8080`

---

## 📈 Visualización de servicios

### cAdvisor

Muestra en tiempo real el uso de CPU, memoria y disco de los contenedores activos.

📸 **Captura1.png**
![Captura1](/assets/Captura1.png)

---

### Grafana

Plataforma de dashboards que permite representar gráficamente las métricas recopiladas.

📸 **Captura2.png**
![Captura2](/assets/Captura2.png)

---

### Prometheus

Sistema de recolección de métricas con interfaz propia para consultas y gráficos.

📸 **Captura3.png**
![Captura3](/assets/Captura3.png)

---

### Targets configurados

Prometheus detecta y monitorea los siguientes endpoints:
- cAdvisor
- Node Exporter local
- Prometheus
- Node Exporter remoto
- Traefik

📸 **Captura5.png**
![Captura5](/assets/Captura5.png)

---

## ✅ Conclusiones

Este laboratorio demuestra cómo construir un entorno completo de monitorización mediante:
- Orquestación con Docker Compose
- Visualización con Grafana
- Recolección de métricas con Prometheus
- Exportación de métricas con Node Exporter y cAdvisor

Ideal para entornos de desarrollo, pruebas o como base para producción ligera.

---

