---
tags:
  - unicap
  - graduação
  - 6-periodo
---

**Professor:** Robson Lins
**Período:** Ago 2025 - Dez 2025
**Nota final:** TBA

**Projeto 1** - Curva de Bezier (Barbie)
- OpenGL
	- vcpkg
	- freeglut
- [Repositório Git](https://github.com/Dudubraga/Computacao-Grafica)

---
### **Relatório: Aplicação de Transformações Geométricas 3D em OpenGL**

**Aluno:** Eduardo Costa Braga - 00000848640

#### **1. Introdução**

Este relatório descreve a implementação de um programa em C++ utilizando as bibliotecas OpenGL e GLUT para renderizar um objeto 3D e aplicar sobre ele transformações geométricas de rotação, escala e translação. O objetivo é demonstrar visualmente o efeito dessas transformações em tempo real, através de comandos interativos do teclado.
O programa inicializa uma cena 3D com eixos cartesianos (X, Y, Z) para servirem como referência visual, facilitando a observação das alterações aplicadas ao objeto.
#### **2. Configuração do Ambiente e Visualização**

A cena é configurada com uma projeção em perspectiva (`gluPerspective`), o que cria a sensação de profundidade. A câmera (observador) é posicionada pela função `gluLookAt` nas coordenadas `(80, 80, 80)`, apontando para a origem `(0, 0, 0)`, com o vetor "up" alinhado ao eixo Y. A função `displayFcn` é responsável por desenhar a cena. Ela primeiro desenha os eixos (`drawAxes`) e, em seguida, renderiza o toro na cor rosa.
#### **3. Implementação das Transformações Geométricas**
As transformações são tratadas na função `keyboard`, que captura as teclas pressionadas pelo usuário. Em OpenGL, essas transformações são cumulativas e modificam a matriz _ModelView_ atual.
##### **3.1. Rotação (`glRotatef`)**
A rotação altera a orientação do objeto ao redor de um eixo específico.
- **Tecla 'x'**: `glRotatef(90.0, 1.0, 0.0, 0.0)`
    - Aplica uma rotação de 90 graus _em torno do eixo X_.
- **Tecla 'y'**: `glRotatef(90.0, 0.0, 1.0, 0.0)`
    - Aplica uma rotação de 90 graus _em torno do eixo Y_.
- **Tecla 'z'**: `glRotatef(90.0, 0.0, 0.0, 1.0)`
    - Aplica uma rotação de 90 graus _em torno do eixo Z_.
##### **3.2. Escala (`glScalef`)**
A escala altera o tamanho do objeto, multiplicando suas coordenadas pelos fatores fornecidos em X, Y e Z.
- **Tecla '+'**: `glScalef(1.5, 1.5, 1.5)`
    - Aplica uma escala uniforme, aumentando o tamanho do objeto em 50% (fator 1.5) em todas as direções.
- **Tecla '-'**: `glScalef(0.5, 0.5, 0.5)`
    - Aplica uma escala uniforme, reduzindo o tamanho do objeto pela metade (fator 0.5) em todas as direções.
- **Tecla ';'**: `glScalef(1.0, 2.0, 0.5)`
    - Aplica uma escala não-uniforme (deformação), mantendo o tamanho em X, duplicando-o em Y e reduzindo-o pela metade em Z.
##### **3.3. Translação (`glTranslatef`)**
A translação move (desloca) o objeto ao longo dos eixos, somando valores às suas coordenadas.
- **Tecla 't'**: `glTranslatef(30.0, 0.0, 0.0)`
    - Move o objeto 30 unidades na direção _positiva do eixo X_.
- **Tecla 'u'**: `glTranslatef(0.0, 30.0, 0.0)`
    - Move o objeto 30 unidades na direção _positiva do eixo Y_.
- **Tecla 'c'**: `glTranslatef(0.0, 0.0, 30.0)`
    - Move o objeto 30 unidades na direção _positiva do eixo Z_.
#### **4. Controle de Visualização**
Após cada transformação aplicada na função `keyboard`, o comando `glutPostRedisplay()` é invocado. Isso sinaliza ao GLUT que a janela precisa ser redesenhada, garantindo que a função `displayFcn` seja chamada novamente para renderizar o objeto com sua nova matriz de transformação. Além disso, a tecla **'r'** foi implementada para resetar a visualização. Ela chama a função `reshapeFcn`, que recarrega as matrizes de projeção e _ModelView_ para seus estados originais, efetivamente desfazendo todas as transformações acumuladas.
#### **5. Conclusão**
O programa cumpre os requisitos ao demonstrar com sucesso a aplicação de transformações 3D. Através da manipulação interativa da matriz _ModelView_ com as funções `glRotatef`, `glScalef` e `glTranslatef`, foi possível observar os efeitos de alteração de orientação, tamanho e posição do toro no espaço tridimensional.
