# Dataset — Garantido x Caprichoso

```
dataset/
├── garantido/     # 118 imagens do boi Garantido (vermelho e branco)
└── caprichoso/    # 107 imagens do boi Caprichoso (azul e branco)
```

Imagens coletadas de duas fontes com licença livre:

- [Wikimedia Commons](https://commons.wikimedia.org), categorias [`Category:Boi Garantido`](https://commons.wikimedia.org/wiki/Category:Boi_Garantido), [`Category:Boi Caprichoso`](https://commons.wikimedia.org/wiki/Category:Boi_Caprichoso) e as categorias por ano de [`Category:Festival de Parintins by year`](https://commons.wikimedia.org/wiki/Category:Festival_de_Parintins_by_year) — licenças CC-BY, CC-BY-SA ou domínio público.
- [Openverse](https://openverse.org) → Flickr, série oficial de fotos do Festival pela Assembleia Legislativa do Amazonas (fotógrafo Alberto César Araújo/Aleam), marcadas como domínio público (PDM).

Cada imagem foi revisada individualmente para garantir que mostra de fato o boi/torcida/símbolo do time correto (sem contaminação cruzada entre as duas classes e sem fotos genéricas do festival sem cor de time identificável). A licença e autoria de cada imagem original estão na respectiva página de arquivo na fonte.

Querendo ampliar o dataset com fotos próprias (do Festival, de eventos locais, etc.), basta adicionar os arquivos `.jpg`/`.png` na pasta da classe correspondente — o notebook lê todas as imagens de `dataset/garantido/` e `dataset/caprichoso/` automaticamente.
