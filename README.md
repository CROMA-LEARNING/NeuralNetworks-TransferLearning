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
│   ├── garantido/       # 118 imagens do boi Garantido
│   ├── caprichoso/      # 107 imagens do boi Caprichoso
│   └── README.md        # fonte e licença das imagens
└── results/              # gráficos e métricas gerados pelo notebook (600 DPI)
```

## Como executar

1. Abra `transfer_learning_garantido_caprichoso.ipynb` no [Google Colab](https://colab.research.google.com/).
2. Clone este repositório (o dataset já vem incluso) ou monte o seu próprio seguindo [`dataset/README.md`](dataset/README.md).
3. Execute as células em ordem: baseline → VGG16 congelada → treino → avaliação → predição.

## Resultados

Treino final com as 225 imagens (split estratificado 70/15/15 → 35 imagens de teste), 40 épocas com early stopping, class weights e data augmentation leve no treino.

| Modelo | Acurácia | Precisão | Recall (sensibilidade) | F1-score |
|---|---|---|---|---|
| Baseline (do zero) | 0.914 | 0.917 | 0.911 | 0.913 |
| Transfer Learning (VGG16) | 0.771 | 0.773 | 0.775 | 0.771 |

Surpresa: o **baseline treinado do zero superou o Transfer Learning** nesse caso. A explicação mais provável é que a tarefa é dominada por um sinal de **cor** bem forte (vermelho x azul), que uma CNN rasa aprende diretamente dos pixels sem esforço — enquanto a VGG16, pré-treinada na ImageNet para reconhecer formas e texturas de objetos, com apenas a camada final destravada (feature extraction puro), não se readapta tão bem a um sinal dominado por cor. Fine-tuning das últimas camadas convolucionais da VGG16 (em vez de mantê-las 100% congeladas) é o próximo passo natural para tentar fechar essa diferença.

Gráficos completos (curvas de loss/acurácia, matriz de confusão, curva ROC, comparação de métricas) em [`results/`](results/), gerados a 600 DPI.

## Aprendizados

- Transfer learning nem sempre vence um baseline simples — depende de quão bem as features da rede pré-treinada (ImageNet: formas, texturas, objetos) se alinham com o sinal que realmente separa as classes do seu problema. Aqui o sinal é cor, e uma CNN rasa aprendeu isso mais rápido que a VGG16 com feature extraction puro.
- Curadoria de dataset importa mais que o volume bruto: boa parte do trabalho foi remover imagens contaminadas (com os dois bois na mesma foto, ou sem nenhum boi visível) mineradas de fontes públicas.
- Dataset pequeno e um pouco desbalanceado (118 x 107) pede split estratificado, `class_weight` e augmentation leve — sem isso as métricas de validação ficam bem instáveis entre épocas.

## Créditos

- Notebook base: material de apoio do desafio "Transfer Learning" da formação em Deep Learning — [DIO](https://www.dio.me).
- Imagens: [Wikimedia Commons](https://commons.wikimedia.org) e [Openverse](https://openverse.org)/Flickr (Aleam) — ver [`dataset/README.md`](dataset/README.md) para fontes e licenças.
