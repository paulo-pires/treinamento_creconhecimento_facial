# 🧑‍💻 Sistema de Reconhecimento Facial com TensorFlow e MTCNN

Este projeto apresenta uma solução completa de **Visão Computacional** desenvolvida em Python para detectar e reconhecer faces em imagens. O sistema foi criado para rodar no **Google Colab** e utiliza técnicas modernas de *Deep Learning*, incluindo o uso de redes pré-treinadas (Transfer Learning) para classificação.

 ## 🎯 Objetivo do Desafio

O projeto foi desenvolvido como parte de um desafio técnico de visão computacional, com os seguintes requisitos:
1.  **Detecção Facial:** Implementar um algoritmo capaz de localizar rostos em uma imagem.
2.  **Classificação Facial:** Criar e treinar uma rede neural para identificar a quem pertence cada rosto detectado.
3.  **Integração:** Unir os dois estágios em um pipeline funcional que recebe uma imagem e desenha os nomes e caixas delimitadoras.

## 🛠️ Tecnologias Utilizadas

* **Python 3.x**
* **TensorFlow / Keras:** Para construção e treinamento da rede neural de classificação.
* **MTCNN (Multi-task Cascaded Convolutional Networks):** Para a etapa de detecção de faces (estado da arte em precisão).
* **OpenCV:** Para manipulação de imagens e desenho das anotações.
* **Matplotlib:** Para visualização dos resultados.
* **MobileNetV2:** Arquitetura de rede utilizada como base para o Transfer Learning (leve e eficiente).

## ⚙️ Como Funciona o Pipeline

O sistema opera em 4 etapas principais, todas automatizadas no notebook:

### 1. Coleta de Dados Automática
O script clona automaticamente um dataset público do GitHub (`Celebrity-Face-Recognition`) contendo imagens de 5 personalidades (Messi, Federer, Serena Williams, etc.), eliminando a necessidade de upload manual de fotos.

### 2. Pré-processamento e Recorte (Face Extraction)
* Utiliza a rede **MTCNN** para escanear todas as fotos do dataset.
* Identifica a região exata do rosto.
* Recorta e redimensiona a face para **224x224 pixels**.
* Salva as faces processadas em uma nova estrutura de pastas, pronta para o treino.

### 3. Treinamento com Transfer Learning
* Utiliza a rede **MobileNetV2** pré-treinada no *ImageNet*.
* Substitui a camada de saída original por uma nova camada densa com ativação `Softmax` para as 5 classes do nosso dataset.
* Aplica **Data Augmentation** (rotação, zoom e espelhamento) durante o treino para tornar o modelo mais robusto.
* Congela os pesos da base para aproveitar o conhecimento prévio da rede.

### 4. Inferência (Teste Final)
* Baixa uma imagem aleatória da internet (ex: foto do Messi na Copa).
* Detecta todos os rostos na imagem usando MTCNN.
* Passa cada rosto detectado pelo classificador treinado.
* Exibe a imagem final com o nome da pessoa e a porcentagem de confiança.

## 🚀 Como Executar

Este projeto é "Plug-and-Play" no Google Colab.

1.  Abra o arquivo `.ipynb` no Google Colab.
2.  No menu superior, vá em **Ambiente de execução > Alterar o tipo de ambiente de execução** e selecione **GPU** (para treinar mais rápido).
3.  Execute todas as células sequencialmente.
    * O script instalará as dependências, baixará os dados, treinará o modelo e mostrará o resultado final automaticamente.

## 📊 Resultados Esperados

Ao final da execução, o sistema exibirá a imagem de teste com um retângulo verde ao redor do rosto e o nome da personalidade identificada, demonstrando que tanto a detecção quanto a classificação foram bem-sucedidas.

---
*Desenvolvido como parte do desafio de projeto de Visão Computacional.*
