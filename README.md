# 🚀 YOLOv3 Player Detector

Sistema de detecção de objetos em tempo real utilizando **YOLOv3 Tiny**, **OpenCV DNN** e **Windows GDI**, desenvolvido em **C++** para demonstração de técnicas de Visão Computacional e Processamento de Imagens.

---

## 📖 Sobre o Projeto

O **YOLOv3 Player Detector** é um projeto desenvolvido para explorar técnicas modernas de **Computer Vision**, realizando captura de tela em tempo real e processamento dos frames utilizando uma rede neural baseada no modelo **YOLOv3 Tiny**.

O sistema realiza a captura de uma região da tela, executa a inferência do modelo de detecção de objetos e desenha caixas delimitadoras (Bounding Boxes) ao redor dos objetos detectados, exibindo também o nível de confiança de cada detecção.

Este projeto possui fins **educacionais**, demonstrando a utilização do módulo **OpenCV DNN**, aceleração por GPU e otimizações para processamento em tempo real.

---

# ✨ Principais Funcionalidades

- Captura de tela em tempo real utilizando Windows GDI
- Conversão automática para OpenCV (`cv::Mat`)
- Inferência utilizando YOLOv3 Tiny
- Renderização de Bounding Boxes
- Exibição da confiança da detecção
- Contador de FPS em tempo real
- Seleção automática do melhor backend disponível
- Suporte para aceleração via CUDA
- Suporte para OpenCL
- Fallback automático para CPU
- Código organizado em módulos independentes

---

# 🏗 Arquitetura do Projeto

```
Desktop
   │
   ▼
Captura de Tela (Windows GDI)
   │
   ▼
Conversão para OpenCV
(cv::Mat)
   │
   ▼
Pré-processamento
(blobFromImage)
   │
   ▼
YOLOv3 Tiny
(OpenCV DNN)
   │
   ▼
Inferência
   │
   ▼
Filtro de Confiança
   │
   ▼
Non-Maximum Suppression
(NMS)
   │
   ▼
Bounding Boxes
   │
   ▼
Renderização Final
```

---

# ⚙ Como o Sistema Funciona

## 1. Captura de Tela

O sistema utiliza a API **Windows GDI** para capturar continuamente uma região configurável da tela.

Durante essa etapa são utilizadas funções como:

- BitBlt()
- GetDIBits()

Após a captura, os pixels são convertidos diretamente para um objeto **cv::Mat** do OpenCV.

---

## 2. Pré-processamento

Cada frame capturado é normalizado utilizando:

```cpp
blobFromImage()
```

Configuração utilizada:

- Escala: **1 / 255**
- Resolução de entrada: **320 × 320 pixels**

---

## 3. Inferência

O modelo utilizado é o:

- YOLOv3 Tiny

Arquivos necessários:

```
yolov3-tiny.cfg
yolov3-tiny.weights
coco-dataset.labels
```

A inferência é executada utilizando o módulo **OpenCV DNN**.

---

## 4. Pós-processamento

Após a inferência são realizados:

- cálculo da confiança
- filtragem das detições
- geração das Bounding Boxes
- Non-Maximum Suppression (NMS)

Por fim, o sistema desenha as caixas delimitadoras e exibe a confiança de cada objeto detectado.

---

# 🚀 Seleção Automática de Backend

O sistema escolhe automaticamente o backend de maior desempenho disponível.

Ordem de prioridade:

```
CUDA
 ↓
OpenCL
 ↓
CPU
```

Caso o computador possua GPU compatível, o processamento é acelerado automaticamente.

---

# 📂 Estrutura do Projeto

```
example_win32_directx11
│
├── detector
│   ├── detector.cpp
│   ├── detector.h
│   ├── object_detector.cpp
│   ├── object_detector.h
│   ├── screen_capture.cpp
│   ├── screen_capture.h
│   └── defines.h
│
├── imgui
│
├── auth
│
├── example_win32_directx11.vcxproj
│
└── ...
```

---

# 🛠 Tecnologias Utilizadas

- C++17
- OpenCV
- OpenCV DNN
- YOLOv3 Tiny
- Windows API
- Windows GDI
- CUDA
- OpenCL
- Visual Studio

---

# 📈 Fluxo de Processamento

```
Captura da Tela
        │
        ▼
Conversão para cv::Mat
        │
        ▼
Pré-processamento
        │
        ▼
YOLOv3 Tiny
        │
        ▼
Inferência
        │
        ▼
Filtro de Confiança
        │
        ▼
NMS
        │
        ▼
Bounding Boxes
        │
        ▼
Renderização
```

---

# 💻 Requisitos

- Windows 10 ou superior
- Visual Studio 2019 / 2022
- OpenCV
- C++
- CUDA (Opcional)
- OpenCL (Opcional)

---

# 📊 Desempenho

O desempenho depende do hardware utilizado.

Backend | Desempenho
-------- | ----------
CUDA | Excelente
OpenCL | Muito Bom
CPU | Compatível

---

# 🔮 Melhorias Futuras

- Suporte para modelos YOLO mais recentes
- Exportação para ONNX Runtime
- Benchmark automático
- Multi-thread para captura
- Pipeline totalmente assíncrono
- Suporte a TensorRT
- Configuração dinâmica dos parâmetros de inferência

---

# 📄 Licença

Este projeto é disponibilizado sob a licença **MIT**.

---

# 👨‍💻 Autor

**Lucas Nolon**

Desenvolvedor focado em:

- Visão Computacional
- Inteligência Artificial
- C++
- OpenCV
- Redes Neurais
- Segurança da Informação

---

## ⭐ Se este projeto foi útil para você

Considere deixar uma **⭐ Star** no repositório para apoiar o desenvolvimento.
