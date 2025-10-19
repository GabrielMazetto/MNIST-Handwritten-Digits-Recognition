# 🚀 MLP from Scratch para MNIST

Este projeto é uma implementação de uma rede neural Multi-Layer Perceptron (MLP) do zero, utilizando principalmente a biblioteca **NumPy** para reconhecer dígitos manuscritos do conjunto de dados MNIST. O objetivo é demonstrar o funcionamento interno de uma rede neural, incluindo feed forward e backpropagation, sem o uso de frameworks de alto nível como TensorFlow ou PyTorch.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-313131?style=for-the-badge&logo=matplotlib&logoColor=white)

## 🎯 Sobre o Projeto

O foco principal é construir e treinar uma rede neural simples "do zero" (from scratch) para a tarefa de classificação de imagens. O conjunto de dados MNIST, que contém 70.000 imagens de dígitos de 0 a 9, é utilizado como base de treinamento e teste.

## 📊 Resultados

Após o treinamento de 500 épocas, o modelo alcança uma acurácia significativa (cerca de 85.5% nos dados de treino, como visto no notebook).

O notebook também inclui uma célula interativa que permite testar o modelo treinado (`trained_model.pkl`) em exemplos aleatórios do conjunto de teste, mostrando a predição e o rótulo real:

![Predição da rede neural mostrando acerto](img/image.png)

## 🤖 Arquitetura e Treinamento

O sistema foi desenvolvido seguindo os seguintes passos:

* **1. Carga e Preparação dos Dados:**
    * O conjunto de dados MNIST é carregado usando a biblioteca TensorFlow (apenas para o download do dataset).
    * Os valores dos pixels das imagens (28x28) são "achatados" (flattened) em vetores de 784 entradas.
    * Os dados de entrada são normalizados para o intervalo [0, 1], dividindo-os por 255.0, o que facilita a convergência do treinamento.

* **2. Arquitetura da Rede Neural:**
    * A rede possui uma camada de entrada com 784 neurônios (um para cada pixel).
    * Uma **camada escondida** com **10 neurônios**, utilizando a função de ativação **ReLU** (Rectified Linear Unit).
    * Uma **camada de saída** com **10 neurônios**, correspondendo aos dígitos de 0 a 9, utilizando a função de ativação **Softmax** para gerar uma distribuição de probabilidade.

* **3. Processo de Treinamento (do Zero):**
    * **Feed Forward:** As entradas são propagadas pela rede, multiplicadas pelos pesos e somadas aos *bias* de cada camada, até gerar a previsão na saída.
    * **Backpropagation:** O erro entre a previsão (saída do Softmax) e o rótulo real (convertido para *one-hot encoding*) é calculado. Esse erro é propagado de volta pela rede para calcular os gradientes dos pesos e *bias*.
    * **Descida do Gradiente:** Os pesos e *bias* da rede são ajustados em pequenas etapas (controladas pela taxa de aprendizado, `alpha`) na direção oposta do gradiente, minimizando o erro ao longo de 500 iterações (épocas).

* **4. Serialização do Modelo:**
    * Após o treinamento, os pesos (Wh, Ws) e bias (bh, bs) da rede são salvos em um arquivo `trained_model.pkl` usando a biblioteca `pickle`. Isso permite que o modelo seja carregado e reutilizado sem necessidade de novo treinamento.

## 🛠️ Tecnologias Utilizadas

* **Python**
* **NumPy:** Utilizado para todas as operações de matrizes, implementação do feed-forward, backpropagation e funções de ativação.
* **Matplotlib:** Para visualização das imagens dos dígitos.
* **TensorFlow (Keras):** Utilizado exclusivamente para facilitar o download e carregamento do *dataset* MNIST.
* **IPyWidgets:** Para criar o botão interativo de demonstração no Jupyter.
* **Pickle:** Para salvar e carregar o modelo treinado.
