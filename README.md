# ACA0430: Trabalho 1, notebooks de apoio

**ACA0430 — Meteorologia Sinótica e Aplicações à Oceanografia (IAG/USP), 2º semestre de 2026**

Três notebooks de exemplo, um por tema, para montar as figuras de base do estudo de caso. Cada um baixa só o recorte necessário do **ERA5** (atmosfera) e do **GLORYS12 / WAVERYS** (oceano e ondas, Copernicus Marine) direto de armazenamentos **Zarr na nuvem**, sem baixar arquivos inteiros, e roda no **Google Colab** (plano gratuito).

Os notebooks são **um ponto de partida**: mude as datas, a região e acrescente outros dados.

| Tema | Caso de exemplo | Abrir |
|---|---|---|
| 1. Ciclone → maré de tempestade e ondas | Ressaca de Santos, 15–23/08/2016 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cbgramcianinov/aca0430-trabalho1/blob/main/T1_tema1_mare_tempestade_ondas.ipynb) |
| 2. Vento favorável → ressurgência costeira | Cabo Frio, 08–26/01/2016 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cbgramcianinov/aca0430-trabalho1/blob/main/T1_tema2_ressurgencia_costeira.ipynb) |
| 3. Alta semipermanente (ASAS) → fluxos ar-mar | Verão (jan–fev) de 2014 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cbgramcianinov/aca0430-trabalho1/blob/main/T1_tema3_alta_semipermanente.ipynb) |

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

## Executar no seu computador

Os notebooks também rodam fora do Colab. O arquivo [`environment.yml`](environment.yml) cria um ambiente conda com todos os pacotes necessários:

```bash
conda env create -f environment.yml
conda activate aca0430
```

Uma vez só, faça o login no Copernicus Marine. O usuário e a senha ficam salvos no seu computador, não no notebook:

```bash
copernicusmarine login
```

Depois abra o notebook com `jupyter lab` e rode normalmente. Fora do Colab:

- a célula de instalação é pulada automaticamente;
- os dados e as figuras são salvos em `saida/dados/` e `saida/figuras/`, na pasta onde o notebook está;
- a célula de credenciais usa o login salvo pelo comando acima.

## Dados

- **ERA5** (Hersbach et al., 2020), via [ARCO-ERA5](https://github.com/google-research/arco-era5) no Google Cloud: horário, 0,25°.
- **GLORYS12** (Lellouche et al., 2021), produto CMEMS `GLOBAL_MULTIYEAR_PHY_001_030`: diário e mensal, 1/12°.
- **WAVERYS** (Law-Chune et al., 2021), produto CMEMS `GLOBAL_MULTIYEAR_WAV_001_032`: 3-horário, 0,2°.

Cada notebook traz, no final, um texto-base para a seção de **Métodos** e a lista de referências.

## Sobre

Este material foi elaborado como parte da disciplina **ACA0430 — Meteorologia Sinótica e Aplicações à Oceanografia**, oferecida pelo Instituto de Astronomia, Geofísica e Ciências Atmosféricas (IAG) da Universidade de São Paulo (USP).

- Docente responsável: Prof. Dr. Ricardo de Camargo
- Colaboradora: Dra. Carolina Barnez Gramcianinov

## Uso de inteligência artificial

Os notebooks deste repositório foram desenvolvidos com auxílio de uma ferramenta de inteligência artificial (Claude Code, da Anthropic), sob orientação e revisão da equipe da disciplina.
