# IOT-IOB-GENERATIVE-IA-CP05

## _Visão Computacional_

Este projeto tem como objetivo aplicar e comparar duas ferramentas de Visão Computacional para tarefas de **detecção e classificação de objetos em imagens**, utilizando um conjunto de dados customizado. Foram utilizados modelos com **Roboflow** e **YOLOv8**, com base em um dataset de **latinhas de energéticos**, para simular uma aplicação prática.

## _Dataset_

Utilizamos um dataset customizado hospedado e rotulado no **Roboflow**, contendo imagens de latas de energético.

- [Clique aqui para acessar o dataset](https://universe.roboflow.com/myfiap-ut6gb/monster-bn5fz-nuvug/dataset/1)

## _Roboflow_

O modelo foi treinado diretamente na plataforma Roboflow, utilizando a opção de treinamento em nuvem. Após o treino, as métricas foram obtidas diretamente do painel.

- [Link do modelo treinado](https://app.roboflow.com/myfiap-ut6gb/monster-bn5fz-nuvug/visualize/1)

**Métricas de desempenho (extraídas da plataforma):**

- **Precisão (Precision):** 99,6%
- **Recall:** 98,1%
- **mAP@0.5:** 99,2%

> O Roboflow não permite a exportação direta do código treinado, mas oferece opção de deploy via nuvem e chamada de API.

## _YOLOv8_

O mesmo dataset foi exportado do _roboflow_ no formato YOLOv8 e utilizado para treinar um modelo local utilizando a biblioteca **Ultralytics** em Python.

**Métricas obtidas:**

- **Precisão média (mp):** 97,4%
- **Recall médio (mr):** 100,0%
- **mAP@0.5:** 99,3%

> O treinamento foi realizado localmente via notebook em Python (Google Colab), com 20 épocas e imagens de 640x640.

## _Comparativo_

| Métrica  | Roboflow (API) | YOLOv8 (local) |
| :------: | :------------: | :------------: |
| Precisão |     99,6%      |     97,4%      |
|  Recall  |     98,1%      |      100%      |
| mAP@0.5  |     99,2%      |     99,3%      |

**Observações:**

- O **YOLOv8**, apesar de exigir configuração manual, permite maior controle dos hiperparâmetros e ajustes no treinamento.
- O **Roboflow** é ideal para treinamentos rápidos e automatizados, com uma interface gráfica.
- Em testes com imagens contendo **variações de cor**, o YOLOv8 demonstrou melhor desempenho, reconhecendo objetos com maior consistência.
- Ambos os modelos apresentaram boas métricas, com **diferença de menos de 2,2% entre as principais**.

## _Melhorias_

1. **Dataset:**

   - O dataset atual possui apenas 114 imagens. Aumentar a base pode ajudar a melhorar o treinamento do modelo.
   - A presença de variações de cor e rótulos afeta a consistência da detecção.
     > _Apesar de aumentar o dataset poder não impactar diretamente nas métricas de precisão, ajuda a reduzir falsos negativos em cenários reais._

2. **Aprimoramento do modelo:**

   - Testar arquiteturas diferentes no YOLOv8 (ex: `yolov8s.pt`, `yolov8m.pt`) para avaliar impacto no desempenho.
   - Aplicar técnicas de **data augmentation** mais intensas para simular ambientes diversos (ruído, brilho, rotação).

## _Vídeo de demonstração_

- [Clique aqui para assistir ao vídeo de uso](https://www.youtube.com/watch?v=n6zei-rEhe0)

## _Ferramentas utilizadas_

- **Roboflow** – rotulagem, treinamento, exportação, deploy e API
- **YOLOv8 (Ultralytics)** – treinamento local com Python
- **Python 3.11**
