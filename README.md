# 🐂 Transfer Learning: Garantido x Caprichoso

Projeto do desafio de código da [DIO](https://www.dio.me) sobre **Transfer Learning** em Deep Learning. Em vez do clássico exemplo de gatos e cachorros, apliquei o método a um tema de cultura popular brasileira: o **Festival Folclórico de Parintins (AM)**, disputa entre os bois-bumbás **Garantido** (vermelho e branco) e **Caprichoso** (azul e branco).

## O desafio

Aplicar Transfer Learning em uma rede de Deep Learning, em Python, no Google Colab, documentando o processo em um repositório público. Base de partida: o notebook de referência da DIO (`transfer-learning.ipynb`, classificação sobre o Caltech-101), adaptado aqui para uma classificação **binária** com dataset próprio.

## Sobre o tema

Garantido e Caprichoso são os dois bois-bumbás que disputam, há mais de um século, o Festival de Parintins — um dos maiores eventos culturais do Brasil. Cada agremiação tem cores, símbolos e torcida (torcedores "encantados" pelo boi) muito característicos, o que os torna um bom par de classes visualmente distintas para um classificador de imagens.

| | Garantido | Caprichoso |
|---|---|---|
| Cores | Vermelho e branco | Azul e branco |
| Símbolo | Boi vermelho | Boi azul |

## O que é Transfer Learning

Em vez de treinar uma rede neural do zero — o que exige muitos dados e poder computacional — reaproveitamos uma rede já treinada em um grande dataset (a **VGG16**, treinada na ImageNet) como extratora de features. Congelamos as camadas convolucionais (que já aprenderam a reconhecer bordas, texturas e formas genéricas) e treinamos apenas uma nova camada de classificação final, adaptada às nossas 2 classes. Isso permite bons resultados mesmo com poucas centenas de imagens.

O notebook compara duas abordagens:
1. **Baseline**: uma CNN simples treinada do zero.
2. **Transfer Learning**: VGG16 pré-treinada + nova camada de classificação (Garantido / Caprichoso).

## Estrutura do repositório

```
.
├── transfer_learning_garantido_caprichoso.ipynb   # notebook principal (Colab)
├── dataset/
│   ├── garantido/       # imagens do boi Garantido (não versionadas)
│   ├── caprichoso/      # imagens do boi Caprichoso (não versionadas)
│   └── README.md        # como montar o dataset
└── images/               # capturas de tela do processo/resultados
```

## Como executar

1. Abra `transfer_learning_garantido_caprichoso.ipynb` no [Google Colab](https://colab.research.google.com/).
2. Monte seu dataset seguindo [`dataset/README.md`](dataset/README.md) (Google Drive, upload de zip, ou clone deste repo).
3. Execute as células em ordem: baseline → VGG16 congelada → treino → avaliação → predição.

## Resultados

_A preencher após o treino:_

| Modelo | Acurácia (teste) |
|---|---|
| Baseline (do zero) | — |
| Transfer Learning (VGG16) | — |

## Aprendizados

- Transfer learning reduz drasticamente a quantidade de dados necessária para um classificador de imagens ter boa performance.
- Congelar as camadas convolucionais e treinar só a camada final é rápido e já entrega ganhos expressivos sobre o baseline.
- Um bom dataset (variado, bem rotulado) importa mais que o volume bruto de imagens.

## Créditos

- Notebook base: material de apoio do desafio "Transfer Learning" da formação em Deep Learning — [DIO](https://www.dio.me).
