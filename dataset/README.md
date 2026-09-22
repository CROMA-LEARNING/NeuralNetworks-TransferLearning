# Dataset — Garantido x Caprichoso

```
dataset/
├── garantido/     # 59 imagens do boi Garantido (vermelho e branco)
└── caprichoso/    # 37 imagens do boi Caprichoso (azul e branco)
```

Imagens coletadas do [Wikimedia Commons](https://commons.wikimedia.org), categorias [`Category:Boi Garantido`](https://commons.wikimedia.org/wiki/Category:Boi_Garantido) e [`Category:Boi Caprichoso`](https://commons.wikimedia.org/wiki/Category:Boi_Caprichoso) (e subcategorias de torcida/bandeiras), todas sob licenças livres (CC-BY, CC-BY-SA ou domínio público). A licença e autoria de cada imagem individual estão na respectiva página de arquivo no Commons.

Querendo ampliar o dataset com fotos próprias (do Festival, de eventos locais, etc.), basta adicionar os arquivos `.jpg`/`.png` na pasta da classe correspondente — o notebook lê todas as imagens de `dataset/garantido/` e `dataset/caprichoso/` automaticamente.
