---
layout: post
title:  "Explain how znlog() work in PARI/GP"
categories: General
---

Fist, we can look up `znlog()` function in `src\basemath\arith1.c`
```c
// Functions compute  the discrete logarithm.
GEN znlog(GEN h, GEN g, GEN o)
{
    pari_sp av = avma;
    GEN N, fa, P, E, x;
    // switch between different input types.
    switch (typ(g))
    {
    case t_PADIC:
        /* some code here, useless */
    case t_INTMOD:
        // settting N and g
        N = gel(g, 1);
        g = gel(g, 2);
        break;
    default:
        //error
        pari_err_TYPE("znlog", g);
        return NULL; /* LCOV_EXCL_LINE */
    }
    if (equali1(N)) // trival
    {
        set_avma(av);
        return gen_0;
    }
    h = Rg_to_Fp(h, N); // h = h % N
    if (o)
        return gerepileupto(av, Fp_log(h, g, o, N));
    fa = Z_factor(N); // factors the N.
    P = gel(fa, 1);
    E = vec_to_vecsmall(gel(fa, 2));

    // znlog_rec()
    x = znlog_rec(h, g, N, P, E, get_PHI(P, E));
    
    /* some code here, useless */
    return gerepileuptoint(av, x);
}
```

Then, look up  `znlog_rec()`
```c
/* find x such that h = g^x mod N > 1, N = prod_{i <= l} P[i]^E[i], P[i] prime.
 * PHI[l] = eulerphi(N / P[l]^E[l]).   Destroys P/E */
static GEN
znlog_rec(GEN h, GEN g, GEN N, GEN P, GEN E, GEN PHI)
{
    long l = lg(P) - 1, e = E[l];
    GEN p = gel(P, l), phi = gel(PHI, l), pe = e == 1 ? p : powiu(p, e);
    GEN a, b, hp, gp, hpe, gpe, ogpe; /* = order(g mod p^e) | p^(e-1)(p-1) */

    /* some code here, useless */
    { /* Avoid black box groups: (Z/p^2)^* / (Z/p)^* ~ (Z/pZ, +), where DL
       is trivial */
        /* [order(gp), factor(order(gp))] */
        GEN v = Fp_factored_order(gp, subiu(p, 1), p);
        GEN ogp = gel(v, 1);
        /* some code here, useless */

        // Fp_log()
        a = Fp_log(hp, gp, v, p);

        /* some code here, useless */
    }
    /* gp^a = hp => x = a mod ogpe => generalized Pohlig-Hellman strategy */
    if (l == 1)
        return a;

    N = diviiexact(N, pe); /* make N coprime to p */
    h = Fp_mul(h, Fp_pow(g, modii(negi(a), phi), N), N);
    g = Fp_pow(g, modii(ogpe, phi), N);
    setlg(P, l); /* remove last element */
    setlg(E, l);
    b = znlog_rec(h, g, N, P, E, PHI);  // Recursion
    if (!b)
        return NULL;
    return addmulii(a, b, ogpe);
}

```

核心内容是 `Fp_log()`
```c

GEN Fp_log(GEN a, GEN g, GEN ord, GEN p)
{
    GEN v = get_arith_ZZM(ord);
    GEN F = gmael(v, 2, 1);
    long lF = lg(F) - 1, lmax;
    if (lF == 0)
        return equali1(a) ? gen_0 : cgetg(1, t_VEC);
    lmax = expi(gel(F, lF));
    if (BPSW_psp(p) && Fp_log_use_index(lmax, expi(p)))
        v = mkvec2(gel(v, 1), ZM_famat_limit(gel(v, 2), int2n(27)));
    return gen_PH_log(a, g, v, (void *)p, &Fp_star);
}

```

```c
GEN gen_PH_log(GEN a, GEN g, GEN ord, void *E, const struct bb_group *grp)
{
    pari_sp av = avma;
    GEN v, ginv, fa, ex;
    long i, j, l;
    /* some code here, useless */
    if (grp->easylog)
    {
        GEN e = grp->easylog(E, a, g, ord);
        if (e)
            return e;
    }
    /* some code here, useless */
}

```

```c
/* Trivial cases a = 1, -1. Return x s.t. g^x = a or [] if no such x exist */
static GEN Fp_easylog(void *E, GEN a, GEN g, GEN ord)
{
    /* some code here, useless */
    if (typ(ord) == t_INT && BPSW_psp(p) && Fp_log_use_index(expi(ord), expi(p)))
        return Fp_log_index(a, g, ord, p);
    return gc_NULL(av); /* not easy */
}
```

```c

static GEN
Fp_log_index(GEN a, GEN b, GEN m, GEN p)
{
    pari_sp av = avma, av2;
    long i, j, nbi, nbr = 0, nbrow, nbg;
    GEN C, c, Ci, ci, pi, pr, sz, l, Ao, Bo, K, d, p_1;
    pari_timer ti;
    struct Fp_log_rel r;
    ulong bnds = itou(roundr_safe(opt_param(sqrti(p), DEFAULTPREC)));
    ulong bnd = 4 * bnds;
    p_1 = subiu(p, 1);
    /* some code here, useless */
    pr = primes_upto_zv(bnd);
    /* some code here, useless */
    nbg = Fp_log_sieve(&r, C, c, Ci, ci, pi, sz);
    nbrow = r.prmax + nbg;
    setlg(r.rel, r.nbrel + 1);
    r.rel = gerepilecopy(av2, r.rel);
    K = check_kernel(nbi + nbrow - r.prmax, nbrow, r.prmax, C, r.rel, p, m);
    Ao = Fp_log_find_ind(a, K, r.prmax, C, p, m);
    Bo = Fp_log_find_ind(b, K, r.prmax, C, p, m);
    d = gcdii(Ao, Bo);
    l = Fp_div(diviiexact(Ao, d), diviiexact(Bo, d), m);
    if (!equalii(a, Fp_pow(b, l, p)))
        pari_err_BUG("Fp_log_index");
    return gerepileuptoint(av, l);
}
```

```c

GEN Fp_log_sieve_worker(long a, long prmax, GEN C, GEN c, GEN Ci, GEN ci, GEN pi, GEN sz)
{
    pari_sp ltop = avma;
    long th, n = lg(pi) - 1;
    long i, j;
    GEN sieve = zero_zv(a + 2) + 1;
    GEN L = cgetg(1 + a + 2, t_VEC);
    pari_sp av = avma;
    long rel = 1;
    GEN z, h;
    h = addis(C, a);
    if ((z = Z_issmooth_fact(h, prmax)))
    {
        gel(L, rel++) = mkvec2(z, mkvecsmall3(1, a, -1));
        av = avma;
    }
    for (i = 1; i <= n; i++)
    {
        ulong li = pi[i], s = sz[i], al = a % li;
        ulong u, iv = Fl_invsafe(Fl_add(Ci[i], al, li), li);
        if (!iv)
            continue;
        u = Fl_mul(Fl_sub(ci[i], Fl_mul(Ci[i], al, li), li), iv, li);
        for (j = u; j <= a; j += li)
            sieve[j] += s;
    }
    if (a)
    {
        long e = expi(mulis(C, a));
        th = e - expu(e) - 1;
    }
    else
        th = -1;
    for (j = 0; j < a; j++)
        if (sieve[j] >= th)
        {
            GEN h = addiu(subii(muliu(C, a + j), c), a * j);
            if ((z = Z_issmooth_fact(h, prmax)))
            {
                gel(L, rel++) = mkvec2(z, mkvecsmall3(2, a, j));
                av = avma;
            }
            else
                set_avma(av);
        }
    /* j = a */
    if (sieve[a] >= th)
    {
        GEN h = addiu(subii(muliu(C, 2 * a), c), a * a);
        if ((z = Z_issmooth_fact(h, prmax)))
            gel(L, rel++) = mkvec2(z, mkvecsmall3(1, a, -2));
    }
    setlg(L, rel);
    return gerepilecopy(ltop, L);
}

static long
Fp_log_sieve(struct Fp_log_rel *r, GEN C, GEN c, GEN Ci, GEN ci, GEN pi, GEN sz)
{
    struct pari_mt pt;
    long i, j, nb = 0;
    GEN worker = snm_closure(is_entry("_Fp_log_sieve_worker"),
                             mkvecn(7, utoi(r->prmax), C, c, Ci, ci, pi, sz));
    long running, pending = 0;
    GEN W = zerovec(r->nbgen);
    mt_queue_start_lim(&pt, worker, r->nbgen);
    for (i = 0; (running = (i < r->nbgen)) || pending; i++)
    {
        GEN done;
        long idx;
        mt_queue_submit(&pt, i, running ? mkvec(stoi(i)) : NULL);
        done = mt_queue_get(&pt, &idx, &pending);
        if (!done || lg(done) == 1)
            continue;
        gel(W, idx + 1) = done;
        nb += lg(done) - 1;
        if (DEBUGLEVEL && (i & 127) == 0)
            err_printf("%ld%% ", 100 * nb / r->nbmax);
    }
    mt_queue_end(&pt);
    for (j = 1; j <= r->nbgen && r->nbrel < r->nbmax; j++)
    {
        long ll, m;
        GEN L = gel(W, j);
        if (isintzero(L))
            continue;
        ll = lg(L);
        for (m = 1; m < ll && r->nbrel < r->nbmax; m++)
        {
            GEN Lm = gel(L, m), h = gel(Lm, 1), v = gel(Lm, 2);
            if (v[1] == 1)
                addifsmooth1(r, h, v[2], v[3]);
            else
                addifsmooth2(r, h, v[2], v[3]);
        }
    }
    return j;
}
```
