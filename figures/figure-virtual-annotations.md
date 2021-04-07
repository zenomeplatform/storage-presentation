```latex {cmd=true,hide=true}
\documentclass[tikz]{standalone}
\usepackage{lmodern}
\usetikzlibrary{shadows,chains,scopes,calc}
\usetikzlibrary{decorations.pathmorphing, shapes}

\begin{document}
\begin{tikzpicture}
    [
        start chain=going right,
        node distance=10mm,
        database/.style={
            thick,
            draw=black,
            top color=white,
            bottom color=black!10,
            font=\sffamily\small,
            minimum width=20mm,
            minimum height=15mm,
            drop shadow
        },
        userfile/.style={
            thick,
            draw=black,
            top color=green!20,
            bottom color=green!10,
            font=\sffamily,
            minimum width=10mm,
            minimum height=10mm
        },
        virtfile/.style={
            thick,
            draw=blue,
            top color=gray!10,
            bottom color=gray!10,
            font=\sffamily,
            minimum width=10mm,
            minimum height=10mm
        },
        deltadb/.style={
            thick,
            draw=black,
            top color=black!20,
            bottom color=black!10,
            font=\sffamily,
            minimum width=2mm,
            minimum height=15mm
        },
        every label/.style={
            font=\sffamily
        },
    ]
    \node[userfile, label={above:User's VCF}] at (-3,-6) (Variants) {};


    \node[on chain, database, label={above:ClinVar 2019-12}] (CV1) {};
    \node[on chain, database, label={above:ClinVar 2020-01}] (CV2) {};
    \node[on chain, database, label={above:ClinVar 2020-02}] (CV3) {};
    \node[on chain, database, label={above:ClinVar 2020-03}] (CV4) {};
    \node[on chain, database, label={above:ClinVar 2020-04}] (CV5) {};

    \node[deltadb, label={below:Delta}] at ($0.5*(CV1) + 0.5*(CV2) + (0,-2.5)$) (DCV1) {};
    \draw[thick,black] ($(CV1.south) + (+0.2, -0.1)$)
                    |- ($(DCV1.north)+ (+0, 0.5)$)
                    -| ($(CV2.south) + (-0.2, -0.1)$)
                       ($(DCV1.north)+ (+0, 0.5)$) -- (DCV1.north) ;


    \node[deltadb, label={below:Delta}] at ($0.5*(CV2) + 0.5*(CV3) + (0,-2.5)$) (DCV2) {};
    \draw[thick,black] ($(CV2.south) + (+0.2, -0.1)$)
                    |- ($(DCV2.north)+ (+0, 0.5)$)
                    -| ($(CV3.south) + (-0.2, -0.1)$)
                       ($(DCV2.north)+ (+0, 0.5)$) -- (DCV2.north) ;


    \node[deltadb, label={below:Delta}] at ($0.5*(CV3) + 0.5*(CV4) + (0,-2.5)$) (DCV3) {};
    \draw[thick,black] ($(CV3.south) + (+0.2, -0.1)$)
                    |- ($(DCV3.north)+ (+0, 0.5)$)
                    -| ($(CV4.south) + (-0.2, -0.1)$)
                       ($(DCV3.north)+ (+0, 0.5)$) -- (DCV3.north) ;


    \node[deltadb, label={below:Delta}] at ($0.5*(CV4) + 0.5*(CV5) + (0,-2.5)$) (DCV4) {};
    \draw[thick,black] ($(CV4.south) + (+0.2, -0.1)$)
                    |- ($(DCV4.north)+ (+0, 0.5)$)
                    -| ($(CV5.south) + (-0.2, -0.1)$)
                       ($(DCV4.north)+ (+0, 0.5)$) -- (DCV4.north) ;


    \node[virtfile, label={above:Annotated with}, label={below:ClinVar 2019-12}] at ($(CV1) + (0, -6)$) (UCV1) {};
    \node[virtfile, label={above:Annotated with}, label={below:ClinVar 2020-01}] at ($(CV2) + (0, -6)$) (UCV2) {};
    \node[virtfile, label={above:Annotated with}, label={below:ClinVar 2020-02}] at ($(CV3) + (0, -6)$) (UCV3) {};
    \node[virtfile, label={above:Annotated with}, label={below:ClinVar 2020-03}] at ($(CV4) + (0, -6)$) (UCV4) {};
    \node[virtfile, label={above:Annotated with}, label={below:ClinVar 2020-04}] at ($(CV5) + (0, -6)$) (UCV5) {};

    \draw[black,->] (CV1) + (-5,0) -> (CV1);
    \draw[black,->] (CV1) -> (CV2);
    \draw[black,->] (CV2) -> (CV3);
    \draw[black,->] (CV3) -> (CV4);
    \draw[black,->] (CV4) -> (CV5);
    \draw[black,->] (CV5) -> +(5,0);

    \draw[blue,->] (Variants) -> (UCV1);
    \draw[blue,->] (UCV1) -> (UCV2);
    \draw[blue,->] (UCV2) -> (UCV3);
    \draw[blue,->] (UCV3) -> (UCV4);
    \draw[blue,->] (UCV4) -> (UCV5);

    \draw[black, very thick,->, ] (CV1) -> ($(UCV1) + (0,1)$) node[midway,fill=white] {Annotate};
    \draw[black!60, very thick,->, ] (DCV1) +(0,-1.25) |- +(1,-3.4) node[midway,below=0.15,fill=white] {Update};
    \draw[black!60, very thick,->, ] (DCV2) +(0,-1.25) |- +(1,-3.4) node[midway,below=0.15,fill=white] {};
    \draw[black!60, very thick,->, ] (DCV3) +(0,-1.25) |- +(1,-3.4) node[midway,below=0.15,fill=white] {};
    \draw[black!60, very thick,->, ] (DCV4) +(0,-1.25) |- +(1,-3.4) node[midway,below=0.15,fill=white] {};


\end{tikzpicture}
\end{document}
```