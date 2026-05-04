# Pipeline de Inteligência Artificial - Predição de Pressão Arterial

Este repositório contém o ambiente de desenvolvimento para processamento de sinais e treinamento de redes neurais para o projeto de predição de Pressão Arterial (BP Prediction). 

---

## Propósito do Projeto

Este repositório serve como a "fábrica" de modelos para o projeto principal:
**[Firmware de Predição BP](https://github.com/erickmasson/firmware_de_predicao_BP.git)**

O objetivo é transformar sinais brutos de PPG (Fotopletismografia) em um modelo matemático leve o suficiente para rodar em tempo real em um ESP32, permitindo a estimativa de pressão sistólica e diastólica sem a necessidade de braçadeiras infláveis.

---

## Requisitos e Ambiente

Para garantir a reprodutibilidade dos resultados e evitar conflitos entre versões do TensorFlow e Keras, utilize as seguintes especificações:

*   **Versão do Python:** `3.9.13` (Recomendada)
*   **Interface de Execução:** [Jupyter Notebook](https://jupyter.org/) (Extensão para VS Code recomendada).
*   **Fluxo de Trabalho:** O projeto foi estruturado em blocos sequenciais dentro do ambiente Jupyter para facilitar a leitura, depuração e visualização dos sinais em cada etapa.

---

## Como utilizar este Repositório

O pipeline está organizado de forma que cada etapa depende do sucesso da anterior. Ao abrir o arquivo `.ipynb` no VS Code, você encontrará:

### 1. Processamento e Limpeza (Etapa 1)
Onde os arquivos `.mat` brutos são filtrados e as características morfológicas são extraídas. 
*   *Nota: Requer os arquivos do dataset PulseDB localmente.*

### 2. Treinamento da MLP (Etapa 2)
A construção da rede neural utilizando TensorFlow/Keras. Aqui você poderá acompanhar as métricas de perda (Loss) e o erro médio (MAE) em mmHg através de gráficos integrados no notebook.

### 3. Otimização e Exportação (Etapa 3)
A conversão do modelo final para o formato `.tflite`. Esta etapa gera os binários necessários para a integração com o firmware C++.

---

## Integração com o Firmware
O arquivo gerado ao final do notebook (`model_data.h`) deve ser movido, ou copiar o conteúdo do arquivo, para o repositório de firmware para que a predição em hardware funcione corretamente.