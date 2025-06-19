# PROPUESTA TÉCNICA: Sistema de Gestión Inteligente para Invernadero de Tomates

## 📋 RESUMEN EJECUTIVO

**Proyecto**: Sistema de Monitoreo y Control Automatizado para Invernadero  
**Tecnología Principal**: LoRa + USR DR 302 + Sensores IoT  
**Objetivo**: Optimizar la producción de tomates mediante monitoreo continuo y control automatizado  
**ROI Estimado**: 25-40% aumento en productividad, 30% reducción en costos operativos  

---

## 🎯 OBJETIVOS DEL PROYECTO

### Objetivos Principales
- **Monitoreo 24/7** de parámetros críticos del invernadero
- **Automatización** de sistemas de riego, ventilación y climatización
- **Optimización** de condiciones de crecimiento para tomates
- **Reducción de pérdidas** por condiciones adversas
- **Trazabilidad completa** de datos ambientales

### Objetivos Específicos
- Mantener temperatura entre 18-25°C (día) y 15-18°C (noche)
- Controlar humedad relativa entre 60-80%
- Monitorear pH del suelo entre 6.0-6.8 (óptimo para tomates)
- Gestionar conductividad eléctrica 2.0-3.5 mS/cm
- Alertas automáticas ante condiciones críticas

---

## 🏗️ ARQUITECTURA TÉCNICA DEL SISTEMA

### Componentes Principales

#### 1. NODOS SENSORES DISTRIBUIDOS
```
┌─────────────────────────────────┐
│        NODO SENSOR LoRa         │
├─────────────────────────────────┤
│ • ESP32 + Módulo LoRa SX1276    │
│ • Sensor Temperatura/Humedad    │
│ • Sensor pH del suelo           │
│ • Sensor Conductividad (EC)     │
│ • Sensor Humedad del suelo      │
│ • Sensor de Luz (LUX)           │
│ • Batería + Panel Solar         │
└─────────────────────────────────┘
```

#### 2. GATEWAY CENTRAL (USR DR 302)
```
┌─────────────────────────────────┐
│       GATEWAY USR DR 302        │
├─────────────────────────────────┤
│ • Receptor LoRa multi-canal     │
│ • Conectividad 4G/WiFi/Ethernet │
│ • Procesamiento local de datos  │
│ • Buffer de datos offline       │
│ • Configuración remota          │
└─────────────────────────────────┘
```

#### 3. SERVIDOR CENTRAL
```
┌─────────────────────────────────┐
│        SERVIDOR BACKEND         │
├─────────────────────────────────┤
│ • API REST + WebSocket          │
│ • Base de Datos PostgreSQL      │
│ • Sistema de Alertas            │
│ • Motor de Reglas de Negocio    │
│ • Integración con Actuadores    │
└─────────────────────────────────┘
```

---

## 📊 ESPECIFICACIONES TÉCNICAS DETALLADAS

### Hardware Requerido

#### Nodos Sensores (Cantidad: 4-6 por invernadero)
| Componente | Modelo | Especificaciones | Precio Aprox. |
|------------|--------|------------------|---------------|
| Microcontrolador | ESP32-WROOM-32 | WiFi + Bluetooth, 240MHz | $8 USD |
| Módulo LoRa | SX1276 | 433/868/915 MHz, 20km alcance | $12 USD |
| Sensor T/H | SHT30 | ±0.2°C, ±2% RH, I2C | $15 USD |
| Sensor pH | Gravity pH | 0-14 pH, ±0.1 precisión | $45 USD |
| Sensor EC | DFRobot EC | 0-20 mS/cm, compensación temp. | $35 USD |
| Sensor Humedad Suelo | Capacitivo | 0-100%, resistente corrosión | $8 USD |
| Sensor Luz | BH1750 | 1-65535 lux, I2C digital | $5 USD |
| Batería | LiPo 3.7V 5000mAh | Recargable, protección | $20 USD |
| Panel Solar | 6V 2W | Carga automática | $15 USD |
| **TOTAL POR NODO** | | | **$163 USD** |

#### Gateway Principal
| Componente | Modelo | Especificaciones | Precio |
|------------|--------|------------------|--------|
| Gateway LoRa | USR DR 302 | 8 canales, 4G/WiFi/Ethernet | $280 USD |
| Antena LoRa | 868MHz 8dBi | Omnidireccional, exterior | $25 USD |
| **TOTAL GATEWAY** | | | **$305 USD** |

#### Actuadores y Control
| Componente | Especificaciones | Precio |
|------------|------------------|--------|
| Relés WiFi (4 canales) | Control bombas/ventiladores | $35 USD |
| Electroválvulas riego | 12V, 1/2", normalmente cerrada | $25 USD c/u |
| Ventiladores | 12V, control PWM | $40 USD c/u |
| Sensores adicionales | Presión, flujo, etc. | $50 USD |

### Software y Plataforma

#### Stack Tecnológico
- **Firmware**: Arduino/PlatformIO (C++)
- **Gateway**: Python 3.9+ con librerías LoRa
- **Backend**: Node.js + Express + Sequelize ORM
- **Frontend**: React + Material-UI + Chart.js
- **Base de Datos**: PostgreSQL 13+
- **Hosting**: AWS/Azure/Google Cloud o servidor local

---

## 📈 FUNCIONALIDADES DEL SISTEMA

### 1. MONITOREO EN TIEMPO REAL
- **Dashboard web** con gráficos en vivo
- **Actualización cada 5 minutos** de todos los sensores
- **Mapas de calor** del invernadero
- **Tendencias históricas** con análisis predictivo

### 2. SISTEMA DE ALERTAS INTELIGENTE
```
ALERTAS CRÍTICAS (Inmediatas):
• Temperatura > 35°C o < 10°C
• Humedad > 95% o < 30%
• pH < 5.0 o > 8.0
• Falla de comunicación > 15 min

ALERTAS PREVENTIVAS (30 min):
• Temperatura fuera de rango óptimo
• Humedad del suelo < 40%
• Conductividad anormal
• Batería baja en sensores
```

### 3. AUTOMATIZACIÓN Y CONTROL
- **Riego automático** basado en humedad del suelo
- **Control de ventilación** por temperatura/humedad
- **Ajuste de pH** automático con dosificadores
- **Programación de horarios** de riego/fertilización

### 4. ANÁLISIS Y REPORTES
- **Reportes diarios/semanales/mensuales**
- **Análisis de correlaciones** entre variables
- **Predicción de cosecha** basada en condiciones
- **Optimización de recursos** (agua, fertilizantes)

---

## 💰 ANÁLISIS ECONÓMICO

### Inversión Inicial
| Concepto | Cantidad | Precio Unit. | Total |
|----------|----------|--------------|-------|
| Nodos Sensores | 6 unidades | $163 USD | $978 USD |
| Gateway USR DR 302 | 1 unidad | $305 USD | $305 USD |
| Actuadores y Control | 1 set | $200 USD | $200 USD |
| Desarrollo Software | 120 horas | $25 USD/h | $3,000 USD |
| Instalación y Configuración | 40 horas | $30 USD/h | $1,200 USD |
| **TOTAL INVERSIÓN** | | | **$5,683 USD** |

### Beneficios Proyectados (Anual)
- **Aumento productividad**: 30% = $8,000 USD
- **Ahorro en agua**: 25% = $1,200 USD
- **Ahorro en fertilizantes**: 20% = $800 USD
- **Reducción pérdidas**: 40% = $3,000 USD
- **TOTAL BENEFICIOS**: $13,000 USD/año

### ROI: 129% en el primer año

---

## 📅 CRONOGRAMA DE IMPLEMENTACIÓN

### Fase 1: Desarrollo y Preparación (4 semanas)
- **Semana 1-2**: Desarrollo firmware y software base
- **Semana 3**: Configuración gateway y comunicaciones
- **Semana 4**: Desarrollo dashboard y API

### Fase 2: Instalación y Pruebas (3 semanas)
- **Semana 5**: Instalación hardware en invernadero
- **Semana 6**: Configuración y calibración sensores
- **Semana 7**: Pruebas integrales y ajustes

### Fase 3: Puesta en Producción (1 semana)
- **Semana 8**: Capacitación personal y documentación
- **Entrega**: Sistema completamente operativo

**DURACIÓN TOTAL: 8 semanas**

---

## 🔒 SEGURIDAD Y CONFIABILIDAD

### Medidas de Seguridad
- **Encriptación AES-256** en comunicaciones LoRa
- **Autenticación** de dispositivos por certificados
- **Backup automático** de datos cada 6 horas
- **Redundancia** en sensores críticos

### Confiabilidad del Sistema
- **Disponibilidad**: 99.5% (máximo 3.6 horas downtime/mes)
- **Autonomía**: 7 días sin conexión (buffer local)
- **Mantenimiento**: Remoto en 90% de casos
- **Vida útil**: 5+ años con mantenimiento básico

---

## 🎓 CAPACITACIÓN Y SOPORTE

### Capacitación Incluida
- **Manual de usuario** completo en español
- **Sesión de capacitación** presencial (4 horas)
- **Videos tutoriales** para operación básica
- **Documentación técnica** detallada

### Soporte Post-Implementación
- **Garantía**: 12 meses en hardware
- **Soporte técnico**: 6 meses incluido
- **Actualizaciones**: Software gratuitas por 2 años
- **Mantenimiento**: Plan opcional $500 USD/año

---

## ✅ PRÓXIMOS PASOS

1. **Aprobación de propuesta** y presupuesto
2. **Visita técnica** al invernadero para mediciones
3. **Pedido de componentes** (tiempo entrega: 2 semanas)
4. **Inicio de desarrollo** según cronograma
5. **Reuniones de seguimiento** semanales

---

**Contacto del Proyecto:**  
**Ingeniero Responsable**: [Tu Nombre]  
**Email**: [tu-email]  
**Teléfono**: [tu-teléfono]  

*Esta propuesta es válida por 30 días desde la fecha de emisión.*

---

## 📋 ANEXOS TÉCNICOS

### ANEXO A: Especificaciones USR DR 302

#### Características Técnicas del Gateway
```
Modelo: USR-DR302-L08
• Frecuencia LoRa: 470MHz (configurable 410-525MHz)
• Canales simultáneos: 8 canales
• Sensibilidad: -139dBm
• Potencia TX: 27dBm (500mW)
• Alcance: hasta 15km en campo abierto
• Conectividad: 4G LTE Cat-1, WiFi 802.11b/g/n, Ethernet
• Protocolos: TCP/UDP/HTTP/MQTT
• Alimentación: 12V DC, 2A
• Temperatura operación: -40°C a +85°C
• Grado protección: IP65
• Dimensiones: 180×120×45mm
```

#### Configuración de Red LoRa
```
Parámetros de Red:
• Spreading Factor: SF7-SF12 (configurable)
• Bandwidth: 125kHz, 250kHz, 500kHz
• Coding Rate: 4/5, 4/6, 4/7, 4/8
• Potencia TX: 14-27dBm (ajustable)
• Clase LoRaWAN: A, B, C
• Encriptación: AES-128
```

### ANEXO B: Protocolos de Comunicación

#### Estructura de Datos LoRa
```json
{
  "node_id": "GREENHOUSE_01_SENSOR_03",
  "timestamp": "2024-01-15T14:30:00Z",
  "battery_level": 85,
  "signal_strength": -67,
  "sensors": {
    "temperature": {
      "value": 23.5,
      "unit": "°C",
      "status": "normal"
    },
    "humidity": {
      "value": 68.2,
      "unit": "%RH",
      "status": "normal"
    },
    "ph": {
      "value": 6.4,
      "unit": "pH",
      "status": "normal"
    },
    "conductivity": {
      "value": 2.8,
      "unit": "mS/cm",
      "status": "normal"
    },
    "soil_moisture": {
      "value": 45.3,
      "unit": "%",
      "status": "low"
    },
    "light_intensity": {
      "value": 25000,
      "unit": "lux",
      "status": "normal"
    }
  },
  "alerts": [
    {
      "type": "warning",
      "message": "Soil moisture below optimal level",
      "threshold": 50,
      "current_value": 45.3
    }
  ]
}
```

#### API Endpoints del Sistema
```
GET /api/v1/sensors/current          # Datos actuales todos los sensores
GET /api/v1/sensors/{id}/history     # Histórico de sensor específico
GET /api/v1/alerts/active           # Alertas activas
POST /api/v1/actuators/control      # Control de actuadores
GET /api/v1/reports/daily           # Reporte diario
POST /api/v1/config/thresholds      # Configurar umbrales
```

### ANEXO C: Rangos Óptimos para Tomates

#### Parámetros Ambientales Críticos
```
TEMPERATURA:
• Germinación: 20-25°C
• Crecimiento vegetativo: 18-24°C (día), 15-18°C (noche)
• Floración: 20-25°C (día), 16-18°C (noche)
• Fructificación: 22-26°C (día), 17-20°C (noche)

HUMEDAD RELATIVA:
• Óptima: 60-80%
• Crítica alta: >90% (riesgo hongos)
• Crítica baja: <40% (estrés hídrico)

pH DEL SUELO:
• Óptimo: 6.0-6.8
• Aceptable: 5.8-7.2
• Crítico: <5.5 o >7.5

CONDUCTIVIDAD ELÉCTRICA:
• Plántulas: 0.8-1.2 mS/cm
• Crecimiento: 1.5-2.5 mS/cm
• Producción: 2.0-3.5 mS/cm
• Máximo tolerable: 4.0 mS/cm

HUMEDAD DEL SUELO:
• Óptima: 70-80% capacidad de campo
• Riego necesario: <60%
• Saturación: >90% (riesgo asfixia radicular)

LUMINOSIDAD:
• Mínima: 15,000 lux
• Óptima: 25,000-35,000 lux
• Máxima: 50,000 lux (con ventilación)
```

### ANEXO D: Algoritmos de Control

#### Lógica de Riego Automático
```python
def irrigation_control(soil_moisture, temperature, humidity, time_of_day):
    """
    Algoritmo de control de riego inteligente
    """
    # Umbrales base
    moisture_threshold = 60  # %

    # Ajustes por temperatura
    if temperature > 28:
        moisture_threshold += 10
    elif temperature < 18:
        moisture_threshold -= 5

    # Ajustes por humedad ambiental
    if humidity > 85:
        moisture_threshold -= 5
    elif humidity < 50:
        moisture_threshold += 5

    # Restricciones horarias
    if 22 <= time_of_day <= 6:  # Noche
        moisture_threshold -= 10  # Menos riego nocturno

    # Decisión de riego
    if soil_moisture < moisture_threshold:
        return {
            "action": "start_irrigation",
            "duration": calculate_irrigation_time(soil_moisture, moisture_threshold),
            "reason": f"Soil moisture {soil_moisture}% below threshold {moisture_threshold}%"
        }

    return {"action": "no_irrigation", "reason": "Soil moisture adequate"}
```

#### Sistema de Alertas Escalonadas
```
NIVEL 1 - INFORMACIÓN (Verde):
• Datos fuera de rango óptimo pero dentro de aceptable
• Notificación en dashboard únicamente
• Ejemplo: Temperatura 26°C (óptimo: 18-25°C)

NIVEL 2 - ADVERTENCIA (Amarillo):
• Parámetros cerca de límites críticos
• Email/SMS a responsable técnico
• Ejemplo: Humedad 35% (crítico: <30%)

NIVEL 3 - CRÍTICO (Naranja):
• Condiciones que pueden afectar la producción
• Llamada automática + email/SMS
• Activación de actuadores automáticos
• Ejemplo: Temperatura 32°C

NIVEL 4 - EMERGENCIA (Rojo):
• Condiciones que pueden causar pérdida total
• Llamadas múltiples + notificaciones push
• Activación de todos los sistemas de emergencia
• Ejemplo: Temperatura >38°C o falla total de comunicación
```

### ANEXO E: Plan de Mantenimiento

#### Mantenimiento Preventivo Mensual
```
SENSORES:
□ Calibración de sensores pH (mensual)
□ Limpieza de sensores de humedad del suelo
□ Verificación de conexiones eléctricas
□ Revisión de niveles de batería
□ Limpieza de paneles solares

GATEWAY:
□ Verificación de conectividad 4G/WiFi
□ Actualización de firmware si disponible
□ Limpieza de antenas
□ Verificación de alimentación eléctrica

SOFTWARE:
□ Backup completo de base de datos
□ Verificación de logs de errores
□ Actualización de certificados de seguridad
□ Prueba de sistema de alertas
```

#### Mantenimiento Correctivo
```
PROBLEMAS COMUNES Y SOLUCIONES:

1. Sensor sin comunicación:
   • Verificar batería (>20%)
   • Revisar antena LoRa
   • Comprobar configuración de red
   • Reinicio remoto del nodo

2. Lecturas erróneas:
   • Calibración de sensor específico
   • Verificar conexiones físicas
   • Comprobar interferencias electromagnéticas
   • Reemplazo de sensor si necesario

3. Gateway desconectado:
   • Verificar conectividad a internet
   • Reinicio del gateway
   • Verificar configuración de red
   • Contactar ISP si problema persiste
```

### ANEXO F: Escalabilidad del Sistema

#### Expansión Futura Posible
```

• Agregar sensores de CO2
• Implementar cámaras de monitoreo
• Sistema de control de iluminación LED
• Integración con estación meteorológica


• Análisis de imágenes con IA para detección de plagas
• Sistema de fertirrigación automatizado
• Control de cortinas y ventanas automáticas
• Integración con drones para monitoreo aéreo


• Machine Learning para predicción de cosechas
• Automatización completa del invernadero
```

**DOCUMENTO TÉCNICO COMPLETO**
**Versión**: 1.0
**Fecha**: Junio 19 2025
