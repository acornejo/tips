# prolog-CSP

First install GNU prolog:

    apt-get install gprolog

To use CLP(FP) in gprolog:

    X+1#=#Y,Y#>3,Y#=<5, fd_labeling([X,Y]).

You can press ';' to see additional solutions.

A different example using explicit domain restrictions is:

    X*Y#=#X+Y, fd_domain([X,Y],1,100), fd_labeling([X,Y]).

Alternatively, you can try to use the Clip\_ extension to Prolog. The
syntax is:

    {X+1=Y, Y>3,Y=<5}, print_clip(X).

.. \_Clip: http://interval.sourceforge.net/interval/index.html

Using the instructions "integer(X)" or "boolean(Y)" its possible to
constraint the values of the variables to be integral or boolean
(\[0,1\]).

A good alternative to Prolog/Clip is RealPaver. A newer system is Ciao,
which offers CLP(R) and CLP(Q) to do constraint programming over the
reals and rationals respectively. Icos is similar to RealPaver but
larger and with a more complex syntax.
