# 🎨 Decágono Estocástico via Monte Carlo

## 📌 Sobre o Projeto

Este projeto foi desenvolvido para a disciplina de **Introdução à Computação Gráfica** (C#) e tem como objetivo renderizar a silhueta de um **decágono regular (10 lados)** em uma matriz de pixels de **800 x 800**.

Diferente da abordagem tradicional (desenhando linhas entre vértices), aqui utilizamos um método **estocástico baseado em Monte Carlo**, onde pontos são gerados aleatoriamente e testados matematicamente para verificar se pertencem à área interna do polígono.

---

## 🧠 Conceitos Utilizados

* Geometria Analítica
* Coordenadas Polares
* Simetria Angular
* Método de Monte Carlo
* Renderização com primitiva de ponto

---

## ⚙️ Como Funciona

Para cada ponto gerado aleatoriamente, o algoritmo segue os seguintes passos:

### 1. 🔄 Translação para o Centro

O ponto é deslocado para um sistema de coordenadas com origem no centro da tela.

> Isso facilita os cálculos radiais e angulares.

---

### 2. 📐 Conversão para Coordenadas Polares

O ponto cartesiano (x, y) é convertido para:

* **Raio (distância até o centro)**
* **Ângulo (θ)**

> Em polígonos regulares, o limite depende do ângulo — por isso essa conversão é essencial.

---

### 3. 🔁 Normalização Angular

O ângulo θ é reduzido para uma única seção do polígono:

```
seccao = 2π / n
α = (θ mod seccao) - (seccao / 2)
```

> Isso aproveita a simetria do decágono, simplificando os cálculos.

---

### 4. 📏 Cálculo do Raio Máximo

O limite do polígono varia conforme o ângulo:

* O raio é menor no meio dos lados
* O raio é maior nos vértices

> Esse cálculo define se o ponto está dentro da forma.

---

### 5. ✅ Teste de Inclusão

Se:

```
d ≤ d_max
```

👉 O ponto é desenhado na tela.

Caso contrário, é descartado.

---

## 🖥️ Interface

* Janela deve iniciar **maximizada**
* Um botão executa a renderização
* Um **ComboBox** permite escolher cores:

  * Síntese Aditiva (RGB)
  * Síntese Subtrativa (CMY)

---

## 🧩 Estrutura do Código

### 🔹 Função de Módulo Ajustado

```csharp
public float Modulo(float a, float b)
{
    return (a % b + b) % b;
}
```

---

### 🔹 Função Principal (Decágono)

Responsável por:

* Gerar pontos aleatórios
* Aplicar os cálculos matemáticos
* Renderizar os pontos válidos

```csharp
public void decagono(PaintEventArgs e, int r, int g, int b)
{
    int n = 10;
    int R = 150;
    int tentativas = 80000;

    int largura = 800;
    int altura = 800;

    int centroX = largura / 2;
    int centroY = altura / 2;

    Random rnd = new Random();

    for (int i = 0; i < tentativas; i++)
    {
        int px = rnd.Next(centroX - R, centroX + R);
        int py = rnd.Next(centroY - R, centroY + R);

        // Implementação do teste de inclusão aqui
    }
}
```

---

## 🚀 Como Executar

1. Clone o repositório:

```
git clone <seu-repo>
```

2. Abra o projeto no Visual Studio

3. Execute a aplicação

4. Escolha a cor desejada

5. Clique no botão para renderizar o decágono

---

## 📊 Parâmetros Importantes

| Parâmetro  | Valor   | Descrição                    |
| ---------- | ------- | ---------------------------- |
| n          | 10      | Número de lados              |
| R          | 150     | Raio externo                 |
| tentativas | 80000   | Quantidade de pontos gerados |
| resolução  | 800x800 | Tamanho da tela              |

---

## 💡 Observações

* Quanto maior o número de tentativas, mais "preenchido" o decágono ficará
* O método não desenha linhas — apenas pontos
* A precisão depende da quantidade de amostras

---

## 👩‍💻 Autoria

Projeto desenvolvido para fins acadêmicos na disciplina de Computação Gráfica.

---

## ⭐ Ideia Principal

> "Transformar matemática em imagem usando aleatoriedade controlada."

---
