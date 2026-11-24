# Análise de vibração de drones com hélices saudáveis e defeituosas

Código da análise dos sinais e da extração de características do projeto de CIN0020 Sinais e Sistemas (Grupo 11: Carolina Santiago de Medeiros, Karolyne Bezerra Rocha e Milla Rwana de Araújo Silva).

## Conteúdo da pasta

```
main.ipynb                     notebook com todo o pipeline e os textos explicativos
caracteristicas_janelas.csv    tabela de características, uma linha por janela de 1 s
output/
  figuras/                     as sete figuras usadas no relatório
  tabelas/                     tabelas auxiliares (registros, resumos, separação d, correlações, rotação)
requirements.txt               dependências
DronePropB Ground Testing Dataset/   dados (não versionados, ver abaixo)
```

O `main.ipynb` vai da leitura dos registros até a extração e a análise das características: seleção e verificação dos dados, janelamento, análise no tempo, FFT e características espectrais, resolução espectral, aliasing, comparação entre domínios e investigação adicional. A tabela `caracteristicas_janelas.csv` e todo o conteúdo de `output/` são gerados pelo próprio notebook.

## Como obter os dados

O dataset é o DronePropB (Mendeley Data, DOI [10.17632/xkvfjmm8zg.1](https://doi.org/10.17632/xkvfjmm8zg.1)), com cerca de 550 MB.

1. Na página do dataset, use *Download All* e descompacte o arquivo.
2. Copie a pasta `DronePropB Ground Testing Dataset`, a que contém os 111 arquivos `.mat`, para esta pasta, ao lado do `main.ipynb`.

A pasta do dataset está no `.gitignore` e não faz parte do repositório.

Arquivos usados na análise: a configuração C1 nas velocidades SP1 a SP3, com os 9 registros saudáveis `F0_SV0_SP{1,2,3}_C1_R{1,2,3}.mat` e os 27 com defeito `F{1,2,3}_SV{1,2,3}_SP{1,2,3}_C1.mat`. Os registros equivalentes da configuração C2 são usados só na verificação dos dados e na checagem da seção 3.6.

## Como executar

Com Python 3.10 ou mais recente:

```
python -m pip install -r requirements.txt
jupyter notebook main.ipynb
```

No Jupyter, execute todas as células (*Run All*). A execução completa leva cerca de um minuto e gera `caracteristicas_janelas.csv` e as pastas `output/figuras/` e `output/tabelas/`. O notebook foi testado com Python 3.11, numpy 1.24, pandas 1.5, matplotlib 3.7 e scipy 1.10.

O notebook também roda no Google Colab. Nesse caso, a primeira célula de configuração monta o Google Drive, e a variável `PASTA` precisa apontar para a pasta do dataset no Drive.
