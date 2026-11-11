# tcc-utfpr
Projeto desenvolvido como TCC do curso de Engenharia de Software na Universidade Tecnológica Federal do Paraná.

-> [Aplicação de Aprendizado Profundo na Classificação de Lesões Cutâneas Usando o Conjunto de dados ISIC Challenge 2020: test]

Este trabalho faz uma avaliação experimental sobre o desempenho de um
classificador EfficientNet-B4, treinado por Transfer Learning e ajuste fino progressivo
somado às técnicas de Oversampling e Focal Loss, na identificação de lesões cutâneas
malignas em imagens dermatoscópicas do conjunto de dados ISIC Challenge 2020:
test. As imagens foram agrupadas em três classes (benigna, indeterminada e maligna)
e a avaliação foi feita de forma um-contra-todos tomando a classe Maligna como de
interesse, com intervalos de confianc¸a de 95% por bootstrap em nível de paciente.
No conjunto de teste (2269 imagens, 62 malignas), a regra de decisão por argmax
com Test-Time Augmentation obteve sensibilidade de 56,5% (35 de 62), precisão de
10,3%, especificidade de 86,2%, AUC-ROC de 0,79 e AUC-PR de 0.135 diante de uma
prevalência de 2,7%. Limiares escolhidos por validação cruzada em duas metades
do teste elevaram a sensibilidade a 72,6% (meta de 0,80), ao custo de precis˜ao de
6,1% e 688 falsos positivos. A análise também identificou limitações que restringem
a generalização: todos os pacientes do teste possuem imagens no treino e o próprio
teste foi usado para seleção de checkpoint. Os resultados indicam um compromisso
entre sensibilidade e precisão e não sustentam qualquer uso clínico.

-> Pré-requisitos

Antes de começar, certifique-se de ter os seguintes requisitos instalados na sua máquina:

Para rodar em ambiente local:
    Python 3 
    Jupyter Notebook ou JupyterLab

Para ambiente virtual do Google Colab:
    GPU NVIDIA Tesla T4 (15GB VRAM)
    Python 3

Git

-> Instalação e Configuração do Ambiente

Para garantir que o experimento rode sem problemas de conflito de versões, recomendamos o uso de um ambiente virtual.

Clone este repositório:

git clone https://github.com/seu-usuario/nome-do-repositorio.git
cd nome-do-repositorio

Instale as dependências necessárias contidas no arquivo \code\Codigo_treinamento_modelo.ipynb

-> Configuração dos Dados

 Faça o download do dataset no link [https://api.isic-archive.com/collections/68/] e em seguida monte o drive com a seguinte organização de pastas:
  
    ISIC/
    ├── train/
    ├── test/
    ├── results_eval/
    └── metadata.csv
 

-> Como Executar os Notebooks

Codigo_treinamento.ipynb: 

    1. Instalação de dependências
    2. Imports e acesso ao drive
    3. Processamento
    4. Redimensionamento de imagens e aplicação do CoarseDropout
    5. Aplicação das transformações e geração dos datasets finais no tensorflow
    6. Checkpoint de salvamento do modelo já treinado.
    7. Implementando a arquitetura EfficientNetB4 -> **Esse bloco deve ser rodado somente na primeira vez em que o modelo for executado.**
    10. Treino do topo da rede neural
    11. Fine Tunning fase 2
    12. Fine Tunning fase 3: Aumento de camadas disponíveis para treinamento.

    As etapas 8 e 9 somente devem ser executadas em caso de interrupção do treinamento.

02_treinamento_do_modelo.ipynb: [Ex: Carrega os dados processados, treina os algoritmos selecionados e salva os pesos do melhor modelo na pasta models/].

Avaliacao_TCC2_inferencia.ipynb: [
    Setup → Parte A (auditoria, só CPU) → Parte B (inferência, GPU) → Parte C (métricas) → Parte D (figuras) → Parte E (erros) → Parte F (registro da execução).].

-> Resultados e Conclusões

Os resultados gerados pela execução e avaliação deste projeto ficam salvos na pasta resultados/*.

-> Licença

Este projeto está sob a licença MIT - veja o arquivo LICENSE para mais detalhes.