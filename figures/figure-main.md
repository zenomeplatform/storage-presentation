```latex {cmd=true,hide=true}
\documentclass[tikz]{standalone}
\usepackage{lmodern}
\usepackage{tikz-network}
\usetikzlibrary{shadows,chains,scopes,calc}
\usetikzlibrary{decorations.pathmorphing, shapes}

\usetikzlibrary{shapes}

\begin{document}
  \begin{tikzpicture}[scale=1, multilayer=3d]

    \begin{scope}[xshift=0cm, yshift=0cm]
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

    \begin{scope}[xshift=14cm, yshift=4cm]
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

    \begin{scope}[xshift=7.5cm, yshift=0.1cm]
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

    \begin{scope}[xshift=0.1cm, yshift=9.1cm]
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

    \begin{scope}[xshift=-3.0cm, yshift=4.5cm]
        \Vertex[x=0,y=0,IdAsLabel,layer=3]{T6}
        \Plane[color=blue, x=-1,y=-1,width=2,height=2, grid=5mm, layer=3, style={thin, dashed}]
        \Plane[color=gray,opacity=.1, x=-2,y=-2,width=4,height=4, grid=5mm, layer=2, style={thin, dashed}]

        \Vertex[x=0.25,y=2.5,color=red!30!gray, layer=1.75, size=0]{File1}
        \Vertex[x=1.75,y=0.5,color=green!30!gray, layer=1.75, size=0]{File2}

        \Vertex[x=0.25,y=-0.5, layer=2, size=0.5,color=red!30!gray]{CFile1}
        \Vertex[x=1.25,y=-1, layer=2, size=0.5, color=green!30!gray]{CFile2}

        \Edge[color=red!30!gray,bend=30](CFile1)(File1)
        \Edge[color=green!30!gray,bend=30](CFile2)(File2)
    \end{scope}

    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T1)(T2)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T1)(T3)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T2)(T4)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T3)(T5)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T4)(T6)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=20](T6)(T1)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T2)(T3)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T3)(T4)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T4)(T5)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T5)(T6)
    \Edge[lw=0.12cm, opacity=0.1, color=blue!50!black, bend=40](T6)(T1)

    \Edge[color=red!30!black, bend=0, Direct,bend=30](File1)(T1-1)
    \Edge[color=red!30!black, bend=-0, Direct,bend=20](File1)(T2-9)
    \Edge[color=red!30!black, bend=0, Direct,bend=10](File1)(T3-3)
    \Edge[color=red!30!black, bend=0, Direct,bend=-30](File1)(T4-4)
    \Edge[color=red!30!black, bend=-0, Direct,bend=-50](File1)(T5-2)

    \Edge[color=green!20!black, bend=0, Direct,bend=30](File2)(T1-2)
    \Edge[color=green!20!black, bend=0, Direct,bend=20](File2)(T2-2)
    \Edge[color=green!20!black, bend=0, Direct,bend=10](File2)(T3-4)
    \Edge[color=green!20!black, bend=0, Direct,bend=-30](File2)(T4-5)
    \Edge[color=green!20!black, bend=0, Direct,bend=-50](File2)(T5-6)

  \end{tikzpicture}
\end{document}
```