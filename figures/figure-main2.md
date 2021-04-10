```latex {cmd=lualatex,hide=true}
\documentclass[tikz]{standalone}
\usepackage{lmodern}
\usepackage{tikz-network}
\usetikzlibrary{shadows,chains,scopes,calc}
\usetikzlibrary{decorations.pathmorphing, shapes}

\usetikzlibrary{shapes}

\begin{document}
  \begin{tikzpicture}[scale=0.8, multilayer=3d]

    \begin{scope}[xshift=-6.5cm, yshift=9.0cm]
        \Vertex[x=0,y=0,IdAsLabel,layer=3]{T1}

        \Vertex[x= 0.0,y= 1.0,IdAsLabel,layer=2]{T1-9} 
        \Vertex[x=-1.0,y=-1.0,IdAsLabel,layer=2]{T1-4} 
        \Vertex[x= 1.0,y=-1.0,IdAsLabel,layer=2]{T1-3} 
        \Vertex[x=-1.0,y= 1.0,IdAsLabel,layer=2]{T1-2} 
        \Vertex[x= 1.0,y= 1.0,IdAsLabel,layer=2]{T1-1} 
        \Vertex[x=-1.0,y= 0.0,IdAsLabel,layer=2]{T1-6} 
        \Vertex[x= 1.0,y= 0.0,IdAsLabel,layer=2]{T1-5} 
        \Vertex[x= 0.0,y=-1.0,IdAsLabel,layer=2]{T1-7} 
        \Vertex[x=-0.0,y= 0.0,IdAsLabel,layer=2]{T1-8} 

        \Edge[bend=10](T1)(T1-1)
        \Edge[bend=10](T1)(T1-2)
        \Edge[bend=10](T1)(T1-3)
        \Edge[bend=10](T1)(T1-4)
        \Edge[bend=10](T1)(T1-5)
        \Edge[bend=10](T1)(T1-6)
        \Edge[bend=10](T1)(T1-7)
        \Edge[bend=10](T1)(T1-8)
        \Edge[bend=10](T1)(T1-9)

        \Plane[color=blue, x=-1,y=-1,width=2,height=2, grid=5mm, layer=3, style={thin, dashed}]
        \Plane[color=gray,opacity=.1, x=-2,y=-2,width=4,height=4, grid=5mm, layer=2, style={thin, dashed}]
    \end{scope}

    \begin{scope}[xshift=15cm, yshift=11cm]
        \Vertex[x=0,y=0,IdAsLabel,layer=3]{T3}

        \Vertex[x= 1.0,y= 1.0,layer=2]{T3-1}
        %\Vertex[x=-1.0,y= 1.0,layer=2]{T3-2}
        \Vertex[x= 1.0,y=-1.0,layer=2]{T3-3}
        \Vertex[x=-1.0,y=-1.0,layer=2]{T3-4}
        %\Vertex[x= 1.0,y= 0.0,layer=2]{T3-5}
        %\Vertex[x=-1.0,y= 0.0,layer=2]{T3-6}
        \Vertex[x= 0.0,y=-1.0,layer=2]{T3-7}
        %\Vertex[x=-0.0,y= 0.0,layer=2]{T3-8}
        \Vertex[x= 0.0,y= 1.0,layer=2]{T3-9}

        \Edge[bend=10](T3)(T3-1)
        %\Edge[bend=10](T3)(T3-2)
        \Edge[bend=10](T3)(T3-3)
        \Edge[bend=10](T3)(T3-4)
        %\Edge[bend=10](T3)(T3-5)
        %\Edge[bend=10](T3)(T3-6)
        \Edge[bend=10](T3)(T3-7)
        %\Edge[bend=10](T3)(T3-8)
        \Edge[bend=10](T3)(T3-9)

        \Plane[color=blue, x=-1,y=-1,width=2,height=2, grid=5mm, layer=3, style={thin, dashed}]
        \Plane[color=gray,opacity=.1, x=-2,y=-2,width=4,height=4, grid=5mm, layer=2, style={thin, dashed}]
    \end{scope}

    \begin{scope}[xshift=10cm, yshift=11.5cm]
        \Vertex[x=0,y=0,IdAsLabel,layer=3]{T4}

        \Vertex[x= 1.0,y= 1.0,layer=2]{T4-1}
        \Vertex[x=-1.0,y= 1.0,layer=2]{T4-2}
        %\Vertex[x= 1.0,y=-1.0,layer=2]{T4-3}
        \Vertex[x=-1.0,y=-1.0,layer=2]{T4-4}
        \Vertex[x= 1.0,y= 0.0,layer=2]{T4-5}
        \Vertex[x=-1.0,y= 0.0,layer=2]{T4-6}
        %\Vertex[x= 0.0,y=-1.0,layer=2]{T4-7}
        \Vertex[x=-0.0,y= 0.0,layer=2]{T4-8}
        %\Vertex[x= 0.0,y= 1.0,layer=2]{T4-9}

        \Edge[bend=10](T4)(T4-1)
        \Edge[bend=10](T4)(T4-2)
        %\Edge[bend=10](T4)(T4-3)
        \Edge[bend=10](T4)(T4-4)
        \Edge[bend=10](T4)(T4-5)
        \Edge[bend=10](T4)(T4-6)
        %\Edge[bend=10](T4)(T4-7)
        \Edge[bend=10](T4)(T4-8)
        %\Edge[bend=10](T4)(T4-9)

        \Plane[color=blue, x=-1,y=-1,width=2,height=2, grid=5mm, layer=3, style={thin, dashed}]
        \Plane[color=gray,opacity=.1, x=-2,y=-2,width=4,height=4, grid=5mm, layer=2, style={thin, dashed}]
    \end{scope}

    \begin{scope}[xshift=4.5cm, yshift=11.5cm]
        \Vertex[x=0,y=0,IdAsLabel,layer=3]{T2}

        %\Vertex[x= 1.0,y= 1.0,layer=2]{T2-1}
        \Vertex[x=-1.0,y= 1.0,layer=2]{T2-2}
        %\Vertex[x= 1.0,y=-1.0,layer=2]{T2-3}
        %\Vertex[x=-1.0,y=-1.0,layer=2]{T2-4}
        %\Vertex[x= 1.0,y= 0.0,layer=2]{T2-5}
        \Vertex[x=-1.0,y= 0.0,layer=2]{T2-6}
        %\Vertex[x= 0.0,y=-1.0,layer=2]{T2-7}
        %\Vertex[x=-0.0,y= 0.0,layer=2]{T2-8}
        \Vertex[x= 0.0,y= 1.0,layer=2]{T2-9}

        \Plane[color=blue, x=-1,y=-1,width=2,height=2, grid=5mm, layer=3, style={thin, dashed}]
        \Plane[color=gray,opacity=.1, x=-2,y=-2,width=4,height=4, grid=5mm, layer=2, style={thin, dashed}]
    \end{scope}

    \begin{scope}[xshift=-1.5cm, yshift=11.5cm]
        \Vertex[x=0,y=0,IdAsLabel,layer=3]{T5}

        %\Vertex[x= 1.0,y= 1.0,layer=2]{T5-1}
        \Vertex[x=-1.0,y= 1.0,layer=2]{T5-2}
        %\Vertex[x= 1.0,y=-1.0,layer=2]{T5-3}
        %\Vertex[x=-1.0,y=-1.0,layer=2]{T5-4}
        %\Vertex[x= 1.0,y= 0.0,layer=2]{T5-5}
        \Vertex[x=-1.0,y= 0.0,layer=2]{T5-6}
        %\Vertex[x= 0.0,y=-1.0,layer=2]{T5-7}
        \Vertex[x=-0.0,y= 0.0,layer=2]{T5-8}
        \Vertex[x= 0.0,y= 1.0,layer=2]{T5-9}

        \Plane[color=blue, x=-1,y=-1,width=2,height=2, grid=5mm, layer=3, style={thin, dashed}]
        \Plane[color=gray,opacity=.1, x=-2,y=-2,width=4,height=4, grid=5mm, layer=2, style={thin, dashed}]
    \end{scope}

    \begin{scope}[xshift=3.5cm, yshift=4.5cm]
        \Vertex[x=4,y=-8, layer=1, size=0.5,color=red!30!gray, label=DataFile, size=1]{File1}
        \Vertex[x=7,y=-4, layer=1, size=0.5, color=green!30!gray, label=DataFile, size=1]{File2}
    \end{scope}

    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T1)(T2)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T1)(T3)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T2)(T4)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T3)(T5)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T2)(T3)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T3)(T4)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T4)(T5)

    \Edge[color=red!30!black, bend=0, Direct,bend=10](File1)(T1-1)
    \Edge[color=red!30!black, bend=-0, Direct,bend=10](File1)(T2-9)
    \Edge[color=red!30!black, bend=0, Direct,bend=10](File1)(T3-3)
    \Edge[color=red!30!black, bend=0, Direct,bend=10](File1)(T4-4)
    \Edge[color=red!30!black, bend=-0, Direct,bend=10](File1)(T5-2)

    \Edge[color=green!20!black, bend=0, Direct,bend=-20](File2)(T1-2)
    \Edge[color=green!20!black, bend=0, Direct,bend=-20](File2)(T2-2)
    \Edge[color=green!20!black, bend=0, Direct,bend=-20](File2)(T3-4)
    \Edge[color=green!20!black, bend=0, Direct,bend=-20](File2)(T4-5)
    \Edge[color=green!20!black, bend=0, Direct,bend=-20](File2)(T5-6)

  \end{tikzpicture}
\end{document}
```