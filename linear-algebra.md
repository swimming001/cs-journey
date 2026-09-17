



5. linear combination and span;
    span 是线性组合的集合:span(v1​,v2​,…,vk​)={a1​v1​+a2​v2​+⋯+ak​vk​∣ai​∈R}
    我的理解：只要一个（V，+，*）是域field，那么在F上高阶都是vector space，这就是向量空间的定义；
        从而引申出子空间，span就是子空间 
    通过新的，来认识旧的，所以subspace就是由向量的线性组合和这些向量的span；
    0. finite dimention vector space:有限维，可以找一个正数m，表示span的向量个数
    1. linearly idependent:是描述向量关系的；lemma:向量线性组合=0，当且仅当coefficient=0；
        虽然定义了很多
        （1）总结一下，这节其实承接了上节subspace，只不过更具体了一点，把里面的向量来线性组合，然后定义出了linearly idependent，然后我们就可以用span+几个向量表示subspace，vector space等等，
        （2）然后一个重要的推论，span的子集的长度小于等于span，定义长度吧，也就是list的个数 number

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
