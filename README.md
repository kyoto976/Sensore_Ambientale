# 📡 Sensore Ambientale ESP32 con Blynk

Un progetto basato su **ESP32** che monitora in tempo reale:
- 🌡️ Temperatura
- 💧 Umidità
- 🧪 Gas (MQ-2)
- 🌬️ Attiva una ventola in automatico

I dati vengono visualizzati su **Blynk**, e un LED segnala lo stato attivo.

---

## ⚙️ Componenti hardware

| Componente          | Modello               |
|---------------------|------------------------|
| Microcontrollore    | ESP32 Dev Module       |
| Sensore Temperatura/Umidità | HTU21D (I2C)      |
| Sensore Gas         | MQ-2 (analogico)       |
| LED + Resistenza    | 220Ω                   |
| Ventola (opzionale) | Collegata al pin 23    |

---

## 📷 Schema del circuito

![Schema del circuito](A_digital_illustration_provides_an_electronic_circ.png)

---

## 💻 Funzionamento

- Ogni **2 secondi**, l’ESP32 legge i valori da:
  - HTU21D → Temperatura / Umidità
  - MQ-2 → Livello gas (convertito in %)
- I dati vengono inviati a Blynk:
  - `V0`: gas
  - `V1`: temperatura
  - `V2`: umidità
  - `V3`: stato ventola
  - `V4`: controllo manuale (ON/OFF)
- La ventola si attiva se:
  - Temperatura ≥ 40°C
  - Gas ≥ 15%
  - O manualmente via app

---

## 🔌 Collegamenti principali

| ESP32 Pin | Collegamento     |
|-----------|------------------|
| 21 (SDA)  | SDA → HTU21D     |
| 22 (SCL)  | SCL → HTU21D     |
| 34        | MQ-2 (analogico) |
| 23        | LED / Fan        |
| 3V3       | VCC sensori      |
| GND       | GND comuni       |

---

## 📲 Dashboard Blynk

Template: **ESP32 Monitor**  
Token: salvato nel codice  
Controlli consigliati:
- Gauge per temperatura, umidità, gas
- Switch (V4) per fan manuale
- LED virtuale per stato fan (V3)

---

## 🧠 Autore

**Giuseppe Cialdella**  
🔗 [LinkedIn](https://www.linkedin.com/in/giuseppe-cialdella-2b582a295)

📧 giuseppecialdella97@gmail.com  
📍 Studente di Cybersecurity & Programmazione

---

## 📁 File inclusi

- `main.ino`: codice ESP32 completo
- `A_digital_illustration_provides_an_electronic_circ.png`: schema circuito

---

## 🚀 Futuri sviluppi

- ✅ Integrazione MQTT o Node-RED
- 📊 Dashboard su Grafana o ThingsBoard
- 🔋 Ottimizzazione consumi con modalità sleep
- ☁️ Connessione a Google Sheets o Telegram bot

---

## 📥 Come clonare

```bash
git clone https://github.com/kyoto976/Sensore-Ambientale.git
