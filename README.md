# 🎯 Simulador de Projétil com Arrasto em JavaScript

Simulação interativa de um **canhão disparando projéteis** usando **p5.js**, levando em conta **gravidade** e **resistência do ar (arrasto aerodinâmico)**. Funciona diretamente no **Google Colab** ou qualquer notebook que suporte JavaScript.

---

## 🚀 Funcionalidades

- **Controle de disparo:** Ajuste o ângulo (10° a 80°) e a velocidade inicial (5 a 50 m/s) com sliders.  
- **Canhão estilizado:** Cano e base desenhados com formas geométricas.  
- **Prévia da trajetória:** Trajetória pontilhada projetada antes do disparo, considerando arrasto realista.  
- **Arrasto aerodinâmico:** Simula desaceleração do projétil pelo ar usando \(F_d = \frac12 \rho C_d A v^2\).  
- **Alvo de dardo:** Alvo colorido no final do canvas com anéis concêntricos.  
- **Detecção de acerto:** Mensagem de "Parabéns!" aparece por 1 segundo ao atingir o alvo.  
- **Reset automático:** Após o acerto ou queda da bola, você pode disparar novamente.

---

## 🛠 Tecnologias

- **JavaScript**  
- **p5.js** para gráficos, animação e interatividade  
- HTML e CSS para HUD, sliders e botão de disparo  
- **Google Colab** ou Jupyter Notebook para rodar diretamente

---

## ⚙ Física implementada

- **Gravidade:** \(g = 9.8 \, m/s²\), aplicada no eixo Y.  
- **Arrasto aerodinâmico:**  
\[
F_d = \frac12 \rho C_d A v^2
\]  
Onde:  
  - \(\rho = 1.225 \, kg/m³\) → densidade do ar  
  - \(C_d = 0.47\) → coeficiente de arrasto (esfera)  
  - \(A = \pi r^2\) → área frontal da bola  
  - \(v = \sqrt{v_x^2 + v_y^2}\) → velocidade instantânea  

A aceleração do arrasto é aplicada em direção oposta à velocidade do projétil:

\[
a_x = -\frac{F_d}{m} \frac{v_x}{v}, \quad
a_y = -\frac{F_d}{m} \frac{v_y}{v} + g
\]

- **Integração temporal:**  
```text
vx += ax * dt
vy += ay * dt
x  += vx * dt * scale
y  += vy * dt * scale
