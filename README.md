# EV3 DevOps - Taller de Integración Continua y Despliegue

Este repositorio contiene el pipeline de CI/CD y los manifiestos de infraestructura para el microservicio Spring Boot.

## 🚀 1. Arquitectura y Despliegue en la Nube (IE2)
El microservicio está completamente orquestado y desplegado en un entorno de producción utilizando **Kubernetes (Minikube)** montado sobre una instancia **AWS EC2 (t3.medium)**.

Para verificar que las réplicas del microservicio están operativas, se adjunta la evidencia del estado de los Pods en el clúster:

![Estado de los Pods de la Aplicación](./images/evidencia_pods.png)


---

## 📊 2. Monitoreo, Observabilidad y Dashboards (IE1 e IE3)
Para cumplir con los requisitos de observabilidad, se implementó un stack de monitoreo utilizando **Prometheus** (recolección de métricas masivas) y **Grafana** (visualización).

El dashboard analiza en tiempo real las cuotas de recursos asignadas al contenedor de Spring Boot. A continuación, se muestra el gráfico de rendimiento con métricas clave de **Uso de CPU** y **Memoria RAM (WSS)**:

![Dashboard de Grafana](./images/evidencia_grafana.png)


---

## 🛡️ 3. Políticas de Cumplimiento y Calidad (IE5 e IE6)
El pipeline en **GitHub Actions** valida la calidad del código mediante políticas estrictas antes de permitir cualquier empaquetado:

1. **SonarQube Cloud:** Analiza la presencia de bugs, code smells y vulnerabilidades.
2. **Control de Fallas Críticas (IE6):** El pipeline está diseñado de manera secuencial. Si una prueba unitaria falla o SonarCloud no aprueba las políticas de calidad, el flujo se detiene inmediatamente, bloqueando la construcción de la imagen Docker y evitando que el código defectuoso llegue a AWS.

![Pipeline Exitoso](./images/evidencia_pipeline.png)
