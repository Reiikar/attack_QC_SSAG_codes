# attack_QC_SSAG_codes

Author : Mathieu Lhotel 

Contact : mathieu.lhotel@univ-fcomte.fr or m.lhotel@laposte.net

---

Description

---

Consider a covering X ---> Y of curves and a quasi-cyclic SSAG code used as public-key in a McEliece cryptosystem. With the knwoledge of the invariant code, this Magma programm shows that we can retrieve the secret strucutre of the public code.

This attack is described in Chapter 3 of the author's thesis.

---

How to use

---

Open Magma and type

`load "security_reduction_Kummer.mgm";` or `load "security_reduction_Kummer_bis.mgm";` 

The cover of curve is fixed in the code, i.e. Y is a degree ell=3 Kummer cover of X. You can instantiate an attack by chosing two integers r>0 and s>0, then run

`AttackKummer(r,s);`

---

What the function does

---

1. This function creates a QC-SSAG code defined on Y, with a support of length n=ell\*r and divisor G=ell\*s\*Q_inf, invariant under a random order ell automorphism in the galois group of Y ---> K.
2. While sampling the secret support, the y-evaluation vector is set aside (supposed unknown).
3. From the knowledge of the invariant support and divisor, several linear systems are constructed, then one attempt to solve them.
4. When we find a unique solution, the fonction outputs:
  - another vector, supposed to be equal to the y-evaluation vector;
  - the initial (unknown) y-evaluation vector, so that you can check we find the good one;
5. Else, it outputs an error.

---

Note

---

The rest of the attack consists in a (multivariate) interpolation step to rebuild a plane model of the curve Y, using the set of rational points we know on it (the public support). This has not been implemented yet.
