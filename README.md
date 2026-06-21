# 3dof-robot-inverse-kinematics
Modelagem geométrica e simulação da cinemática inversa de um manipulador robótico planar de 3 graus de liberdade (RRR) em Python.

# Cinemática Inversa e Simulação de Manipulador Robótico Planar 3-DOF (RRR)

Este repositório contém a modelagem matemática e a implementação computacional da **Cinemática Inversa** de um manipulador robótico planar com 3 juntas rotativas (Configuração RRR). O projeto foi desenvolvido em Python utilizando a ferramenta Jupyter Notebook (Google Colab).

## 📌 Sobre o Projeto

O objetivo principal deste projeto é calcular os ângulos das juntas ($q_1$, $q_2$, $q_3$) necessários para posicionar o efetuador final do robô em uma coordenada cartesiana específica $(x, y)$ com uma determinada orientação ($\phi$) em relação ao plano horizontal.

### Características do Manipulador:
* **Configuração:** RRR (Três juntas rotacionais planas).
* **Elo 1 ($L_1$):** 1.00 m
* **Elo 2 ($L_2$):** 0.50 m
* **Elo 3 ($L_3$):** 0.25 m

## 🧠 Abordagem Matemática

A solução foi desenvolvida utilizando o método do **Desacoplamento Cinemático** associado à **Lei dos Cossenos**:
1. **Desacoplamento do Punho:** Isola-se a ponta do segundo elo $(x_1, y_1)$ subtraindo a projeção trigonométrica do elo final ($L_3$) orientado pelo ângulo desejado $\phi$.
2. **Lei dos Cossenos:** Reduz-se o problema para um manipulador de 2 elos (antropomórfico planar) para solucionar de forma geométrica direta o ângulo da junta do meio ($q_2$).
3. **Resolução de $q_1$ e $q_3$:** Utiliza-se a mudança de variáveis trigonométricas com a função de arco tangente de dois argumentos (`arctan2`) para identificar o quadrante exato, evitando divisões por zero e indeterminações.

## 🛠️ Tecnologias Utilizadas

* **Python 3**
* **NumPy:** Para manipulação de matrizes e funções trigonométricas de alta performance.
* **Matplotlib:** Para renderização geométrica e simulações estáticas e dinâmicas do braço mecânico.

## 🚀 Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone [https://github.com/Jose-Savyo/3dof-robot-inverse-kinematics.git](https://github.com/Jose-Savyo/3dof-robot-inverse-kinematics.git)

2. Instale as dependências necessárias:
   ```bash
    pip install numpy matplotlib

3. Abra o arquivo RRR.ipynb em seu ambiente Jupyter local ou faça o upload diretamente no Google Colab.

📈 Resultados obtidos

Abaixo, um exemplo da estrutura lógica utilizada para validar os cálculos:
Python

# Exemplo de chamada para o algoritmo de cinemática inversa
q1, q2, q3 = calc(x=0.8, y=0.5, pos=110)

O algoritmo conta com proteções matemáticas através de truncamentos (np.clip) que evitam erros numéricos de ponto flutuante próximos das fronteiras físicas de alcance, tornando a simulação altamente confiável.

