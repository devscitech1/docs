


observer
========

observer design



Calling Sequence
~~~~~~~~~~~~~~~~


::

    Obs=observer(Sys,J)
    [Obs,U,m]=observer(Sys [,flag,alfa])




Arguments
~~~~~~~~~

:Sys `syslin` list (linear system)
: :J nx x ny constant matrix (output injection matrix)
: :flag character strings ( `'pp'` or `'st'` (default))
: :alfa location of closed-loop poles (optional parameter, default=-1)
: :Obs linear system ( `syslin` list), the observer
: :U orthogonal matrix (see `dt_ility`)
: :m integer (dimension of unstable unobservable ( `st`) or
  unobservable ( `pp`) subspace)
:



Description
~~~~~~~~~~~

`Obs=observer(Sys,J)` returns the observer
`Obs=syslin(td,A+J*C,[B+J*D,-J],eye(A))` obtained from `Sys` by a `J`
output injection. (td is the time domain of `Sys`). More generally,
`observer` returns in `Obs` an observer for the observable part of
linear system `Sys`: `dotx=A x + Bu, y=Cx + Du` represented by a
`syslin` list. `Sys` has `nx` state variables, `nu` inputs and `ny`
outputs. `Obs` is a linear system with matrices `[Ao,Bo,Identity]`,
where `Ao` is `no x no`, `Bo` is `no x (nu+ny)`, `Co` is `no x no` and
`no=nx-m`.

Input to `Obs` is `[u,y]` and output of `Obs` is:

xhat=estimate of x modulo unobservable subsp. (case `flag='pp'`) or

xhat=estimate of x modulo unstable unobservable subsp. (case
`flag='st'`)

case `flag='st'`: z=H*x can be estimated with stable observer iff
`H*U(:,1:m)=0` and assignable poles of the observer are set to
`alfa(1),alfa(2),...`

case `flag='pp'`: z=H*x can be estimated with given error spectrum iff
`H*U(:,1:m)=0` all poles of the observer are assigned and set to
`alfa(1),alfa(2),...`

If H satifies the constraint: `H*U(:,1:m)=0` (ker(H) contains unobs-
subsp. of Sys) one has H*U=[0,H2] and the observer for z=H*x is H2*Obs
with H2=H*U(:,m+1:nx) i.e. Co, the C-matrix of the observer for H*x,
is Co=H2.

In the particular case where the pair `(A,C)` of `Sys` is observable,
one has `m=0` and the linear system `U*Obs` (resp. `H*U*Obs`) is an
observer for `x` (resp. `Hx`). The error spectrum is
`alpha(1),alpha(2),...,alpha(nx)`.



Examples
~~~~~~~~


::

    nx=5;nu=1;ny=1;un=3;us=2;Sys=`ssrand`_(ny,nu,nx,`list`_('dt',us,us,un));
    //nx=5 states, nu=1 input, ny=1 output, 
    //un=3 unobservable states, us=2 of them unstable.
    [Obs,U,m]=observer(Sys);  //Stable observer (default)
    W=U';H=W(m+1:nx,:);[A,B,C,D]=`abcd`_(Sys);  //H*U=[0,eye(no,no)];
    Sys2=`ss2tf`_(`syslin`_('c',A,B,H))  //Transfer u-->z
    Idu=`eye`_(nu,nu);Sys3=`ss2tf`_(H*U(:,m+1:$)*Obs*[Idu;Sys])  
    //Transfer u-->[u;y=Sys*u]-->Obs-->xhat-->HUxhat=zhat  i.e. u-->output of Obs
    //this transfer must equal Sys2, the u-->z transfer  (H2=eye).
    
    //Assume a Kalman model
    //dotx = A x + B u + G w
    // y   = C x + D u + H w + v
    //with Eww' = QN, Evv' = RN, Ewv' = NN
    //To build a Kalman observer:
    //1-Form BigR = [G*QN*G'         G*QN*H'+G*NN;
    //               H*QN*G'+NN*G'   H*QN*H'+RN];
    //the covariance matrix of the noise vector [Gw;Hw+v]
    //2-Build the plant P21 : dotx = A x + B1 e ; y = C2 x + D21 e 
    //with e a unit white noise.
    // [W,Wt]=fullrf(BigR);
    //B1=W(1:size(G,1),:);D21=W(($+1-size(C,1)):$,:);
    //C2=C;
    //P21=syslin('c',A,B1,C2,D21);
    //3-Compute the Kalman gain
    //L = lqe(P21);
    //4- Build an observer for the plant [A,B,C,D];
    //Plant = syslin('c',A,B,C,D);
    //Obs = observer(Plant,L);
    //Test example:
    A=-`diag`_(1:4);
    B=`ones`_(4,1);
    C=B'; D= 0; G=2*B; H=-3; QN=2;
    RN=5; NN=0;
    BigR = [G*QN*G'         G*QN*H'+G*NN;
            H*QN*G'+NN*G'   H*QN*H'+RN];
    [W,Wt]=`fullrf`_(BigR);
    B1=W(1:`size`_(G,1),:);D21=W(($+1-`size`_(C,1)):$,:);
    C2=C;
    P21=`syslin`_('c',A,B1,C2,D21);
    L = `lqe`_(P21);
    Plant = `syslin`_('c',A,B,C,D);
    Obs = observer(Plant,L);
    `spec`_(Obs.A)




See Also
~~~~~~~~


+ `dt_ility`_ detectability test
+ `unobs`_ unobservable subspace
+ `stabil`_ stabilization


.. _dt_ility: dt_ility.html
.. _stabil: stabil.html
.. _unobs: unobs.html


