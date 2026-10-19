# ACA0430: Trabalho 1, notebooks de apoio

**ACA0430 — Meteorologia Sinótica e Aplicações à Oceanografia (IAG/USP), 2º semestre de 2026**

Três notebooks de exemplo, um por tema, para montar as figuras de base do estudo de caso. Cada um baixa só o recorte necessário do **ERA5** (atmosfera) e do **GLORYS12 / WAVERYS** (oceano e ondas, Copernicus Marine) direto de armazenamentos **Zarr na nuvem**, sem baixar arquivos inteiros, e roda no **Google Colab** (plano gratuito).

Os notebooks são **um ponto de partida**: mude as datas, a região e acrescente outros dados.

| Tema | Caso de exemplo | Abrir |
|---|---|---|
| 1. Ciclone → maré de tempestade e ondas | Ressaca de Santos, 18–25/08/2016 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cgramcianinov/aca0430-trabalho1/blob/main/T1_tema1_mare_tempestade_ondas.ipynb) |
| 2. Vento favorável → ressurgência costeira | Cabo Frio, 08–26/01/2016 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cgramcianinov/aca0430-trabalho1/blob/main/T1_tema2_ressurgencia_costeira.ipynb) |
| 3. Alta semipermanente (ASAS) → fluxos ar-mar | Verão (jan–fev) de 2014 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cgramcianinov/aca0430-trabalho1/blob/main/T1_tema3_alta_semipermanente.ipynb) |

Exemplos das figuras que cada notebook gera estão em [`exemplos_figuras/`](exemplos_figuras/).

## Como usar

1. **Crie uma conta gratuita no Copernicus Marine:** https://data.marine.copernicus.eu/register. O ERA5 é público e não precisa de conta.
2. **Clique no botão "Open in Colab"** do seu tema.
3. **Salve uma cópia no seu Drive:** *Arquivo → Salvar uma cópia no Drive*. Sem isso, suas alterações se perdem.
4. **Cadastre suas credenciais como segredos do Colab:** clique no ícone de chave na barra lateral e crie
   - `COPERNICUSMARINE_SERVICE_USERNAME` com o seu usuário,
   - `COPERNICUSMARINE_SERVICE_PASSWORD` com a sua senha,

   e ative "Acesso ao notebook" nos dois. **Nunca escreva a senha no notebook.**
5. Altere só a **célula de parâmetros** (marcada com `# >>> ALUNO:`) e rode tudo: *Ambiente de execução → Executar tudo*.

Tempo aproximado de execução com os parâmetros padrão: 5–10 min por notebook. O Tema 3 é o mais lento, por causa da climatologia do ERA5.

## Dados

- **ERA5** (Hersbach et al., 2020), via [ARCO-ERA5](https://github.com/google-research/arco-era5) no Google Cloud: horário, 0,25°.
- **GLORYS12** (Lellouche et al., 2021), produto CMEMS `GLOBAL_MULTIYEAR_PHY_001_030`: diário e mensal, 1/12°.
- **WAVERYS** (Law-Chune et al., 2021), produto CMEMS `GLOBAL_MULTIYEAR_WAV_001_032`: 3-horário, 0,2°.

Cada notebook traz, no final, um texto-base para a seção de **Métodos** e a lista de referências.

## Para a docente: regenerar os notebooks

Os notebooks são gerados por scripts em [`dev/`](dev/) (`build_t1.py`, `build_t2.py`, `build_t3.py`, com as células comuns em `comum.py`). Para alterar um notebook, edite o script correspondente e rode:

```bash
python dev/build_t1.py              # gera o .ipynb na raiz
python dev/executa.py T1_tema1_mare_tempestade_ondas.ipynb   # executa e salva em dev/executados/
python dev/finaliza.py              # limpa as saídas, valida e copia as figuras para exemplos_figuras/
```

`executa.py` usa um kernel Jupyter chamado `to_plot_aca`; ajuste o nome para o seu ambiente.
