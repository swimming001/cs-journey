5. 假如说所作的一切都是为了定义dimension:any two bases of a finite-dimensional vector space has the same lenth,这说明了向量空间的基长度是固定的，由此可以定义维度dim(V),那上面为什么成立呢
    (1) base : linear independent+spans
        (0) linear combination:A linear combination of a list 𝑣1,…,𝑣𝑚 of vectors in 𝑉 is a vector of the form 𝑎1𝑣1 + ⋯+𝑎𝑚𝑣𝑚, where 𝑎1,…,𝑎𝑚 ∈ 𝐅.
        (1) linear indepentent: 𝑎1𝑣1 + ⋯+𝑎𝑚𝑣𝑚 = 0当且仅当系数为0
            就是这个向量之间的关系，不是互相组成的；
        (2) span:linear combination of some vectors
        (3) linear dependence lemma:不线性独立，就可以删成线性独立；->linear indepent< spans list ->够了
    (2) finite-dimensional:A vector space is called finite-dimensional if some list of vectors in it spans the space.
        我的理解：就是这个空间能被有限长度的的向量列表中的向量线性组合，找到一个就行
                 例如我能用((0,1)(1,0),(1,1))可以组成F^2;
    总结:vector space->subspace->spans->basis


4. direct sum of subspace
    1. Suppose 𝑉1,…,𝑉𝑚 are subspaces of 𝑉. Then 𝑉1 + ⋯ +𝑉𝑚 is a direct sum if and only if the only way to write  0 as a sum 𝑣1 +⋯+𝑣𝑚, where each 𝑣𝑘 ∈ 𝑉𝑘, is by taking each 𝑣𝑘 equal to 0.
    2. Suppose 𝑈 and 𝑊 are subspaces of 𝑉. Then 𝑈+𝑊 is a direct sum ⟺ 𝑈∩𝑊 ={0}.

3. Prove that the union of three subspaces of 𝑉 is a subspace of 𝑉 if and only if one of the subspaces contains the other two.
    0. a+b是U3，同理a-b是U3，然后相加，得到2a属于U3，这个要求2要在F中，如果有，说明2a是U3,如果1/2也有U3，那a,b都是U3的，这样就没问题了；所以面对只有0，1的F是不成立的，轻松证明啊(・∀・(・∀・(・∀・*)))
    1. 一个空间F=（{0,1}，mod2+，*）是域 那它的幂次F^2={(0,0),(1,0),(0,1),(1,1)}是vector space吗?
        这个问题很简单，只需要运算符和基础元素满足这个性质就行；
        首先mod2+:封闭性,结合律，单位元0，逆元（本身），交换律；
            *：封闭，分配；确实仍然满足
            //突然发现，mod2+是异或；

2. 证明子空间只能是过原点的线+R^2在R^2,这个很难；
    即A是subspace in R3，so，A is a line or a plane or R3，containing zero points
    3. 为什么引入sums of subspaces？
        我理解是为了构建更高维的向量空间，类似于集合的子集的概念，在某个系统中仍然成立，
    4. 什么是union of subspaces？
        这个很简单∩，∩能是子空间，只能一个是另一个的子集，但三元的情况复杂；

1. The set of continuous real-valued functions on the interval [0,1] is a subspace of 𝐑[0,1].
    Q1：为什么连续函数+连续函数还是连续函数
        由定义来：f(x),g(x)连续；
        则对于
        $\forall \epsilon>0,\exists \delta>0, when |x-x0|>0\rightarrow|f(x)-f(x0)|<\epsilon$;
        $\forall \epsilon>0,\exists \delta>0, when |x-x0|>0\rightarrow|g(x)-g(x0)|<\epsilon$;
        那么分别取$\delta=\epsilon$/2,两者相加，分别相减，用绝对值不等式，<$\epsilon$;
    Q2：连续的定义，极限的定义
        极限:$\forall \epsilon>0,\exists \delta>0, when |x-x0|>0\rightarrow|f(x)-A|<\epsilon$;
            简写$\lim_{x\to x0}f(x)=A$;
        连续:$\forall \epsilon>0,\exists \delta>0, when |x-x0|>0\rightarrow|f(x)-f(x0)|<\epsilon$;
            简写$\lim_{x\to x0}f(x)=f(x0)$;
        也就是连续在极限的基础上新增了f(x0)的定义；
    
        

0. subspace=additive identity+addition closure+scalar multiplication closure
