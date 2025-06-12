
# 🌡️ Projeto FIAP – Enterprise Challenge - Sprint 2 - Reply

[![Grupo](https://img.shields.io/badge/Grupo-77-green)]()
[![Turma](https://img.shields.io/badge/Turma-1TIAOB%2F2025-blue)]()
[![Status](https://img.shields.io/badge/Status-Concluído-success)]()

---
## Fase 4  
Período: 21/05/2025 a 11/06/2025

## 👨‍🎓 Integrantes:
- Deivisson Gonçalves Lima – RM565095 – [deivisson.engtele@gmail.com](mailto:deivisson.engtele@gmail.com)
- Omar Calil Abrão Mustafá Assem – RM561375 – [ocama12@gmail.com](mailto:ocama12@gmail.com)
- Paulo Henrique de Sousa – RM564262 – [pauloo.sousa16@outlook.com](mailto:pauloo.sousa16@outlook.com)
- Renan Danilo dos Santos Pereira – RM566175 – [renansantos4978@gmail.com](mailto:renansantos4978@gmail.com)

## 👩‍🏫 Professores:
### Tutor(a):
- Lucas Gomes Moreira  
### Coordenador(a):
- André Godoi Chiovato  
---

## 💡 Descrição

Este projeto foi desenvolvido como parte da atividade prática da Fase 4 da disciplina de Inteligência Artificial da FIAP, em parceria com a empresa Hermes Reply. O objetivo é simular um sistema básico de **monitoramento industrial** com foco em temperatura e umidade, utilizando o microcontrolador **ESP32** e o sensor **DHT22** na plataforma **Wokwi**.

---

## 🎯 Objetivos do Projeto

* Simular um ambiente industrial com coleta de dados ambientais.
* Utilizar o sensor DHT22 para medir temperatura e umidade.
* Visualizar os dados no Monitor Serial.
* Analisar estatisticamente os dados coletados.
* Representar as variações em gráfico.
* Documentar o circuito e código-fonte no GitHub.

---

## 🔌 Componentes Simulados

* **Placa ESP32**
* **Sensor de Temperatura e Umidade DHT22**
* **Plataforma Wokwi (simulação do circuito)**

---

## 🧠 Lógica de Funcionamento

* O ESP32 inicializa e realiza leituras periódicas (a cada 2s) do DHT22.
* Os dados lidos (temperatura e umidade) são enviados ao **Monitor Serial**.
* Os valores são registrados e utilizados para **análise e visualização estatística**.

### 📋 Ligações do Circuito

| Pino do DHT22 | Pino do ESP32 |
|---------------|----------------|
| VCC           | 3V3            |
| DATA (SDA)    | GPIO 15        |
| GND           | GND            |

---

## 📄 Código-Fonte (Arduino/C++)

```cpp
#include "DHT.h"

#define DHTPIN 15
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
  Serial.println("Iniciando leitura do DHT22...");
}

void loop() {
  delay(2000);
  float temperatura = dht.readTemperature();
  float umidade = dht.readHumidity();

  if (isnan(temperatura) || isnan(umidade)) {
    Serial.println("Falha na leitura do sensor DHT!");
    return;
  }

  Serial.print("Temperatura: ");
  Serial.print(temperatura);
  Serial.print(" °C | Umidade: ");
  Serial.print(umidade);
  Serial.println(" %");
}
```

---

## 📊 Análise e Gráfico

* Foram simuladas **10 leituras sequenciais**.
* Os dados foram registrados no arquivo `dados_simulados_dht22.csv`.
* A temperatura variou entre **24.0 °C e 24.7 °C**.
* A umidade oscilou entre **38.5% e 40.0%**.

### 📈 Gráfico de Variação

![Gráfico de Dados](grafico.png)

---

## 📷 Imagens do Projeto

* Circuito simulado na Wokwi: `imagens/circuito.png`
* Captura do Serial Monitor: `imagens/monitor_serial.png`

---

## 💻 Estrutura do Projeto

```
enterprise-challenge-reply/
├── docs/
│   ├── circuito.png                                            # Circuito do Wokwi
│   ├── Registro da simulação                                   # Leitura no serial
│   └── Gráfico de leituras simuladas.png                       # Gráfico gerado (pode ser em JPG ou PNG)
├── dados/
│   └── Dados simulados - Sprint 2.xlsx                         # XLSX com os dados simulados
├── src/
│   └── Código sem comnetários_ESP32 usando Arduino IDE         # Código principal (Arduino)
│   ├── Código comentado para ESP32 usando Arduino IDE          # Código Comentado (Arduino)
├── README.md                                                   # Documentação principal
```

---

## ✅ Status Final

Entrega concluída com êxito, com todos os requisitos da proposta Hermes Reply atendidos. Projeto funcional, documentado e pronto para apresentação.

---
