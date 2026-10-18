```tikz
\begin{document}
\begin{tikzpicture}[x=2.8cm, y=1.2cm]

    % Define styling
    \tikzstyle{neuron}=[circle, thick, draw=white, fill=black, inner sep=0pt, minimum size=0.55cm]
    
    % Define custom line color (greyer white)
    \colorlet{lineColor}{white!45!black}

    % --- NODES / NEURONS ---
    
    % Input Layer (2 nodes)
    \node[neuron] (I-1) at (0, -1.5) {};
    \node[neuron] (I-2) at (0, -2.5) {};

    % Hidden Layer 1 (4 nodes)
    \node[neuron] (H1-1) at (1, -0.5) {};
    \node[neuron] (H1-2) at (1, -1.5) {};
    \node[neuron] (H1-3) at (1, -2.5) {};
    \node[neuron] (H1-4) at (1, -3.5) {};

    % Hidden Layer 2 (4 nodes)
    \node[neuron] (H2-1) at (2, -0.5) {};
    \node[neuron] (H2-2) at (2, -1.5) {};
    \node[neuron] (H2-3) at (2, -2.5) {};
    \node[neuron] (H2-4) at (2, -3.5) {};

    % Output Layer (2 nodes)
    \node[neuron] (O-1) at (3, -1.5) {};
    \node[neuron] (O-2) at (3, -2.5) {};

    % --- CONNECTIONS ---
    
    % Input -> Hidden 1
    \foreach \source in {1,2}
        \foreach \dest in {1,2,3,4}
            \draw[lineColor, semithick] (I-\source) -- (H1-\dest);

    % Hidden 1 -> Hidden 2
    \foreach \source in {1,2,3,4}
        \foreach \dest in {1,2,3,4}
            \draw[lineColor, semithick] (H1-\source) -- (H2-\dest);

    % Hidden 2 -> Output
    \foreach \source in {1,2,3,4}
        \foreach \dest in {1,2}
            \draw[lineColor, semithick] (H2-\source) -- (O-\dest);

    % --- LABELS (Explicitly forced white text) ---
    \node[above, text=black, align=center, font=\Large\sffamily] at (0, 0.2) {Input\\layer};
    \node[above, text=black, align=center, font=\Large\sffamily] at (1, 0.2) {Hidden\\layer 1};
    \node[above, text=black, align=center, font=\Large\sffamily] at (2, 0.2) {Hidden\\layer 2};
    \node[above, text=black, align=center, font=\Large\sffamily] at (3, 0.2) {Output\\layer};

\end{tikzpicture}
\end{document}
```
<div align="center">
Layer sizes: 2, 4, 4, 2
</div>

$$
\begin{array}{r@{\quad}r r} Weights: & & 3 2 \\ Biases : & & 1 0 \\ \hline Parameters: & & 4 2 \end{array}$$

<div align="center"> A weight corresponds to any of the individual lines connecting a neuron in one layer to a neuron in the next layer. A feedforward perceptron or Multilayer Perceptron (MLP) is a simple neural network where information moves in one direction with no loops or feedback cycles.
</div>

``` Python
# A single Neuron
inputs = [1.2, 5.1]
weights = [3.2, 3.1]
bias = 3

Output = inputs[0]*weights[0] + inputs[1]*weights[1] + bias
print(Output)
```

<div align ="center"> Or can be expressed as :</div>
$$z_{1,1}=x_{1,1}\cdot w_{1,1,1}+x_{1,2}\cdot w_{1,2,1}+b_{1,1}$$
<div align = "center"> The output is subsequently passed on to the next Neuron</div>
















