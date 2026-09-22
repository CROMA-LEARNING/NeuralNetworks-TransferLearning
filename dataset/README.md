# Dataset — Garantido x Caprichoso

As imagens não são versionadas neste repositório (direitos de imagem de terceiros). Organize seu dataset localmente/no Drive seguindo esta estrutura antes de rodar o notebook:

```
dataset/
├── garantido/     # fotos do boi Garantido (vermelho e branco)
└── caprichoso/    # fotos do boi Caprichoso (azul e branco)
```

Recomendações:
- Pelo menos ~100–150 imagens por classe (mais = melhor, transfer learning tolera datasets pequenos).
- Formatos aceitos: `.jpg`, `.jpeg`, `.png`.
- Prefira fotos variadas: boi estilizado, galera nas arquibancadas com as cores do time, bandeiras, itens/alegorias — sempre respeitando direitos autorais de quem tirou a foto.
- Fontes possíveis: fotos próprias tiradas no Festival de Parintins, perfis oficiais das agremiações, bancos de imagem com licença livre.

O notebook (`transfer_learning_garantido_caprichoso.ipynb`) traz 3 formas de carregar o dataset no Colab: montar o Google Drive, subir um `dataset.zip`, ou clonar este repositório.
