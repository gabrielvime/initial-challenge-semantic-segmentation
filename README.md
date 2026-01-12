# Desafio de Programação: Classificação de Pistas de Pouso em Imagens de Satélite

Bem-vindo(a) ao desafio de programação! O objetivo é construir uma aplicação capaz de identificar e classificar pistas de pouso em uma imagem de satélite Sentinel-2, com foco na região do sudoeste paraense. Você tem a liberdade de escolher a abordagem tecnológica, seja utilizando o Google Earth Engine (GEE) para processamento em nuvem ou baixando a imagem para processamento local.

---

## O Desafio

Seu projeto deve abordar os seguintes pontos:

1.  **Acesso à Imagem Sentinel-2:** Obtenha uma imagem de satélite **Sentinel-2** cobrindo a região do **sudoeste paraense**. Você pode definir as coordenadas exatas ou usar um polígono que represente a área de interesse. A coleta dos dados pode ser feita através da API do Google Earth Engine (`ee`), da biblioteca `xee` (uma extensão do GEE para `xarray`) ou por meio de download direto.

2.  **Pré-processamento (Opcional, mas recomendado):** Se achar necessário, aplique técnicas de pré-processamento na imagem para melhorar a qualidade e facilitar a classificação. Isso pode incluir a remoção de nuvens, correção atmosférica (se não estiver pré-aplicada) ou a criação de índices de vegetação.

3.  **Classificação de Pistas de Pouso:** Desenvolva um algoritmo ou modelo para classificar as áreas que correspondem a pistas de pouso na imagem. A escolha da metodologia é sua desde que seja um segmentador semantico como as redes em forma de U ou até mesmo Transformers como o SwinTransformer.

4.  **Visualização e/ou Exportação:** Apresente os resultados da sua classificação de forma clara. Isso pode ser uma visualização interativa (no GEE ou em uma biblioteca como `folium`), ou a exportação dos resultados para um formato geoespacial padrão, como **GeoJSON** ou **GeoTIFF**, com as áreas classificadas.

---

## Requisitos Técnicos

Você pode usar as seguintes ferramentas, mas sinta-se à vontade para explorar outras:

* **Linguagem de Programação:** **Python** é altamente recomendado devido à vasta gama de bibliotecas geoespaciais e de aprendizado de máquina.
* **Acesso a Dados:**
    * **Google Earth Engine (GEE):** Para processamento em nuvem. Use a biblioteca `earthengine-api` ou `xee` para uma interface mais intuitiva.
* **Bibliotecas Sugeridas:**
    * `earthengine-api`
    * `xee` (para integrar o GEE com `xarray`)
    * `rasterio` e `fiona` (para manipulação de dados geoespaciais)
    * `scikit-learn` (para modelos de Machine Learning)
    * `matplotlib` ou `folium` (para visualização)
    * `geopandas` (para análise de dados vetoriais)

---

## Entrega do Projeto

Seu projeto deve ser entregue com os seguintes componentes:

* **Código-fonte:** Todo o código utilizado (scripts Python, notebooks Jupyter, etc.).
* **Instruções de Execução:** Um guia detalhado explicando como configurar o ambiente e executar seu código.
* **Resultados:** Uma amostra dos resultados gerados (imagens, mapas, arquivos). Se a visualização for interativa, inclua uma captura de tela ou um GIF.
* **Documentação:** Um texto breve (pode ser no próprio README) descrevendo a sua abordagem, a metodologia de classificação escolhida, os desafios encontrados e como você os superou.

---

## Critérios de Avaliação

O projeto será avaliado com base em:

* **Funcionalidade:** A aplicação executa as tarefas propostas de forma correta e completa.
* **Qualidade do Código:** Organização, clareza, modularidade e uso de boas práticas de programação.
* **Escolha da Abordagem:** A justificativa para as ferramentas e métodos utilizados é clara e bem fundamentada.
* **Documentação:** As instruções e explicações fornecidas são fáceis de entender.

---

## Como Começar

1. **Faça um fork deste repositório.**

2. **Clone o repositório** para sua máquina local.

3. **Crie um ambiente virtual** (recomendado) e instale as dependências necessárias.

4. **Configure o acesso ao Google Earth Engine** (se for utilizá-lo). Siga as instruções oficiais do GEE para autenticação.

5. **Comece a codificar!**

Boa sorte e divirta-se com o desafio!



# Projeto

## Instruções de Execução

Este projeto está estruturado em um Python Notebook, para utilizá-lo basta seguir os simples passos abaixo. Após isso, tudo será feito de forma automática: configuração das funções e modelo, treinamento, gráficos de estatísticas, testes e execução no sudoeste do Pará. 

1. Baixe o [dataset](https://www.google.com/url?q=https%3A%2F%2Fdrive.google.com%2Ffile%2Fd%2F1B3ag5kWrjg6aTiYQ2izRlwb-vehwFpqi%2Fview%3Fusp%3Dsharing) disponibilizado e extraia-o no seu [Google Drive](https://drive.google.com), não esqueça de verificar o checksum por segurança. Após, altere o valor da variável ```DATA_DIR``` (na célula ```CONFIGURAR GOOGLE DRIVE```) com o diretório correto de onde você extraiu o dataset.

2. Acesse o [API Console](https://console.developers.google.com/) para copiar seu **Project ID** do Google Cloud. Na célula ```Autenticar GEE```, altere ```'seu-projeto-123456'``` com o seu **Project ID**. Em caso de dúvidas, acesse a documentação aficial [aqui](https://support.google.com/googleapi/answer/7014113).

3. Opcional: Por padrão o Colab utiliza aceleração por CPU, porém, treinar modelos com CPU é extremamente demorado. Recomenda-se alterar para aceleração por GPU. O Google disponibiliza GPUs T4 gratuitamente (apesar de limitado).
Para alterar, clique em ```Runtime > Change runtime type``` e selecione ```T4 GPU```, ou outra caso tenha algum plano premium.

4. Clique em ```Run all```, confirme a permissão de acesso ao seu Google Drive, depois confirme suas credenciais do Google Cloud. Após isso, o projeto será executado sem precisar de mais nenhuma intervenção.



**Dataset**: [S2_dataset.zip](https://www.google.com/url?q=https%3A%2F%2Fdrive.google.com%2Ffile%2Fd%2F1B3ag5kWrjg6aTiYQ2izRlwb-vehwFpqi%2Fview%3Fusp%3Dsharing)

**Checksum**: 944964916e4e01d7b8946d3bb1c9b0680806b06319a92a8c25666bb4257fc538

### Observações:
-  Para executar este projeto recomenda-se utilizar o [Google Colab](https://colab.research.google.com/). Você pode copiar o link deste repositório ou fazer um fork para sua conta e carregá-lo na página inicial da plataforma.

- Este projeto não está configurado para utilizar TPUs. Saiba mais clicando [aqui](https://docs.cloud.google.com/tpu/docs/intro-to-tpu).

- Também é possível executa-lo localmente instalando as bibliotecas necessárias e alterando o valor de ```DATA_DIR``` para seu diretório local.

- Apesar de não ser recomendado, é possível pular a parte de treino e utilizar o arquivo de modelo já treinado que está disponível no arquivo do dataset.

## Abstract

## Abordagem

Este projeto foi produzido partindo do princípio de que pistas de pouso são difíceis de serem detectadas em meio a toda a vegetação amazônica, portando, foram feitas buscas acadêmicas e pesquisas na internet a respeito do assunto, buscando melhor compreensão do tema para nortear decisões e estruturar metodologias.

\
A priori, foi feito um estudo sobre os dados fornecidos pelo satélite Sentinel-2, buscando informações sobre bandas espectrais, resoluções espaciais e frequência, onde se chegou a conclusão de utilizar o período de imagens de 01 de agosto de 2024 à 30 de setembro de 2024, por se tratar do período de seca da região amazônica e por conseguinte menor ocorrência de nuvens; as bandas de RGB foram selecionadas por serem o padrão geral para visualização de imagens; a banda de Near-Infrared (NIR) foi selecionada devido ao contraste intenso que ela cria entre a vegetação saudável e as pistas que, em sua maioria, são solo exposto; já as bandas de Short-Wave Infrared (SWIR) foram escolhidas devido ao seu comportamento com a umidade, a vegetação absorve quase toda a frequência enquanto pistas de solo batido e, em especial, asfalto as reflete, isso faz com que as pistas brilhem na imagem, especialmente útil para o modelo não confundir com sombras de nuvens, fumaça e rios; o Normalized Difference Vegetation Index (NDVI) mede a saúde das plantas, portanto, valores muitos baixos indicam intervenção humana e probabilidade de pista; por outro lado, o Normalized Difference Built-Up Index (NDBI) foi criado para mapear áreas urbanas destacando superfície impermeável ou solo compactado, ajudando a separar áreas de terra natural da terra batida da pista.

\
Foi feita uma pesquisa para buscar mapeamentos anteriores de pistas de pouso no Brasil, de preferência na região amazônica, para servir de referência para marcar manualmente dados de treino, então, com as pistas e áreas de não pistas devidamente marcadas, foi produzido um dataset simples e pequeno porém útil e efetivo para alimentar o modelo.

\
O modelo escolhido para o projeto foi uma rede neural convolucional U-Net MiT-B2, o qual utiliza a arquitetura Transformer (SegFormer),uma poderosa arquitetura que consegue utilizar o contexto do objeto em foco através de seus mecanismos de self-attention, tornando especialmente útil para o objetivo.

\
Com o dataset e o modelo definidos, o treinamento foi iniciado e mesmo com poucos dados para treinamento e pouca informação para analisar, o modelo conseguiu fazer inferências com bons resultados.

## Metodologia

### Preparação dos dados

Para preparar o dataset de treino, utilizou-se da plataforma Code Editor do Google Earth Engine para marcar manualmente polígonos de pistas (positivos) e de não pistas (negativos). Com o auxílio de um mapa interativo¹, foram definidos 51 polígonos positivos e 102 polígonos negativos (proporção 1:2, totalizando 153 polígonos) em toda a região amazônica do Brasil, variando desde aeroportos internacionais (como os de Belém e de Manaus), aeroportos simples (como o de Parintins) à pistas clandestinas e improvisadas em regiões remotas. Para os negativos, foram escolhidas rodovias, portos, clareiras, estradas de terra, elementos os quais poderiam confundir o modelo como pistas por sua geometria similar. Tais polígonos foram salvos como ```ee.FeatureCollection``` com metadados de ```CONFIDENCE```, ```DATE```, ```ID``` e ```SURFACE```  com as seguintes informações:

- ```CONFIDENCE```: Nível de cconfiança dos dados.
- ```DATE```: Intervalo da data os quais os dados foram obtidos.
- ```ID```: Identificador único da pista.
- ```SURFACE```: Tipo de superfície, 1 para pistas de asfalto e 0 para pistas de terra e ademais.

\
Após a marcação dos polígonos, foi carregado o dataset **Harmonized Sentinel-2 MSI: MultiSpectral Instrument, Level-2A (SR)** ² com a máscara de filtro de nuvens disponibilizado pela plataforma **Earth Engine Data Catalog** ². Criou-se um composite com as bandas RGB (B4, B3, B2), NIR (B8), SWIR (B11, B12) nas quais foi aplicado um algorítimo de reprojeção bilinear para 10m, uma vez que as imagens destas bandas está em 20m, e por fim, calculou-se os valores de NDVI e NDBI para adcionar ao composite.

\
Para cada polígono, foi criado um patch normalizado de 256px centrado no próprio polígono com uma máscara binária (nomeada ```'runway_mask'```) de valor ```1``` apenas nos pixeis de pista e ```0``` nos restantes, obviamente patches negativos possuem apenas valor ```0``` em toda a máscara, a qual foi então empilhada nas bandas do patch.

\
Desta forma, cada patch foi exportado com as seguintes características:
 - **9 bandas**: Vermelho (B4), Verde (B3), Azul (B2), SWIR (B11), SWIR (B12), NDVI, NDBI, 'runway_mask', estritamente nesta ordem;
 - **Dimensões**: 256px de largura, 256px de altura, estritamente;
 - **Escala**: estritamente 10m;
 - **Formato**: GeoTIFF;
 - **Metadados**: CONFIDENCE, DATE, ID, SURFACE;
 - **Nome do arquivo**: Arquivos de pistas foram salvos com o nome genérico ```'patch_runway_{ID}.tif```, enquanto os negativos com ```'patch_negative_{ID}.tif```, para facilitar a diferenciação em testes e debugs.

 Todas estas informações foram salvas no arquivo ```'patches_metadata.csv'``` juntamente com as coordenadas.

\
Por fim, os arquivos foram divididos em treino, validação e teste com a seguinte proporção:
- ~70% Treino: 35 positivos, 71 negativos, totalizando 106 patches;
- ~15% Validação: 8 positivos, 15 negativos, totalizando 23 patches;
- ~15% Teste: 8 positivos, 16 negativos, totalizando 24 patches;

Estas informações de divisão foram salvas no arqquivos ```split_info.json```, onde está o nome de cada arquivo e onde o mesmo foi alocado.

### Definição do modelo e ambiente de treinamento

 O mit_b2 faz parte da família Mix Transformer (MiT), que é o encoder da arquitetura SegFormer. No PyTorch, o mesmo é implementado através da biblioteca ```segmentation_models_pytorch``` (SMP), ele substitui as tradicionais ResNets com uma abordagem baseada em Vision Transformers (ViT). Este framework foi escolhido por ser facilmente "debugavel" e muito bem estabelecido, com ampla documentação e utilização na área acadêmica.

Para a função de perda, foi escolhida a Binary-Cross Entropy (BCE) com camada Sigmoid. A camada Sigmoid transforma em probabilidades valores numéricos gerados pelo modelo, podendo ajustar o threshold para evitar falsos positivos ou diminuir a cautela do modelo de acordo com a necessidade. O BCE é uma função logarítmica que gera penalidades muito altas para erros, especialmente útil no contexto deste projeto, onde os pixeis de uma pista geralmente ocupam em torno de 1% da imagem.

O otimizador escolhido foi o Adam por conta de sua velocidade adaptativa e de seu *Momentum*, onde o mesmo calcula taxas de aprendizado individuais para cada peso do modelo e leva em consideração erros anteriores para não ficar preso em mínimos locais.

Por fim, função Dice Loss foi usada para validação por se tratar de uma função tida como "padrão" para modelos de visão computacional.

## Resultados

## Desafios

## Conclusões

## Trabalhos futuros

## Referencias

- Xie, E., Wang, W., Yu, Z., Anandkumar, A., Alvarez, J. M., & Luo, P. (2021). SegFormer: Simple and efficient design for semantic segmentation with transformers. arXiv preprint arXiv:2105.15203. https://arxiv.org/abs/2105.15203

2. Google Earth Engine Data Catalog. (n.d.). Harmonized Sentinel-2 MSI: MultiSpectral Instrument, Level-2A (SR). European Union/ESA/Copernicus.
https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED

- Iakubovskii, P. (2019). Segmentation Models PyTorch. GitHub repository. https://github.com/qubvel/segmentation_models.pytorch

- Sahilcarterr. (2023, dezembro 26). Why nn.BCEWithLogitsLoss Numerically Stable. Medium. https://medium.com/@sahilcarterr/why-nn-bcewithlogitsloss-numerically-stable-6a04f3052967

1. Pistas de Pouso. (s.d.). Earth Engine App. Google Earth Engine. Recuperado em 27 de dezembro de 2025, de https://solvedgeo.users.earthengine.app/view/pistas-de-pouso.

- “Projeto MapBiomas - Mapa de Pistas de Pouso da Amazonia 2021 (v1)”
acessado em 29 de dezembro de 2025 através do link: https://brasil.mapbiomas.org/wp-content/uploads/sites/4/2023/08/MapBiomas_Pistas_de_Pouso_06.02.2023_1.pdf”

- PyTorch. (2025). torch. Documentação oficial do PyTorch. Recuperado em 29 dezembro de 2025, de
https://docs.pytorch.org/docs/stable/torch.html

- Google Earth Engine. (2025). Exporting images. Google Developers Guide. Disponível em:
https://developers.google.com/earth-engine/guides/exporting_images
​
- Instituto Nacional de Pesquisas Espaciais - INPE. (2019). Aplicação de Índices de Vegetação ara Identificação de Área
Construída e Vegetação Densa em Áreas Urbanas na Amazônia. Repositório Marte2. Disponível em: http://marte2.sid.inpe.br/col/sid.inpe.br/marte2/2019/10.31.12.02/doc/97992.pdf
